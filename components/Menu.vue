<template>
        <nav class="font-mono">
            <ul class="flex space-x-4">
                <li>
                    <NuxtLink to="/" class="link">Main</NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/about" class="link">About</NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/projects" class="link">Projects</NuxtLink>
                </li>
                <li>
                    <NuxtLink to="/blogs" class="link">Blogs</NuxtLink>
                </li>
            </ul>
        </nav>
</template>

<style>
.link{
    @apply p-1 hover:bg-gray-200 dark:hover:bg-gray-800 transition-all duration-300
}
</style>
