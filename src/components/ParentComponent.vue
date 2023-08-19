<script setup>
import ButtonComponent from './ButtonComponent.vue';
import ChildComponent from './ChildComponent.vue';
import {ref, reactive} from 'vue'


const message = ref("Hello World, We are learning Vue JS from Ostad")

</script>

<template>
    <h1 class="text-3xl my-1">Parent Component</h1>
    <p>{{message}}</p>

    <hr class="my-4">

  <div class="mt-5">
    <ChildComponent v-model:msg="message"/>
  </div>

</template>

<style scoped>

</style>