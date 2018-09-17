<template>
  <div id="app">
      <h1>G95 BABY</h1>
      <!-- form should be handled in another component, but this is easier -->
      <div>
        <form v-on:submit.prevent='addToStudents'>
            <label for='firstName'>First Name:</label>
            <input type='text' name='firstName' v-model='firstName'>
            <label for='lastName'>Last Name:</label>
            <input type='text' name='lastName' v-model='lastName'>
            <label for='lat'>Lat:</label>
            <input type='text' name='Lat' v-model='lat'>
            <label for='long'>Long:</label>
            <input type='text' name='long' v-model='long'>
            <label for='favAnimal'>Favorite Animal:</label>
            <input type='text' name='favAnimal' v-model='favAnimal'>
            <input type='submit' value='SUBMIT'>
          </form>
       </div>
      <StudentList v-bind:students='students.data'/>
  </div>
</template>

<script>
import StudentList from './components/StudentList'
import StudentForm from './components/StudentForm'

export default {
  name: 'app',
  data(){
    return {
      students: [],
      firstName: '',
      lastName: '',
      lat: '',
      long: '',
      favAnimal: ''
    }
  },
  methods: {
    getStudents(){
      fetch('https://g95server.herokuapp.com/')
        .then(response => response.json())
        .then(response => this.students = response)
    },
    addToStudents(){
      var newStood = {
        id: 14,
        first: this.firstName,
        last: this.lastName,
        lat: this.lat,
        long: this.long,
        favAnimal: this.favAnimal
      }
      this.students.data.splice(0,0, newStood)
    }
  },
  mounted(){
    this.getStudents()
  },
  components: {
    StudentList,
    StudentForm
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-flow: column nowrap;
  width: 100vw;
  background-color:gray;
}

form {
  display: flex;
  justify-content: center;
  align-items: center;
}

input {
  width: 48vw;
}
</style>
