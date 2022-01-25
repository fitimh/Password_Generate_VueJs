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
            <span class="range-value"></span>
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
   props: {
      msg: String,
   },
};
</script>
