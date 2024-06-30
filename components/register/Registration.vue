<script>
import axios from 'axios'
import sal from "sal.js";

export default {
    methods: {
        postData(mail, pwd) {
            axios.post("http://localhost:1337/api/auth/local/register", {
                    username: mail,
                    email: mail,
                    password: pwd,
                })
                .then(() => {
                    this.$router.push('/connect');
                })
                .catch(error => {
                    // Handle error.
                    console.log('An error occurred:', error.response);
                });
        },
    },
    mounted() {
        sal();
        let registerForm = document.getElementById("registerForm");
        registerForm.addEventListener("submit", async (e) => {
            e.preventDefault();
            let mail = document.getElementById("mail");
            let pwd = document.getElementById("pwd");
            let pwdConfirm = document.getElementById("pwdConfirm");

            if (mail.value === "" || pwd.value === "" || pwdConfirm.value === "") {
                alert("Veuillez à saisir une valeur dans les trois champs !");
                return;
            }
            if (pwd.value !== pwdConfirm.value) {
                alert("Les mots de passe ne correspondent pas !");
                return;
            }
            try {
                await this.postData(mail.value, pwd.value);
            } catch (error) {
                this.error = error;
            }
        });
        registerForm.reset();
    }
}
</script>

<template>
    <section class="page">
        <div class="leftContainer">
            <h3 data-sal="fade"
                data-sal-delay="100"
                data-sal-duration="1000"
                data-sal-easing="ease"
                style="color: black">Avenir Immobilier</h3>
            <div data-sal="slide-right"
                 data-sal-delay="1000"
                 data-sal-duration="1000"
                 data-sal-easing="ease" class="connect">
                <h2 class="title">S'inscrire</h2>
                <p>Tu es déjà inscrit ?</p>
                <p>Tu peux
                    <NuxtLink :to="'/connect'" class="colorLink">te connecter ici !</NuxtLink>
                </p>
                <form id="registerForm">
                    <img class="prefix0" src="@/assets/connect/envInput.svg" :width=17 :height=12 alt="env"/>
                    <input style="margin-bottom: 100px" id="mail" class="input" type="email"
                           placeholder="Entre ton adresse e-mail"/>
                    <label class="top">Email</label>
                    <img class="prefix1" src="@/assets/connect/lockInput.svg" :width=17 :height=17 alt="lock"/>
                    <input style="margin-bottom: 100px" type="password" id="pwd" class="input"
                           placeholder="Entre ton mot de passe" minlength="6"/>
                    <label class="top2">Mot de passe</label>
                    <img class="prefix2" src="@/assets/connect/eyesPassword.svg" :width=14 :height=12 alt="eyesPass"/>
                    <img class="prefix3" src="@/assets/connect/lockInput.svg" :width=17 :height=17 alt="lock"/>
                    <input style="margin-bottom: 17px" type="password" id="pwdConfirm" class="input"
                           placeholder="Confirme ton mot de passe" minlength="6"/>
                    <label class="top3">Confirmation de mot de passe</label>
                    <img class="prefix4" src="@/assets/connect/eyesPassword.svg" :width=14 :height=12 alt="eyesPass"/>
                    <button class="button" type="submit">S'inscrire</button>
                </form>
            </div>
        </div>
        <div class="rightContainer"
             data-sal="slide-left"
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

.prefix3 {
    position: absolute;
    top: 270px;
    left: 0;
}

.prefix4 {
    position: absolute;
    top: 276px;
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

.top3 {
    top: 238px;
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
