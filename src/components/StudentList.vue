<template>
    <div>
        <h1>IM THE STUDNET LIUST </h1>
        <StudentCard v-for='(student, index) in students' v-bind:key='"studentCard" + index' :student='student'/>
    </div>
</template>

<script>
import StudentCard from './StudentCard'

export default {
  name: 'StudentList',
  props: ['students'],
  components:{
      StudentCard
  }  
}
</script>

<style scoped>
</style>

