<script setup>
const prop = defineProps(['msg'])
const emit = defineEmits(['update:msg'])

function reverseMsg(value) {
    emit('update:msg', value = "Vue Js Is Amazing!")
}
</script>

<template>
    <div class="space-y-1 mb-3">
        <h1 class="text-3xl my-1">Child Component</h1>
        <p>{{ prop.msg }}</p>
    </div>

    <a @click="reverseMsg(prop.msg)" class="px-6 text-2xl  py-1.5 bg-green-700 text-white hover:bg-orange-700 hover:text-white border-none  rounded-sm mr-4 cursor-pointer">Click Here To Get Custom Message</a>
</template>

<style scoped></style>