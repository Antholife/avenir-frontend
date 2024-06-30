<template>
  <NuxtLayout>
   <NuxtPage />
  </NuxtLayout>
</template>

<style>
@import '/node_modules/sal.js/dist/sal.css';
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
@font-face {
  font-family: 'IntegralCF-Regular';
  src: url('assets/fonts/IntegralCF-Regular.otf')  format('truetype');
}

body {
  background: black;
  font-family: 'Poppins', 'IntegralCF-Regular', sans-serif;
  color: #FFFFFF;
  margin: auto;
}
h1 {
    font-family: 'IntegralCF-Regular', sans-serif;
    font-size: 55px;
    line-height: 72px;
    font-weight: 400;
  }
h2 {
    font-family: 'IntegralCF-Regular', sans-serif;
    font-size: 32px;
    line-height: 48px;
    font-weight: 800;
  }
h3 {
    font-family: 'IntegralCF-Regular', sans-serif;
    font-size: 24px;
    line-height: 31px;
    font-weight: 400;
  }
p {
    font-family: 'Poppins', sans-serif;
    font-size: 24px;
    line-height: 36px;
    font-weight: 600;
    max-width: 769px;
    text-align: center;
    color: black;
  }
</style>

