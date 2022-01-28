<template>
  <div>
    <button @click="counterComputed++">computed button</button>
    <p>{{ counterComputed }}</p>
    <br />
    <button @click="counterMethod++">method button</button>
    <p>{{ counterMethod }}</p>
    <br />
    {{ printTextMethod() }}
    {{ printTextComputed }}
  </div>
</template>
<script>
export default {
  name: "Hello",
  data: function () {
    return {
      counterComputed: 0,
      counterMethod: 0,
    };
  },
  computed: {
    printTextComputed: function () {
      console.log("counter printed from computed:", this.counterComputed);
      return 0;
    },
  },
  methods: {
    printTextMethod: function () {
      console.log("counter printed from method:", this.counterMethod);
    },
  },
};
</script>
