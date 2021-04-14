<template>
  <div>
    <OptionApi />
    <hr />
    <CompApi :propsPower="propsPower" :power2="power2" 
    :downPower2="downPower2"/>
  </div>
</template>

<script>
import { ref } from 'vue';
//siempre que vayamos a cambiar el valor de un dato por medio de una función debemos
//importar ref y agregarlo al dato que será intervenido

import CompApi from "@/components/CompApi.vue";
import OptionApi from "@/components/OptionApi.vue";



export default {
  name: "App",
  components: {
    CompApi,
    OptionApi,
  },
  setup(){
    let propsPower = 30;
    let power2 = ref(50);

    const downPower2 = () => {
      power2.value --
    }

    return {
      propsPower,
      power2,
      downPower2,
    }
  }
};
</script>

<style></style>
