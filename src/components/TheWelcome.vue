<script setup>

</script>

<template>
<div class="flex justify-center items-center h-90">
  <div class="max-w-sm p-6 h-80 w-80 rounded-lg shadow bg-gray-800">
        <img class="w-24 h-24 rounded-full mx-auto" v-bind:src="picture"/>
       
        <h1 class="mb-2 text-2xl font-bold text-center tracking-tight text-gray-900 dark:text-white">{{ firstName }} {{ lastName }}</h1>
      
         
          <h3 class="font-normal text-center text-gray-700 dark:text-gray-400">{{ phone }}</h3>
          <h3 class="font-normal text-center text-gray-700 dark:text-gray-400">{{ email }}</h3>
      
   <br>
   <div class="flex justify-center items-center">
    <button class="rounded-full bg-gradient-to-br from-[#00DBDE] to-[#FC00FF] px-5 py-3 text-base font-medium text-white transition duration-200 hover:shadow-lg hover:shadow-[#FC00FF]/50  mb-80" v-on:click="getUser()">Get Random User</button>
  </div>

  </div>
  
</div>
  
</template>

<script>
export default {
  
  data() {
    return {
      firstName: "Jessica",
      lastName: "Jones",
      email: "test@example.com",
      phone: "222-222-2222",
      picture: "https://randomuser.me/api/portraits/med/women/1.jpg",
    }
  },
  methods: {
    async getUser() {
      
      let res = await fetch('https://randomuser.me/api/')
        let {results} = await res.json()
        // console.log(results)
      
        this.firstName = results[0].name.first
        this.lastName = results[0].name.last
        this.email = results[0].email
        this.phone = results[0].phone
        this.picture = results[0].picture.medium
    }
  }
}
</script>