<template>
<div  class=" bg-center h-[844px] w-[440px] relative overflow-hidden mb-60" :style="{backgroundImage : `url(${bgImage})`}">
<Header/>
<img class=" absolute top-[100px]" :src="weather" alt="">
  <img class="h-[390px] w-[390px] absolute top-[304px] px-[8px] py-[16px] object-cover" :src="house">
  <div  class="down absolute top-[520px] ">
   <div :class="menuclass" class="test w-[385px] relative flex flex-col gap-4 bg-purple-900/60 backdrop-blur-md rounded-[50px] overflow-y-auto h-[700px] no-scrollbar duration-500">
   <div class="h-[850px] w-[390px] overflow-y-scroll">
    <Header v-if="menuSituation === 'open' "/>
    <div v-if="menuSituation === 'open' " class="flex justify-center items-center flex-col gap-2 my-3">
      <div class="text-white text-4xl">Montreal</div>
      <div class="text-gray-400">19°</div>
    </div>
   <div class="shapeBox">
    <img :src="separator" alt="">
    <img :src="ellipse" alt="" class="h-[1px] mt-[-2px]">
    <img :src="ellipse2" alt="">
    <img @click="goTop"  :src="tB" ref="top" alt="" :class="topclass" class=" mx-auto   mt-1 w-5 cursor-pointer block ">
    <img  @click="goDown" ref="down" :src="dB" alt="" :class="downclass" class=" mx-auto  mt-2 w-5 cursor-pointer block ">
    </div>
    <div v-if=" menuSituation === 'open'" class="flex justify-center mb-6 text-gray-400 mt-4 text-xl">Mostly clear</div>
    <div class="flex justify-between px-8 border-b-[1px] border-gray-500">
      <div class="flex flex-col justify-between py-3">
      <img :src="label" @click="changeToHourly" class=" cursor-pointer" alt="">
      <div class="relative" ref="under">
      <img :src="ellipse" alt="" class=" h-2 w-28 absolute top-2">
      <img :src="ellipse2" alt="" class=" h-2 w-28">
      </div>
      </div>
      <div class="py-3">
      <img :src="label2" @click="changeToWeekly" class=" cursor-pointer" alt="">
      </div>
    
    </div>
    <div class="flex flex-col gap-5 mt-5">
      <div class="flex gap-5 mx-5 overflow-x-scroll no-scrollbar h-[175px] overflow-y-scroll">
      <div  v-for="(item, index) in now" :key="index" :class="{
        'bg-indigo-700': item.now
      }"  class="bg-[rgba(72,49,157,0.2)] w-[60px] h-[160px] rounded-[30px] border border-gray-500 flex flex-col items-center gap-5 flex-shrink-0 text-white text-[14px] p-2" >
        <div  class="time">{{item.time}}</div>
        <img :src="item.weather" alt=""> 
        <div class="temp">{{item.temp}}</div>
      </div>
      </div>
    </div>
     <div class="p-5">
        <img :src="quality" alt="">
        <div class="flex gap-4">
            <img :src="uv" class="w-[164px] h-[140px]" alt="">
            <img :src="sunrise" class="w-[164px] h-[140px]" alt="">
        </div>
        <div class="flex gap-4 mt-5">
            <img :src="wind" class="w-[164px] h-[140px]" alt="">
            <img  :src="rainfall" class="w-[164px] h-[140px]" alt="">
        </div>
        <div v-if="menuSituation==='open' " class="flex gap-4 mt-5">
          <img :src="feels" class="w-[164px] h-[140px]" alt="">
          <img :src="humidity" class="w-[164px] h-[140px]" alt="">
        </div>
        <div v-if="menuSituation==='open' " class="flex gap-4 mt-5">
          <img :src="visibility" class="w-[164px] h-[140px]" alt="">
          <img :src="pressure" class="w-[164px] h-[140px]" alt="">
        </div>
      </div>
    </div>
   </div>
   <div 
   :class="menub" 
   class="menu h-[100px] w-[385px] absolute top-[250px] duration-300">
    <div class=" relative">
        <img :src="rect" alt="" class=" h-full">
          <img :src="symbol" alt="" class="absolute top-[35px] left-[40px]" >
          <router-link to="/weather">
          <img  :src="symbol2" alt="" class="absolute top-[35px] left-[320px]">
          </router-link>
          <img :src="subtract" alt="" class=" absolute top-[-12px] left-14">
          <img :src="plus" alt="" class="absolute top-[-12px] left-[130px]">
    </div>
    </div>
  </div>
