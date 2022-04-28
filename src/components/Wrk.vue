<script setup>
    import { ref, onMounted } from 'vue'
    let news = ref([]);

    onMounted(() => {
        fetch('https://wrk.weareimd.be/api/v1/tickers')
            .then(res => res.json())
            .then(data => {
                console.log(data.data);
                news.value = data.data[0].tickers;
            });
    });
</script>

<template>
    <h2>News</h2>
    <div>
        <ul>
            <li v-for="(n, index) in news" :key="index">x{{ n.tickerText }}</li>
        </ul>
    </div>
</template>

<style scoped>

</style>