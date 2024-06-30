<script>
import 'mapbox-gl/dist/mapbox-gl.css'
import mapboxgl from 'mapbox-gl'
import axios from 'axios'
import sal from "sal.js";

export default {
    data() {
        return {
            locations: [],
            map: null,
            error: null,
            open: false,
            location: null,
            urlToIllu: null,
            features: [],
        }
    },
    methods: {
        modal(location) {
            if ((this.location && this.location.id) === location.id) {
                this.open = false
                this.setMarkerClicked(this.location.id, false)
                this.location = null
            } else {
                this.open = true
                if (this.location){
                    this.setMarkerClicked(this.location.id, false)
                }
                this.location = location
                this.urlToIllu = `http://localhost:1337${this.location.properties.illu}`
                this.setMarkerClicked(location.id, true)
            }
        },
        setMarkerClicked(id, isClicked) {
            this.map.setFeatureState({
                source: 'geojson',
                id: id,
            }, {
                clicked: isClicked
            });
        }
    },
    async mounted() {
        sal();
        mapboxgl.accessToken = 'pk.eyJ1IjoiYW50aG9saWZlIiwiYSI6ImNsZTc0aG0wZDAxejAzcWtibWw0MnkyemMifQ.Vs9QSCI2-3LJ0-r2puRszA';
        this.map = new mapboxgl.Map({
            container: 'map', // container ID
            style: 'mapbox://styles/mapbox/light-v11', // style URL
            center: [6.129384, 45.899247], // starting position [lng, lat]
            zoom: 12, // starting zoom
        });
        try {
            const response = await axios.get('http://localhost:1337/api/locations?populate=illu')
            this.locations = response.data.data
        } catch (error) {
            this.error = error;
        }

        let idFeature = 1
        this.locations.forEach(location => {
            const data = {
                type: 'Feature',
                id: idFeature,
                properties: {
                    name: location.attributes.name,
                    latitude: location.attributes.latitude,
                    longitude: location.attributes.longitude,
                    type: location.attributes.type,
                    illu: location.attributes.illu.data.attributes.url,
                    description: location.attributes.description,
                },
                geometry: {
                    type: 'Point',
                    coordinates: [location.attributes.longitude, location.attributes.latitude]
                }
            }
            idFeature++
            this.features.push(data)
        })

        const geojson = {
            type: 'FeatureCollection',
            features: this.features
        };

        this.map.on('load', () => {
            this.map.addSource('geojson', {
                type: 'geojson',
                data: geojson,
                cluster: true,
                clusterMaxZoom: 14,
                clusterRadius: 50
            });

            this.map.addLayer({
                id: 'clusters',
                type: 'circle',
                source: 'geojson',
                filter: ['has', 'point_count'],
                paint: {
                    'circle-color': "#dbae5f",
                    'circle-radius': [
                        'step',
                        ['get', 'point_count'],
                        20,
                        100,
                        30,
                        750,
                        40
                    ]
                }
            });

            this.map.addLayer({
                id: 'cluster-count',
                type: 'symbol',
                source: 'geojson',
                filter: ['has', 'point_count'],
                layout: {
                    'text-field': ['get', 'point_count_abbreviated'],
                    'text-font': ['DIN Offc Pro Medium', 'Arial Unicode MS Bold'],
                    'text-size': 12
                }
            });

            this.map.addLayer({
                id: 'unclustered-point',
                type: 'circle',
                source: 'geojson',
                filter: ['!', ['has', 'point_count']],
                paint: {
                    "circle-color": [
                        'case',
                        ['boolean', ['feature-state', 'clicked'], false],
                        "#33007A",
                        "#dbae5f"
                    ],
                    'circle-radius': 12,
                }
            });

            this.map.on('click', 'clusters', (e) => {
                const features = this.map.queryRenderedFeatures(e.point, {
                    layers: ['clusters']
                });
                const clusterId = features[0].properties.cluster_id;
                this.map.getSource('geojson').getClusterExpansionZoom(
                    clusterId,
                    (err, zoom) => {
                        if (err) return;

                        this.map.easeTo({
                            center: features[0].geometry.coordinates,
                            zoom: zoom
                        });
                    }
                );
            });
            this.map.on('click', 'unclustered-point', (e) => {
                this.modal(e.features[0])
            });
            this.map.on('mouseenter', ['clusters', 'unclustered-point'], () => {
                this.map.getCanvas().style.cursor = 'pointer';
            });
            this.map.on('mouseleave', ['clusters', 'unclustered-point'], () => {
                this.map.getCanvas().style.cursor = '';
            });
        });
    }
}
</script>

<template>
    <section class="page">
        <div class="container">
            <h3 data-sal="fade"
                data-sal-delay="100"
                data-sal-duration="1000"
                data-sal-easing="ease"
                style="color: black">Avenir Immobilier</h3>
            <div data-sal="fade"
                 data-sal-delay="400"
                 data-sal-duration="1000"
                 data-sal-easing="ease"
                 class="header">
                <h2 class="title">Bienvenu</h2>
                <p>Trouve la location qu'il te faut ici !</p>
            </div>
            <div class="content" data-sal="fade"
                 data-sal-delay="600"
                 data-sal-duration="1000"
                 data-sal-easing="ease">
                <div id='map'></div>
                <div class="popup" v-if="open">
                    <img class="illu" :src=urlToIllu alt="illustration">
                    <div class="contentText">
                        <h3 class="titlePopup">{{ this.location.properties.name }},
                            {{ this.location.properties.type }}</h3>
                        <p>{{ this.location.properties.description }}</p>
                    </div>
                    <NuxtLink :to="'/map'" class="button">Contacter</NuxtLink>
                </div>
            </div>
            <NuxtLink data-sal="fade"
                      data-sal-delay="800"
                      data-sal-duration="1000"
                      data-sal-easing="ease" :to="'/map'" class="button" style="margin-top: 33px">Rechercher ici</NuxtLink>
        </div>
    </section>
</template>

<style scoped>

#map {
    width: inherit;
    height: inherit;
    border-radius: 29px;
}

.content {
    width: 1025px;
    height: 530px;
    position: relative;
    display: flex;
    align-items: center;
}

.popup {
    width: 385px;
    border-radius: 29px;
    padding: 17px 17px;
    z-index: 1;
    left: 942px;
    position: absolute;
    background-color: white;
    height: 409px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
    display: flex;
    flex-direction: column;
    align-items: center;
}

.contentText {
    text-align: left;
}

.header {
    display: flex;
    flex-direction: column;
    margin: 33px 0;
}

.container {
    width: 735px;
    height: 839px;
    background-color: white;
}

.page {
    display: flex;
    justify-content: space-between;
    padding: 21px 26px 29px;
    background-color: #FFFFFF;
}

.title {
    font-size: 30px;
    font-weight: 400;
    color: black;
}

.titlePopup {
    font-family: 'Poppins', sans-serif;
    font-size: 18px;
    font-weight: 800;
    color: black;
}

.button {
    font-family: 'IntegralCF-Regular', sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #dbae5f;
    border-radius: 8px;
    color: white;
    text-decoration: none;
    width: 210px;
    min-height: 46px;
    margin: 21px 0;
}

.illu {
    border-radius: 18px;
    width: 380px;
    min-height: 200px;
}

p {
    font-size: 16px;
    font-weight: 400;
    text-align: left;
    line-height: 21px;
    margin: 0;
}
@media screen and (max-width: 1060px){
    .content {
        width: 100%;
    }
}
</style>
