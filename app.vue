<template>
  <NuxtLoadingIndicator throttle="0" />
  <Navbar />
  <NuxtPage />
  <Up />
  <Footer />
</template>

<script setup>
  const base = 'https://a1c537287dd6.vps.myjino.ru' 
  const api = await $fetch(`${base}/api/config?populate=*`)
  const config = api.data

  const isDarkMode = ref('')
  const isDark = ref(false)

  useHead({
    title: config.title,
    meta: [
      { name: 'description', content: config.desc },
      { name: 'keywords', content: config.keywords },
    ],
    link: [
      {
        rel: 'icon',
        type: 'image/x-icon',
        href: base+config.favicon.url
      },
      {
        rel: 'stylesheet',
        href: 'https://cdn.jsdelivr.net/npm/flowbite@2.5.2/dist/flowbite.min.css',
      },
    ],
    htmlAttrs: {
        class: isDarkMode.value
    },
    bodyAttrs: {
      class: 'container mx-auto bg-white dark:bg-gray-900'
    },
    head: {
      script: [
        {
          src: 'https://yastatic.net/share2/share.js',
          async: true,
          defer: true
        },
        {
          src: 'https://cdn.jsdelivr.net/npm/flowbite@2.5.2/dist/flowbite.min.js',
          async: true,
          defer: true
        }
      ]
    }
  })

onMounted(() => {
  if (localStorage.getItem('color-theme') === 'dark') {
      isDark.value = true;
      isDarkMode.value = 'dark'
  } else {
      isDark.value = false;
      isDarkMode.value = ''
  }
});
</script>