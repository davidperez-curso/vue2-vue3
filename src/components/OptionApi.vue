<template>
  <div>
    <h1>Option API</h1>
    <h2>Coche</h2>
    <p>Marca: {{ brand }}</p>
    <p>Modelo: {{ model }}</p>
    <p>Potencia: {{ power }}</p>
    <button @click="upPower(10)">Aumentar</button>
    <button @click="downPower">Dismninuir</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      brand: "Audi",
      model: "A4",
      power: 180,
    };
  },
  methods: {
    upPower(newPower) {
      console.log("aumentar potencia");
      this.power = this.power + newPower;
    },
    downPower() {
      console.log("disminuir potencia");
      this.power--;
    },
  },
};
</script>

<style></style>
