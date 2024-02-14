<template>
    <div class="container mx-auto max-w-4xl">
        <header class="flex justify-between items-start md:items-center mt-2">
            <div class="flex md:space-x-12 items-center">
                <div class="hidden md:block">
                    <NuxtLink to="/" class="text-xl font-semibold py-2 px-3 hover:bg-gray-200 dark:hover:bg-gray-800 rounded-lg duration-300 transition-all ">
                        Lemon Nuxt
                    </NuxtLink>
                </div>
                <Menu />
            </div>

            <ClientOnly>
                <color-mode-selector />
            </ClientOnly>
        </header>

        <main class="px-2 mt-10">
            <slot />
        </main>
    </div>
</template>

<style>
    body{
        font-family: 'Roboto';
    }

    body{
        @apply bg-white dark:bg-gray-900 text-gray-700 dark:text-gray-300
    }
</style>
<script setup>
    const colorMode = useColorMode()
    console.log(colorMode.preference)

    useHead({
        titleTemplate: '%s - Lemon'
    })
</script>