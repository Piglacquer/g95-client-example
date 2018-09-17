<template>
    <div class='student-card'>
        <h1 v-on:click='showInfoToggle'>{{student.first}} {{student.last}}</h1>
        <img v-if='this.showInfo' :src=student.favAnimal>
        <small v-if='this.showInfo'>LAT: {{student.lat}} LONG: {{student.long}}</small> 
    </div>
</template>

<script>
export default {
  name: 'StudentCard',
  data(){
      return {
          showInfo: false
      }
  },
  methods: {
      showInfoToggle(){
          this.showInfo = !this.showInfo
      }
  },
  props: ['student']  
}
</script>

<style>
.student-card{
    display: flex;
    flex-flow: column nowrap;
    justify-content: center;
    align-items: center;
    background-color: seagreen;
    border-style: solid;
}

img {
    max-height: 30vh;
    max-width: 30vw;
}
</style>
