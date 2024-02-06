<template>
    <div>Hello Phil</div>
</template>

<script setup>
useSeoMeta({
  title: 'Main Page',
  description: 'This is the main page',
  ogTitle: 'Main page',
  ogDescription: 'This is the main page',
  ogImage: 'hj',
  ogUrl: 'jhjkhg',
  twitterTitle: 'title',
  twitterDescription: 'desc',
  twitterImage: '',
  twitterCard: 'summary'
})

useHead({

    link: [
        {
        rel: 'preconnect',
        href: 'https://fonts.googleapis.com'
        },
        {
        rel: 'stylesheet',
        href: 'https://fonts.googleapis.com/css2?family=Roboto&display=swap',
        crossorigin: ''
        }
    ]
})

</script>