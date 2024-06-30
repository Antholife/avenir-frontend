<script>
import axios from 'axios'
import sal from 'sal.js'
export default {
    mounted() {
        sal();
        const connectForm = document.getElementById("connectForm");
        const checkbox = document.getElementById("checkbox");
        if (localStorage.getItem("check") === "true") {
            console.log("check")
            document.getElementById("mail").setAttribute("value", localStorage.getItem("mail"));
            document.getElementById("pwd").setAttribute("value", localStorage.getItem("pwd"));
            checkbox.setAttribute("checked", "true")
        }
        connectForm.addEventListener("submit", async (e) => {
            e.preventDefault();
            let mail = document.getElementById("mail");
            let pwd = document.getElementById("pwd");

            if (mail.value === "" || pwd.value === "") {
                alert("Veillez à saisir une valeur dans les deux champs !");
                return;
            }
            await axios.post("http://localhost:1337/api/auth/local", {
                identifier: mail.value,
                password: pwd.value,
            })
                .then(response => {
                    localStorage.setItem('token', response.data.jwt);
                    localStorage.setItem('user', JSON.stringify(response.data.user));
                    if (checkbox.checked) {
                        localStorage.setItem('check', "true");
                        localStorage.setItem('mail', mail.value);
                        localStorage.setItem('pwd', pwd.value);
                    } else {
                        localStorage.setItem('check', "false");
                        localStorage.removeItem('mail');
                        localStorage.removeItem('pwd');
                    }
                    alert("Vous êtes connecté ! Redirection vers la page d'accueil");
                    this.$router.push('/');
                })
                .catch(error => {
                    alert("Combinaison email/mot de passe incorrecte !");
                    alert("Si ce n'est pas le cas, merci de confirmer votre adresse mail dans votre boite de réception");
                    console.log('An error occurred:', error.response);
                });
        });
        connectForm.reset();
    },
    methods: {
        pwdF() {
            let mail = document.getElementById("mail");
            if (mail.value === "") {
                alert("Veillez à saisir une valeur dans le champ email pour réinitialiser votre mot de passe !");
                return;
            }
            axios
                .post('http://localhost:1337/api/auth/forgot-password', {
                    email: mail.value, // user's email
                })
                .then(response => {
                    alert('Un email de réinitialisation a été envoyé à l\'adresse ' + mail.value + ' !');
                })
                .catch(error => {
                    console.log('An error occurred:', error.response);
                });
        }
    }
}
</script>

<template>
    <section class="page">
        <div class="leftContainer">
            <h3 data-sal="fade"
                data-sal-delay="100"
                data-sal-duration="1000"
                data-sal-easing="ease" style="color: black">Avenir Immobilier</h3>
            <div class="connect" data-sal="slide-right"
                 data-sal-delay="1000"
                 data-sal-duration="1000"
                 data-sal-easing="ease">
                <h2 class="title">Se connecter</h2>
                <p>Si tu n’es pas encore inscrit,</p>
                <p>Tu peux
                    <NuxtLink :to="'/register'" class="colorLink">t’inscrire ici !</NuxtLink>
                </p>
                <form id="connectForm">
                    <img class="prefix0" src="@/assets/connect/envInput.svg" :width=17 :height=12 alt="env"/>
                    <input style="margin-bottom: 100px" class="input" type="email" id="mail"
                           placeholder="Entre ton adresse e-mail"/>
                    <label class="top">Email</label>
                    <img class="prefix1" src="@/assets/connect/lockInput.svg" :width=17 :height=17 alt="lock"/>
                    <input style="margin-bottom: 17px" type="password" class="input" id="pwd" minlength="6"
                           placeholder="Entre ton mot de passe"/>
                    <label class="top2">Mot de passe</label>
                    <img class="prefix2" src="@/assets/connect/eyesPassword.svg" :width=14 :height=12 alt="eyesPass"/>
                    <div class="pwd">
                        <div class="wrapper">
                            <input class="checkbox" type="checkbox" id="checkbox"/>
                            <label class="checkLabel">Se souvenir de moi</label>
                        </div>
                        <p class="fgPwd" v-on:click="pwdF" >Mot de passe oublié ?</p>
                    </div>
                    <button class="button" type="submit">Se connecter</button>
                </form>
                <p class="continue">ou continue avec</p>
                <img class="social" src="@/assets/connect/social.png" alt="social" :width=165 :height=43>
            </div>
        </div>
        <div class="rightContainer" data-sal="slide-left"
             data-sal-delay="600"
             data-sal-duration="1000"
             data-sal-easing="ease">
            <p class="header"><img style="margin-right: 8px" src="@/assets/connect/phone-call.svg" alt="phone-call"/>+94
                0116 789 754</p>
            <div style="display: flex; justify-content: center; margin-top: 79px">
                <img src="@/assets/connect/influenceur.png" alt="influenceur" :width=312 :height=456 />
            </div>
            <div style="margin-left: 98px; margin-top: 87px">
                <p class="titleRight">Rejoins la communauté</p>
                <p class="subTitle">Et sois mis en relation en 15 secondes.</p>
            </div>
        </div>
    </section>
