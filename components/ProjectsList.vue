<template>
    <p class="mb-10">Take a look at my github project</p>
    <section v-if="pending">Loading ...</section>
    <section v-else-if="error">Something went wrong ... Try again</section>
    <section v-else>
        <!-- <a href="/deploy/vercel" class="block px-6 py-8 border not-prose rounded-lg border-gray-200 dark:border-gray-800 hover:bg-gray-100/50 dark:hover:bg-gray-800/50 group text-right"><div class="inline-flex items-center rounded-full p-1.5 bg-gray-100 dark:bg-gray-800 group-hover:bg-primary/10 ring-1 ring-gray-300 dark:ring-gray-700 mb-4 group-hover:ring-primary/50"><span class="i-ph-arrow-right w-5 h-5 text-gray-900 dark:text-white group-hover:text-primary"></span></div><p class="font-medium text-gray-900 dark:text-white text-[15px] mb-1">Vercel</p><p class="text-sm font-normal text-gray-500 dark:text-gray-400 line-clamp-2">Deploy your Nuxt Application to Vercel infrastructure.</p></a> -->
        <ul class="grid grid-cols-1 gap-4">
            <li v-for="repository in repos" :key="repository?.id" class="border border-gray-300 p-4 cursor-pointer rounded-sm hover:bg-gray-200 dark:border-gray-800 hover:bg-gray-100/50 dark:hover:bg-gray-800/50 group font-mono">
                <a :href="repository.html_url" target="_blank">
                    <div class="flex items-center justify-between text-sm">
                        <div class="font-semibold text-black dark:text-gray-300 dark:hover:text-gray-400">{{ repository.name }}</div>
                        <div class="">{{ repository.stargazers_count }} *</div>
                    </div>
                    <p class="text-sm pt-1 text-gray-500">{{ repository.description }}</p>
                </a>
            </li>
        </ul>
    </section>
</template>

<script setup>
    const {error ,pending, data} = await useFetch('https://api.github.com/users/philemon1112/repos', {method: 'get'})
    // console.log(data);
    const repos = computed(() => data.value.filter(repo => repo.description).sort((a,b)=> b.stargazers_count - a.stargazers_count))
</script>