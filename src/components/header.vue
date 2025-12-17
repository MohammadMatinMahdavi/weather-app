<template>
    <div class="text-white w-[390px] h-[47px] rounded-md flex justify-between px-7 items-center">
  <div class="w-[54px] h-[21px]">1:41</div>
  <div class="w-[88px] h-[13px] flex gap-2">
    <img :src="signal" alt="">
    <img :src="wifi" alt="">
    <img :src="battery" alt="">
  </div>
</div>
</template>
<script setup>

import signal from "../assets/images/Mobile-signal.png";
import wifi from "../assets/images/Wifi.png";
import battery from "../assets/images/Battery.png";
</script>