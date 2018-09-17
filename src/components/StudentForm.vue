<template>

</template>

<script>
export default {
    name: 'StudentForm',
    data(){
        return {
            firstName: '',
            lastName: '',
            lat: '',
            long: '',
            favAnimal: ''
        }
    },
    props: ['addToStudents']
}
</script>

<style>
form{
    display: flex;
    flex-flow: column nowrap;
}
</style>
