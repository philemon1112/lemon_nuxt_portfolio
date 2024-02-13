<template>
    <section class="not-prose font-mono max-w-none">
        <h2 class="text-2xl font-semibold mb-10">My Blogs</h2>
        <div class="column text-gray-400 text-sm">
            <div>Date</div>
            <div>Time</div>
        </div>
        <ul>
            <li v-for="post in posts" :key="post?._path">
                <NuxtLink :to="post?._path" class="column group cursor-pointer hover:bg-gray-300 dark:hover:bg-gray-800 ">
                    <div :class="{'text-white group-hover:text-gray-100 dark:text-gray-900 dark:group-hover:text-gray-900': !post?.displayYear, 'text-gray-400 dark:text-gray-600': post?.displayYear}">{{ post?.year }}</div>
                    <div>{{ post?.title }}</div>
                </NuxtLink>
            </li>
        </ul>
    </section>
</template>

<script setup>
    const {data} = await useAsyncData(
        'blog-list', ()=> queryContent('/blog')
        .where({ _path: {$ne: '/blog'}})
        .only(['_path', 'title', 'publishedAt'])
        .sort({publishedAt: -1})
        .find()
    )

    const posts = computed(() => {
        if(!data.value){
            return []
        }
        const result = []
        let lastyear = null; 

        for(const post of data.value){
            const year = new Date(post.publishedAt).getFullYear()
            const displayYear = year !== lastyear
            post.displayYear = displayYear
            post.year = year
            result.push(post) 
        }
        return result
    })

    console.log(posts)

    
</script>

<style>
.column{
    @apply flex items-center space-x-8 py-2 border-b border-gray-700
}
</style>