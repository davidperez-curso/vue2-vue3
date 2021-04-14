<template>
  <div>
    <h1>Composition API</h1>
    <h2>Coche</h2>
    <p>Marca: {{ brand }}</p>
    <p>Modelo: {{ model }}</p>
    <p>Potencia: {{ power }}</p>
    <p>Props desde app : {{propsPower}}</p>
    <p>power desde app : {{power2}}</p>
    <button @click="upPower(10)">Aumentar</button>
    <button @click="downPower">Dismninuir</button>
    <button @click="downPower2">Disminuir desde app</button> <!-- si hemos traido la funcion mediante props, podemos usarla directamente -->
  </div>
</template>

<script>
import { ref } from "vue";
//si vamos a ocupar funciones que modifiquen el valor de los datos
//debemos importar ref y añadirlo al dato

export default {
  props: {
    //los props deben ser igual al tipo de variable que traen: Number, string, etc.
    //pueden tener un valor default en caso de que la informacion no llegue o de que lo necesitemos.
    //no es necesario retornar los props ya que ya están siendo retornados desde su componente original
    propsPower: {
      type: Number,
      default: 60,
    //propsPower: Number
    },
    power2: Number,
    downPower2: Function,
    //usamos props con una función, el tipo debe ser Function.
  },
  //En vez de data() se utiliza setup y los datos deben ir como constantes
  // y siempre ser retornados con return{}
  setup() {
    //setup(props)//console.log(props.propsPower)
    const brand = "audi";
    const model = "A4";
    let power = ref(180); // si el dato es una constante no podrá cambiar
    // ni se le podrá asignar una función que cambie su valor
    //por lo tanto debe ser let


    //funciones van dentro del setup y deben ser retornadas de igual forma
    //que los demás datos
    const upPower = (newPower) => {
      console.log("aumentar potencia");
      power.value= power.value + newPower; // cuando usamos setup ya no podemos ocupar el this
      //por lo cual debemos llamar directamente al dato, pero si queremos modificar
      //su valor, debemos ser más especificos en el llamado, en este caso
      //aumentaremos el value del dato
    };
    const downPower = () => {   
      console.log("disminuir potencia");
      power.value--;
    };

    // si queremos que la funcion que hemos traido desde otro componente haga más cosas, simplemente debemos
    // crear otra función e ingresar dentro de ella la función de los props, ej:
    // const otraFunción = () => {
    //      props.downPower2();
            /* otras funciones*/
    //   }

    return {
      brand,
      model,
      power,
      upPower,
      downPower,
    };
  },
};
</script>

<style></style>
