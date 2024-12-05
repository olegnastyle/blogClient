<template>
    <h1>Поиск</h1>
    <main>
        
    </main>
</template>

<script setup>
const stringSearch = ref('')
const response = await $fetch(`https://a1c537287dd6.vps.myjino.ru/api/posts?filters[$or][0][title][$containsi]=${stringSearch}&filters[$or][1][body][$containsi]=${stringSearch}`)
const search = response.data

</script>