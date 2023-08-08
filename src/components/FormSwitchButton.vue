<script setup>
const isLogin = ref(true)

function changeForm() {
    isLogin.value = !isLogin.value;
    console.log(isLogin.value)
}
</script>

<template>
   
</template>

<style scoped>
</style>