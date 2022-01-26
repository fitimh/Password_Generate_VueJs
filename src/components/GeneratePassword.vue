<template>
   <section class="wrapper">
      <h1>Generate Password</h1>
      <div class="password-box">
         <span id="password" class="password"></span>
         <span class="regenerate-password"></span>
         <span class="copy-password"></span>
         <span class="tooltip">Password copied successfuly!</span>
      </div>
      <form>
         <div class="field-wrap">
            <label>Strength</label>
            <span class="range-value">{{ set.length }}aa</span>
            <div class="range-slider_wrapper slider-strength">
               <span class="slider-bar"></span>
               <input
                  type="range"
                  class="range-slider"
                  min="0"
                  max="100"
                  disabled
               />
            </div>
         </div>
         <div class="seperator"></div>
         <div class="field-wrap">
            <label>Length</label>
            <span class="range-value"></span>
            <div class="range-slider_wrapper">
               <span class="slider-bar"></span>
               <input type="range" class="range-slider" min="6" />
            </div>
         </div>
         <div class="field-wrap">
            <label>Digits</label>
            <span class="range-value"></span>
            <div class="range-slider_wrapper">
               <span class="slider-bar"></span>
               <input type="range" class="range-slider" min="0" />
            </div>
         </div>
         <div class="field-wrap">
            <label>Symbols</label>
            <span class="range-value"></span>
            <div class="range-slider_wrapper">
               <span class="slider-bar"></span>
               <input type="range" class="range-slider" min="0" />
            </div>
         </div>
      </form>
   </section>
</template>

<script>
import "@/assets/css/style.css";
export default {
   name: "HelloWorld",
   data() {
      return {
         password: "",
         copied: false,

         set: {
            maxLength: 32,
            maxDigits: 6,
            maxSymbol: 6,
            length: 10,
            digits: 4,
            symbols: 2,
            ambiguous: true,
         },
      };
   },

   computed: {
      lengthThumbnailPosition: function () {
         return (this.set.length - 6 / this.set.length - 6) * 100;
      },
   },
};
</script>
