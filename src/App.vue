<template>
  <router-view/>
</template>

<style>
@font-face {
  font-family: "League";
  src: url("@/assets/fonts/league_font/League-ThinInline.otf") format("truetype");
  font-weight: thin;
  font-style: normal;
}

body {
  font-family: "League", sans-serif !important;
  min-height: 100%;
  background: linear-gradient(0deg,rgba(0, 0, 0, 1) 19%, rgba(56, 22, 22, 1) 100%, rgba(71, 0, 0, 1) 100%);
}

@media (min-width: 1024px) {
  html, body {
    overflow-y: hidden;
  }
}
</style>