</template>

<style scoped>
.social {
    cursor: pointer;
    text-align: center;
    margin: 25px auto 0 auto;
}

.continue {
    font-family: 'Poppins', sans-serif;
    font-weight: 500;
    font-size: 16px;
    line-height: 24px;
    color: #B5B5B5;
    text-align: center;
    margin-top: 58px;
}

.titleRight {
    font-family: 'Poppin', sans-serif;
    font-weight: 600;
    font-size: 40px;
    line-height: 60px;
    color: #FFFFFF;
}

.subTitle {
    font-family: 'Poppins', sans-serif;
    font-weight: 300;
    font-size: 20px;
    line-height: 30px;
    color: #FFFFFF;
}

.header {
    text-align: right !important;
    color: #FFFFFF;
    font-size: 15px;
    font-weight: 400;
    padding-right: 26px;
}

.rightContainer {
    display: flex;
    flex-direction: column;
    width: 735px;
    height: 724px;
    background-color: black;
    border-radius: 8px;
    padding: 24px 0 96px 0;
}

.button {
    display: flex;
    font-family: 'IntegralCF-Regular', sans-serif;
    font-size: 12px;
    align-items: center;
    justify-content: center;
    margin-top: 48px;
    background: #B188EA;
    border-radius: 8px;
    border: none;
    color: white;
    text-decoration: none;
    width: 200px;
    height: 46px;
    cursor: pointer;
}

.fgPwd {
    cursor: pointer;
    font-family: 'Poppins', sans-serif;
    font-size: 12px;
    color: #4D4D4D;
    font-weight: 300;
}

.checkbox {
    width: 15px;
    height: 15px;
}

.wrapper {
    display: flex;
    align-items: center;
}

.checkLabel {
    font-weight: 300;
    font-size: 12px;
    color: #000000;
    margin-left: 25px;
}

.pwd {
    display: flex;
    justify-content: space-between;
    margin-bottom: 48px;
}

.prefix0 {
    position: absolute;
    top: 7px;
}

.prefix1 {
    position: absolute;
    top: 136px;
    left: 0;
}

.prefix2 {
    position: absolute;
    top: 142px;
    right: 0;
    cursor: pointer;
}

.input {
    color: #000842;
    width: 429px;
    font-size: 16px;
    font-weight: 400;
    font-family: 'Poppins', sans-serif;
    border: none;
    padding-left: 30px;
    padding-bottom: 7px;
    border-bottom: #000842 2px solid;
}

.input::placeholder {
    color: #000842;
    font-size: 16px;
    font-weight: 400;
    font-family: 'Poppins', sans-serif;
}

.top {
    top: -30px;
    left: 0;
}

.top2 {
    top: 104px;
    left: 0;
}

form {
    position: relative;
    margin-top: 70px;
}

label {
    position: absolute;
    font-size: 13px;
    font-weight: 500;
    color: #999999;
    font-family: 'Poppins', sans-serif;
}

.connect {
    display: flex;
    flex-direction: column;
    margin: 75px 0 28px 124px;
    width: min-content;
}

.leftContainer {
    width: 735px;
    height: 839px;
    background-color: white;
    margin-right: 130px
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

.colorLink {
    color: #B188EA;
    cursor: pointer;
    text-decoration: none;
}

p {
    font-size: 16px;
    font-weight: 400;
    text-align: left;
    margin: 0;
}
@media screen and (max-width: 1280px) {
    .leftContainer {
        width: unset;
        margin: 0 0 60px 0;
    }
    .page {
        flex-direction: column;
        align-items: center;
    }
    .rightContainer {
        width: 1110px;
        align-items: center;
    }
    .connect {
        margin: unset;
    }
}
</style>
