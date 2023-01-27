<script setup>
import { useImage } from '@vueuse/core'
const avatarUrl = 'https://s1.ax1x.com/2023/01/23/pSYuIYD.png'
const waka = 'https://wakatime.com/badge/user/84476697-3421-4720-bcdc-efb5c0fbc1b8.svg?style=flat-square'
const kita = 'https://picxyxsw.oss-cn-hangzhou.aliyuncs.com/kita.gif'
const { isLoading } = useImage({ src: avatarUrl })
const { isLoading_waka } = useImage({ src: waka })
const { isLoading_kita } = useImage({ src: kita })
const to_left = () => {
  document.getElementsByClassName('img')[0].classList.remove('to_right')
  document.getElementsByClassName('right_text')[0].classList.remove('to_right_text')
  document.getElementsByClassName('right_block')[0].classList.remove('to_right_block')
  document.getElementsByClassName('left_block')[0].classList.remove('to_left_block')
  document.getElementsByClassName('left_img')[0].classList.remove('to_left_img')
}
const to_right = () => {
  document.getElementsByClassName('img')[0].classList.add('to_right')
  document.getElementsByClassName('right_text')[0].classList.add('to_right_text')
  document.getElementsByClassName('right_block')[0].classList.add('to_right_block')
  document.getElementsByClassName('left_block')[0].classList.add('to_left_block')
  document.getElementsByClassName('left_img')[0].classList.add('to_left_img')
}
</script>

<template>
  <main class="w-[384px] h-[256px] text-center text-light-700 bg-[#f69db2] font-sans">
    <div class="h-100% w-100% flex flex-row justify-between p-5 items-center gap-5">
      <div class="absolute left-0 top-0 translate-x-[-100%]">
        <div class="flex flex-col justify-end left_block duration-700 ">
          <div class="bg-[#60c5e7] p-5" />
          <div class="bg-[#f3d263] p-5" />
        </div>
      </div>
      <div class="absolute left-0 top-0 translate-x-[-100%]">
        <span v-if="isLoading" class="animate-pulse bg-[#0A4445] px-11.5 py-16 text-center font-black">Loading</span>
        <img v-else :src="kita" class="left_img duration-400">
      </div>
      <span v-if="isLoading" class="animate-pulse bg-[#0A4445] px-11.5 py-16 text-center font-black">Loading</span>
      <img v-else :src="avatarUrl" class="w-35 h-35 img duration-700">
      <div class="flex flex-col gap-5 h-119%">
        <div class="flex flex-row justify-end translate-x-4.9 right_block duration-700 ">
          <div class="bg-[#60c5e7] p-5" />
          <div class="bg-[#f3d263] p-5" />
        </div>
        <div class="flex flex-col gap-5 pt-8 right_text duration-700 ">
          <div class="text-center font-bold text-lg text-[#df4b57]">
            👋  Hi, I’m  @camera-2018
          </div>
          <span v-if="isLoading" class="animate-pulse bg-[#0A4445] px-15 text-center font-black">Loading</span>
          <a v-else href="https://wakatime.com/@84476697-3421-4720-bcdc-efb5c0fbc1b8"><img :src="waka" alt="Total time coded since May 9 2022"></a>
        </div>
      </div>
    </div>
    <footer class="bg-[#f69db2] ">
      <button class="i-carbon-caret-left hover:bg-[#1DCED1] bg-light-50" @click="to_left" />
      <button class="i-carbon-caret-right hover:bg-[#1DCED1] bg-light-50" @click="to_right" />
    </footer>
  </main>
</template>

<style>
.to_right{
  @apply translate-x-142% transition
}

.to_right_text {
  @apply translate-x-190% transition
}

.to_right_block {
  @apply translate-y-[-120%] transition
}

.to_left_block {
  @apply translate-x-100% transition
}

.to_left_img {
  @apply translate-x-90% transition
}
</style>
