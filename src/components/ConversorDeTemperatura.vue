<template lang="html">

  <section class="container">
    <h1 class="title">Conversor de Temperatura</h1>
    <hr />
    <div>
      <p>Ingrese Temperatura °C</p>
      <input type="number" @input="calcularTemperaturas($event)"/> 
    </div>
    <div>
      <p>Con temperatura °F:</p> <span :style="setColorByTemp(tempEnCentigrados)">{{tempEnFarenheit}}</span>
      <p>Con temperatura °K:</p> <span :style="setColorByTemp(tempEnCentigrados)">{{tempEnKelvin}}</span>
    </div>
    <hr />
    <h2>Respuestas</h2>
    <p>1:c 2:b 3:d 4:c 5:b</p>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'form-view',
    props: [],
    mounted () {

    },
    data () {
      return {
        tempEnCentigrados: '',
        tempEnFarenheit: '',
        tempEnKelvin: '',
      }
    },
    methods: {
      calcularTemperaturas({target}) {
        this.tempEnCentigrados = target.value;
        this.tempEnFarenheit = this.tempEnCentigrados ? ((+this.tempEnCentigrados*(1.8)) + 32) : '';
        this.tempEnKelvin = this.tempEnCentigrados ? (+this.tempEnCentigrados + 273.15) : '';
      },
      setColorByTemp(temp) {
        let color = 'red';
        if (temp <= 0) {
          color = 'blue';
        } else if(temp > 0 && temp < 15) {
          color = 'magenta';
        }
        return { color };
      },
    },
    computed: {
    }
}


</script>

<style scoped lang="css">
.title {
  color: red;
}
</style>
