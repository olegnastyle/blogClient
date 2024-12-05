<template>
    <h1>Поиск</h1>

    <main>
        <article v-for="post in posts" :key="post.id">
            <h3>{{ post.title }}</h3>
        </article>
    </main>
</template>

<script setup>
const search = useSearchStore()
const posts = ref()

async function searchAlert() {
    console.log(search.searchQuery);

    try {
        const response = await $fetch(`https://a1c537287dd6.vps.myjino.ru/api/posts?filters[$or][0][title][$containsi]=${search.searchQuery}&filters[$or][1][body][$containsi]=${search.searchQuery}`);
        posts = response.data;
    } catch (error) {
        console.error('Ошибка при выполнении запроса:', error);
    }
}

onMounted(() => searchAlert())
</script>