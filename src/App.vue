<template>
   <GeneratePassword msg="Welcome to Your Vue.js App" />
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css";
import GeneratePassword from "./components/GeneratePassword.vue";
// <link
//    rel="stylesheet"
//    href="https://use.fontawesome.com/releases/v5.15.4/css/all.css"
//    integrity="sha384-DyZ88mC6Up2uqS4h/KRgHuoeGwBcD4Ng9SiP4dIRy0EXTlnuz47vAwmeGwVChigm"
//    crossorigin="anonymous"
// ></link>;

export default {
   name: "App",
   components: {
      GeneratePassword,
   },
};
</script>

<style></style>
