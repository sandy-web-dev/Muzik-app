<template>
  <div>
    <front-my-navbar/>
    <Nuxt />
    <front-my-footer/>
  </div>
</template>

<script>
  export default {
    scrollToTop: true
  }
</script>

<style>

:root {
  --iq-title-text: #222428;
  --iq-body-text:#4a525f;
  --iq-body-header:#FBFCFF;
  --iq-body-bg: #ffffff;
  --iq-primary: #ff4545;
  --iq-primary-pro: #ff4545;
  --iq-secondary: #a09e9e;
  --iq-success: #1ee2ac;
  --iq-warning: #ffdd31;
  --iq-danger: #ff7750;
  --iq-info: #00d0ff;
  --iq-dark: #01041b;
  --iq-light: #ccced2;
  --iq-white: #ffffff;
  --iq-black: #4a525f;
  --iq-gray: #c2c2c2;
  --iq-close: #ff4e4e;
  --iq-search: #b4a4ff;
  --iq-light-primary: #fcd9d8;
  --iq-light-secondary: #f1f2f1;
  --iq-light-success: #e1fff7;
  --iq-light-danger: #ffe4dc;
  --iq-light-warning: #fefaee;
  --iq-light-info: #f4f0ff;
  --iq-light-dark: #f0efef;
  --iq-light-close: #ffdbdb;
  --iq-light-menu: #9f8bf6;
  --iq-light-search: #5b43c7;
  --iq-light-hover: #b8b9bc;
  --iq-primary-hover: #fa3a3a;
  --iq-secondary-hover: #5b5959;
  --iq-success-hover: #0ce1a6;
  --iq-danger-hover: #f9663c;
  --iq-warning-hover: #ffdb23;
  --iq-info-hover: #03b6de;
  --iq-dark-hover: #00020f;
  --iq-border-light: #DFDFDF;
  --iq-border-danger: #ff9273;
  --iq-light-card: #ffffff;
  --iq-primary-rgb: 100, 114, 248;
  --iq-border-radius:0px 15px;
  --iq-bg-gray:#f8f8fd;
  --iq-hover:#ea0f0f;
  /* color for customizer*/
  --iq-color1: #4e37b2;
  --iq-color2: #02d871;
  --iq-color3: #309cf3;
  --iq-color4: #ff00ff;
  --iq-color5: #fb1f4c;
  --iq-color6: #00ced1;
  --iq-color7: #f35f3b;
  --iq-color8: #fde117;
  --iq-color9: #ff0000;
  --iq-color10: #88028c;
  --iq-color11: #00d5ab;
  --iq-color12: #ce9252;
  --iq-color13: #f9ae02;
  --iq-color14: #1e7fe4;
  --iq-color15: #006400;
  --iq-color16: #fa7c04;
  --iq-color17: #81bf02;
  --iq-color18: #99a7ca;
  --iq-color19: #3d2a26;
  --iq-color20: #a0746b;

}
.my-navbar .link-active-color{
  color: var(--iq-primary-pro)!important;
}
.content-page{
  overflow: hidden;
  padding: 20px 20px 10px;
  min-height: 100vh;
}
.iq-card{
  background: var(--iq-light-card);
  border-radius: 15px;
  margin-bottom: 30px;
  border: none;
  box-shadow: 0px 4px 20px 0px rgba(44, 101, 144, 0.1);
}
.fa-ellipsis-v{
  color: var(--iq-primary);
  font-size: 30px;
  margin-bottom: 15px;
}
[class^="hvr-"] {
  margin: .4em;
  padding: 0.5em;
  cursor: pointer;
  text-decoration: none;
  border-radius: var(--iq-border-radius);
  border: none;
  color: var(--iq-title-text);
}
.hvr-shutter-out-horizontal {
  display: inline-block;
  vertical-align: middle;
  transform: perspective(1px) translateZ(0);
  box-shadow: 0 0 1px rgba(0, 0, 0, 0);
  position: relative;
  transition-property: color;
  transition-duration: 0.3s;
}
.hvr-shutter-out-horizontal:before {
  content: "";
  position: absolute;
  z-index: -1;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  border-radius: var(--iq-border-radius);
  background: var(--iq-primary);
  transform: scaleX(0);
  transform-origin: 50%;
  transition-property: transform;
  transition-duration: 0.3s;
  transition-timing-function: ease-out;
}
.hvr-shutter-out-horizontal:hover,
.hvr-shutter-out-horizontal:focus,
.hvr-shutter-out-horizontal:active {
  color: white;
}
.hvr-shutter-out-horizontal:hover:before,
.hvr-shutter-out-horizontal:focus:before,
.hvr-shutter-out-horizontal:active:before {
  transform: scaleX(1);
}

 </style>
