<template>
<div class=" w-[390px] h-[844px] bg-gradient-to-b from-indigo-950 to-purple-900 flex flex-col gap-5 text-white pt-5 pb-10 ">
    <div class="text-white w-[390px] h-[47px] rounded-md flex justify-between items-center px-10">
  <div class="w-[54px] h-[21px]">1:41</div>
  <div class="w-[88px] h-[13px] flex gap-2">
    <img :src="signal" alt="">
    <img :src="wifi" alt="">
    <img :src="battery" alt="">
  </div>
</div>
<div class=" flex gap-40">
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
<div>
  <img :src="extra" alt="">
</div>
<div class="flex mx-5 flex-col overflow-x-scroll gap-4 no-scrollbar">
  <img :src="weather1" alt="">
  <img :src="weather2" alt="">
  <img :src="weather3" alt="">
  <img :src="weather1" alt="">
  <img :src="weather2" alt="">
</div>
</div>
</template>
<script setup>
import signal from "../assets/images/Mobile signal.png";
import wifi from "../assets/images/Wifi.png";
import battery from "../assets/images/Battery.png";
import back from "../assets/images/chevron.left.png";
import right from "../assets/images/right.png";
import extra from "../assets/images/Extra.png";
import weather1 from "../assets/images/Weather Widget.png"
import weather2 from "../assets/images/Weather Widget2.png"
import weather3 from "../assets/images/Weather Widget3.png"
import { RouterLink } from "vue-router";
</script>