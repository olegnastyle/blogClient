<template>
    <h1>Поиск</h1>

    <main>
        <button @click="searcAlert">Показать Search</button>
    </main>
</template>

<script setup>
const search = useSearchStore()

function searcAlert() {
    console.log(search.searchQuery);
    console.log(searchResponse);
}

const response = await $fetch(`https://a1c537287dd6.vps.myjino.ru/api/posts?filters[$or][0][title][$containsi]=${search.searchQuery}&filters[$or][1][body][$containsi]=${search.searchQuery}`)
const searchResponse = response.data


</script>