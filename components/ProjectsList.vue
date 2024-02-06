<template>
    <p class="mb-10">Take a look at my github project</p>
    <section v-if="pending">Loading ...</section>
    <section v-else-if="error">Something went wrong ... Try again</section>
    <section v-else>
        <ul class="grid grid-cols-1 gap-4">
            <li v-for="repository in repos" :key="repository?.id" class="border border-gray-300 p-4 cursor-pointer rounded-sm hover:bg-gray-200 font-mono">
                <a :href="repository.html_url" target="_blank">
                    <div class="flex items-center justify-between text-sm">
                        <div class="font-semibold text-black dark:text-gray-700">{{ repository.name }}</div>
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
// console.log(data)

const repos = computed(() => data.value.filter(repo => repo.description).sort((a,b)=> b.stargazers_count - a.stargazers_count))
</script>