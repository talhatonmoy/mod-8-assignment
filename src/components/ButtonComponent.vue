<script setup>
defineProps(['link', 'label'])

</script>

<template>
    <a :href="link"  class="px-6 text-2xl  py-1.5 bg-green-700 text-white hover:bg-orange-700 hover:text-white border-none  rounded-sm mr-4">{{ label }}</a>
</template>

<style scoped>

</style>