</div>
</template>
<script setup>
import { computed, ref } from "vue";
import bgImage from "../assets/images/background.jpg";
import house from "../assets/images/House.png";
import Header from "../components/header.vue";
import weather from "../assets/images/Weather (1).png";
import modal from "../assets/images/Modal.png";
import separator from "../assets/images/Separator (1).png"
import rect from "../assets/images/Rectangle 364.png"
import subtract from "../assets/images/Subtract (1).png";
import shape from "../assets/images/Shape.png";
import ellipse from "../assets/images/Ellipse 2 (1).png";
import ellipse2 from "../assets/images/Ellipse 3 (1).png";
import label from "../assets/images/Label.png"
import label2 from "../assets/images/Label (1).png";
import hone from "../assets/images/moon-cloud-mid-rain.png";
import htwo from "../assets/images/moon-cloud-fast-wind.png";
import plus from "../assets/images/button.png";
import symbol from "../assets/images/Symbol.png";
import symbol2 from "../assets/images/Symbol (1).png";
import wone from "../assets/images/sun and rain.png"
import wtwo from "../assets/images/sun and wind.png";
import quality from '../assets/images/air-quality.png'
import uv from "../assets/images/uv index.png";
import sunrise from "../assets/images/sunrise.png";
import rainfall from "../assets/images/rainfall.png";
import wind from "../assets/images/wind.png";
import tB from "../assets/images/top.jpg"
import dB from "../assets/images/down.jpg"
import feels from "../assets/images/feels.png";
import humidity from "../assets/images/humidity.png";
import visibility from "../assets/images/visibility.png";
import pressure from "../assets/images/pressure.png";

import { RouterLink } from "vue-router";
const hourly = [
  {time: '12 AM' , weather : hone, temp : '19°'},
  {time: 'now', weather:hone, temp:'19°',now:'yes'},
  {time: '1 AM', weather: htwo, temp:'18°'},
  {time: '1 AM', weather:hone, temp:'19°'},
  {time: '1 AM', weather:hone, temp:'19°'},
  {time: '1 AM', weather:hone, temp:'19°'},
  {time: '1 AM', weather:hone, temp:'19°'},
  {time: '1 AM', weather:hone, temp:'19°'},
]
const weekly = [
  {time: 'MON', weather :wone , temp: '20°'},
  {time: 'TUE', weather :wone , temp: '21°', now:'yes'},
  {time: 'WEDN', weather :wtwo , temp: '18°'},
  {time: 'THU', weather :wtwo , temp: '20°'},
  {time: 'FRI', weather :wone , temp: '22°'},
  {time: 'SAT', weather :wtwo , temp: '24°'},
  {time: 'SON', weather :wone , temp: '23°'},
]
const isOnHourly = ref(true)
const under = ref(null)
const now = computed(() => isOnHourly.value ? hourly : weekly)
const top = ref(null)
const down = ref(null)
function changeToHourly() {
  isOnHourly.value = true
  under.value.classList.remove("left-52")
}
function changeToWeekly() {
  isOnHourly.value = false
  under.value.classList.add("left-52")
}
const menuSituation = ref('halfOpen')
const menuclass = computed(() => ({
  '-translate-y-[520px] h-[1300px] rounded-[0px]' : menuSituation.value === 'open',
  'translate-y-[150px]' : menuSituation.value === 'notOpen',
  '' : menuSituation.value === 'halfOpen',
}))
const topclass = computed(()=> ({
  'hidden' : menuSituation.value === 'open',
  'block' : menuSituation.value === 'notOpen' || menuSituation.value === 'halfOpen'
}))
const downclass = computed(()=> ({
  'hidden' : menuSituation.value === 'notOpen',
  'block' : menuSituation.value === 'open' || menuSituation.value === 'halfOpen',
  '-mt-[20px]' : menuSituation.value === 'Open',
}))
function goTop() {
  if (menuSituation.value === 'notOpen') {
    menuSituation.value = 'halfOpen'
  }
  else{
  menuSituation.value = 'open'
  }
}
const menub = computed(()=> ({
  'hidden' : menuSituation.value === 'open'
}))
function goDown() {
  if (menuSituation.value === 'open') {
    menuSituation.value = 'halfOpen'
    

  }
  else{
  menuSituation.value = 'notOpen'
  }
}

</script>