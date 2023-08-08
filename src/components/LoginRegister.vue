<script setup>
import { ref, reactive, computed } from 'vue'

// Login Process

const loginInfo = reactive({
  username: '',
  password: ''
})

function authentication() {
  if (loginInfo.username === formData.username && loginInfo.password === formData.password) {
    formState.welcome = true;
  } else {
    alert('Invalid Username Or Password')
  }
}

// Registration Process

const userData = []

const formData = reactive({
  username: '',
  email: '',
  password: '',
  confirmPassword: ''
})

function saveData() {
  userData.push(formData)
  alert('Registration Completed, Please Login')
  formState.isLogin = true;
}


// Form changing mechanism
const formState = reactive({
  isLogin: true,
  label: function () {
    if (this.isLogin) {
      return 'Register'
    } else {
      return 'Sign In'
    }
  },
  welcome: false,
})

function changeForm() {
  formState.isLogin = !formState.isLogin;
}

</script>

<template>
  <!-- Registration Form -->
  <form v-if="formState.isLogin == false" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 text-left">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="r">
        Username
      </label>
      <input
        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        id="usernamer" v-model="formData.username" type="text" placeholder="Username">
    </div>
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="emailr">
        Email
      </label>
      <input
        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        id="emailr" v-model="formData.email" type="text" placeholder="Email">
    </div>
    <div class="mb-1">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="passwordr">
        Password
      </label>
      <input
        class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
        id="passwordr" v-model="formData.password" type="password" placeholder="******************">
      <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
    </div>
    <div class="mb-6">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="Confirmpassword">
        Confirm Password
      </label>
      <input
        class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
        id="Confirmpassword" v-model="formData.confirmPassword" type="password" placeholder="******************">
      <p v-show="formData.password != formData.confirmPassword" class="text-red-500 text-xs italic">Confirm Password
        Doesn't Match</p>
    </div>
    <div class="flex items-center justify-between">
      <button :disabled="(formData.password != formData.confirmPassword) ? true : false" @click="saveData()"
        class="bg-orange-600 disabled:bg-gray-500 focus:outline-none border-none hover:bg-orange-700 text-white font-bold py-2 px-4 rounded "
        type="button">
        Register
      </button>
      <button @click="changeForm"
        class="inline-block focus:outline-none border-none align-baseline font-bold text-sm text-orange-600 hover:text-orange-800"
        type="button">
        Or {{ formState.label() }}
      </button>
    </div>

  </form>
  <!-- Registration Form -->

  <!-- Login Form -->
  <form v-if="formState.isLogin == true" :class="(formState.welcome) ? 'hidden' : ''"
    class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 text-left">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
        Username
      </label>
      <input v-model="loginInfo.username"
        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        id="username" type="text" placeholder="Username">
    </div>

    <div class="mb-1">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
        Password
      </label>
      <input v-model="loginInfo.password"
        class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
        id="password" type="password" placeholder="******************">
      <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
    </div>
    <div class="flex items-center justify-between">
      <button @click="authentication()"
        class="bg-orange-600 border-none hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none "
        type="button">
        Sign In
      </button>
      <button @click="changeForm"
        class="inline-block focus:outline-none border-none align-baseline font-bold text-sm text-orange-600 hover:text-orange-800"
        type="button">
        Or {{ formState.label() }}
      </button>


    </div>
 
  </form>
  <!-- Login Form End -->

  <!-- Welcome Screen -->
  <div v-show="formState.welcome == true" class="bg-white p-12 rounded-md shadow-lg mb-5">
    <p class="text-sm text-green-700 mb-5">Your are successfully loggedin</p>
    <h2 class="text-xl">Hello {{ loginInfo.username }}!, Thanks for choosing our platform.</h2>
  </div>
</template>
<style scoped></style>