<script setup>
    import { ref, onMounted } from 'vue'
    import Wrk from "./Wrk.vue"
    const title = ref('Hello Worldz!');
    let todos = ref([]);

</script>

<template>
    <h1>{{ title }}</h1>
    <input type="text" v-model="title">

    <Wrk></Wrk>
   
</template>

<style scoped>
ul {
    max-width: 600px;
    margin: 0 auto;
    text-align: left;
}
</style>