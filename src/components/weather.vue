<template>
<div class=" w-[410px] h-[844px] md:w-[700px] bg-gradient-to-b from-indigo-950 to-purple-900 flex flex-col gap-5 text-white pt-5  ">
    <div class="text-white w-[390px] md:w-[700px]  h-[47px]  rounded-md flex gap-[180px] md:gap-[510px] items-center px-10">
  <div class="w-[54px] h-[21px] ">1:41</div>
  <div class="w-[88px] h-[13px] flex gap-2 md:w-full">
    <img  :src="signal" alt="">
    <img :src="wifi" alt="">
    <img :src="battery" alt="">
  </div>
</div>
<div class=" flex gap-[140px] md:gap-[450px] mx-[20px]">
  <div  class=" px-5 flex gap-2 ">
  <router-link to="/" class="flex items-center pt-3">
<img :src="back" alt="">
  </router-link>
<div class=" text-[30px] flex items-center">
  <p>weather</p>
  </div>
  </div>
  <div class=" pt-3">
    <img :src="right" alt="">
  </div>

</div>
<div class="mx-[40px]">
  <input v-model="input" @keydown="filterTheWeather" type="text" placeholder="search for a city" class="rounded-xl p-2 bg-blue-900 w-full">
</div>
<div class="flex mx-[40px] flex-col overflow-x-scroll gap-4 no-scrollbar">
  <div class="md:flex gap-4">
  <img :class="weatherClass('montreal')" class="md:w-2/3 duration-500" :src="weather1" alt="">
  <img :class="weatherClass('toronto')" class="md:w-2/3 duration-500" :src="weather2" alt="">
  </div>
  <div class="md:flex gap-4">
  <img :class="weatherClass('tokyo')" class="md:w-2/3 duration-500" :src="weather3" alt="">
  <img :class="weatherClass('montral')" class="md:w-2/3 duration-500" :src="weather1" alt="">
  </div>
  <div class="md:flex">
  <img :class="weatherClass('toronto')" class="md:w-[300px] " :src="weather2" alt="">
  </div>
</div>
</div>
</template>
<script setup>
import signal from "../assets/images/Mobile-signal.png";
import wifi from "../assets/images/Wifi.png";
import battery from "../assets/images/Battery.png";
import back from "../assets/images/chevron.left.png";
import right from "../assets/images/right.png";
import extra from "../assets/images/Extra.png";
import weather1 from "../assets/images/Weather Widget.png"
import weather2 from "../assets/images/Weather Widget2.png"
import weather3 from "../assets/images/Weather Widget3.png"
import { RouterLink } from "vue-router";
import { computed, ref } from "vue";



var input = ref('')
function weatherClass(city) {
  return city.includes(input.value.toLowerCase()) ? '' : 'hidden'
}

</script>