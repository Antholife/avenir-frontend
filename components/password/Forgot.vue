<script>
import axios from 'axios'
import sal from "sal.js";

export default {
    methods: {
        postData(pwd) {
            const queryString = window.location.search;
            const urlParams = new URLSearchParams(queryString);
            const token = urlParams.get('code');
            axios
                .post('http://localhost:1337/api/auth/reset-password', {
                    code: token, // code contained in the reset link of step 3.
                    password: pwd,
                    passwordConfirmation: pwd,
                })
                .then(response => {
                    alert("Votre mot de passe à été modifié avec succès ! Redirection...");
                    this.$router.push('/connect');
                })
                .catch(error => {
                    console.log('An error occurred:', error.response);
                });
        },
    },
    mounted() {
        sal();
        let registerForm = document.getElementById("registerForm");
        registerForm.addEventListener("submit", async (e) => {
            e.preventDefault();
            let pwd = document.getElementById("pwd");
            let pwdConfirm = document.getElementById("pwdConfirm");

            if (pwd.value === "" || pwdConfirm.value === "") {
                alert("Veillez à saisir une valeur dans les deux champs !");
                return;
            }
            if (pwd.value !== pwdConfirm.value) {
                alert("Les mots de passe ne correspondent pas !");
                return;
            }
            try {
                await this.postData(pwd.value);
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
                <h2 class="title">Modification de mot de passe</h2>
                <p>Ici tu peu modifier ton mot de passe !</p>
                <form id="registerForm">
                    <img class="prefix1" src="@/assets/connect/lockInput.svg" :width=17 :height=17 alt="lock"/>
                    <input style="margin-bottom: 100px" type="password" id="pwd" class="input"
                           placeholder="Entre ton nouveau mot de passe" minlength="6"/>
                    <label class="top2">Mot de passe</label>
                    <img class="prefix2" src="@/assets/connect/eyesPassword.svg" :width=14 :height=12 alt="eyesPass"/>
                    <img class="prefix3" src="@/assets/connect/lockInput.svg" :width=17 :height=17 alt="lock"/>
                    <input style="margin-bottom: 17px" type="password" id="pwdConfirm" class="input"
                           placeholder="Confirme ton mot de passe" minlength="6"/>
                    <label class="top3">Confirmation de mot de passe</label>
                    <img class="prefix4" src="@/assets/connect/eyesPassword.svg" :width=14 :height=12 alt="eyesPass"/>
                    <button class="button" type="submit">Valider</button>
                </form>
            </div>
        </div>
    </section>
</template>

<style scoped>

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
    top: 2px;
    left: 0;
}

.prefix4 {
    position: absolute;
    top: 8px;
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

.top2 {
    top: -32px;
    left: 0;
}

.top3 {
    top: 100px;
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
    flex-direction: column;
    align-items: center;
    padding: 21px 26px 29px;
    background-color: #FFFFFF;
}

.title {
    font-size: 30px;
    font-weight: 400;
    color: black;
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
    .connect {
        margin: unset;
    }
}
</style>
