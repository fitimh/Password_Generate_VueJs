<template>
  <section class="wrapper">
    <h1>Generate Password</h1>
    <div class="password-box">
      <span id="password" class="password"></span>
      <span class="regenerate-password" v-on:Click="generatePassword"></span>
      <span class="copy-password">{{ password }}</span>
      <span class="tooltip">Password copied successfuly!</span>
    </div>
    <form>
      <div class="field-wrap">
        <label>Strength</label>
        <span class="range-value"> {{ strength.text }}</span>
        <div
          class="range-slider_wrapper slider-strength"
          v-bind:class="strength.text"
        >
          <span class="slider-bar">hello</span>
          <input type="range" class="range-slider" min="0" max="100" disabled />
        </div>
      </div>
      <div class="seperator"></div>
      <div class="field-wrap">
        <label>Length</label>
        <span class="range-value">
          {{ set.length }}
        </span>
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
      return ((this.set.length - 6) / (this.set.maxLength - 6)) * 100;
    },
    digitsThumbPosition: function () {
      return ((this.set.digits - 0) / (this.set.maxDigits - 0)) * 100;
    },
    symbolThumbPosition: function () {
      return ((this.set.symbols - 0) / (this.set.maxSymbol - 0)) * 100;
    },
    strength: function () {
      var count = {
        excess: 0,
        upperCase: 0,
        numbers: 0,
        symbols: 0,
      };
      var weight = {
        excess: 3,
        upperCase: 4,
        numbers: 5,
        symbols: 5,
        combo: 0,
        flatLower: 0,
        flatNumber: 0,
      };
      var strength = {
        text: "",
        score: 0,
      };

      var baseScore = 30;

      for (i = 0; i < this.password.length; i++) {
        if (this.password.charAt(i).match(/[A-Z]/g)) {
          count.upperCase++;
          console.log(count.upperCase);
        }
        if (this.password.charAt(i).match(/[0-9]/g)) {
          count.numbers++;
          console.log(count.numbers);
        }
        if (this.password.charAt(i).match(/(.*[!,@,#,$,%,^,&,*,?,_,~])/)) {
          count.symbols++;
          console.log(count.symbols);
        }
      }
      count.excess = this.password.length - 6;

      if (count.upperCase && count.numbers && count.symbols) {
        weight.combo = 25;
      } else if (
        (count.upperCase && count.numbers) ||
        (count.upperCase && count.symbols) ||
        (count.numbers && count.symbols)
      ) {
        weight.combo = 15;
      }
      if (this.password.match(/^[\sa-z]+$/)) {
        weight.flatLower = -30;
      }

      if (this.password.match(/^[\s0-9]+$/)) {
        weight.flatNumber = -50;
      }

      var score =
        baseScore +
        count.excess * weight.excess +
        count.upperCase * weight.upperCase +
        count.numbers * weight.numbers +
        count.symbols * weight.symbols +
        weight.combo +
        weight.flatLower +
        weight.flatNumber;

      if (score < 30) {
        strength.text = "weak";
        strength.score = 10;
        return strength;
      } else if (score >= 30 && score < 75) {
        strength.text = "average";
        strength.score = 40;
        return strength;
      } else if (score >= 74 && score < 100) {
        strength.text = "strong";
        strength.score = 80;
        return strength;
      } else {
        strength.text = "secure";
        strength.score = 100;
        return strength;
      }
    },
  },
  mounted() {
     this.generatePassword();
  }
};
</script>
