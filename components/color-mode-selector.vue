<template>
    <div class="flex items-center space-x-2">
        <div class="text-gray-400 text-xs" v-if="showNextModelabel">Change to {{ nextMode }}</div>
        <button @click="toggleMode" @mouseenter="showNextModelabel = true" @mouseleave="showNextModelabel = false" class="px-2 hover:bg-gray-100 dark:hover:bg-gray-600 py-1 text-gray-500">{{ nextModeItem }}</button>
    </div>
</template>

<script setup>
const showNextModelabel = ref(false)
const colorMode = useColorMode()

const modes = [
    'system',
    'light',
    'dark'
]

const nextModeIcons = {
    system: '🌓',
    light: '🌕',
    dark: '🌑'
}

const nextMode = computed(()=> {
    const currentModeIndex = modes.indexOf(colorMode.preference)
    let nextModeIndex = null
    if(currentModeIndex+1 === modes.length){
        nextModeIndex = 0
    }else{
        nextModeIndex = currentModeIndex + 1
    }
    
    return modes[nextModeIndex]
})

const nextModeItem = computed(()=> nextModeIcons[nextMode.value])
const toggleMode = () => {
    colorMode.preference = nextMode.value
}
</script>