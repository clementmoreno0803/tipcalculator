<template>
  <button v-for="(tip, index) in tips" :key="index" @click="tipsValue(index)">
    {{ tip.valeur + "%" }}
  </button>
</template>
<script>
export default {
  name: "tipsbuton",
  data() {
    return {
      tips: [
        { valeur: 5, amount: 1.05 },
        { valeur: 10, amount: 1.1 },
        { valeur: 15, amount: 1.15 },
        { valeur: 25, amount: 1.25 },
        { valeur: 50, amount: 1.5 },
      ],
      props: { tips: Number },
    };
  },
  methods: {
    tipsValue(index) {
      this.$emit("val", {tipsamount: this.tips[index].amount});
    },
  },
};
</script>

<style>
</style>
