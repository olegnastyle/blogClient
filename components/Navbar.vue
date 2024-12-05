<template>
    <button @click="goToSearch">Перейти</button>
</template>

<script setup>
const router = useRouter()
const isActive = (path) => router.path.split('/')[1] === path

function goToSearch() {
    router.replace('/search')
}
</script>