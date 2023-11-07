<script setup lang="ts">
import QRCode from "qrcodejs2-fix";
import { computed, onMounted, ref } from "vue";

const androidCRef = ref<HTMLElement | null>(null);
const androidPRef = ref<HTMLElement | null>(null);
const iosC = `https://open.test.luojigou.vip/admin/211/ipa/qrcode/c/逻辑狗.jpg`;
const iosP = computed(() => {
  return `https://open.test.luojigou.vip/admin/211/ipa/qrcode/parent/${new Date().getDate()}-parent-bate.jpg`;
});
async function makeCode(val: any, url: string) {
  if (val) val.innerHTML = "";
  new QRCode(val, {
    text: url, // 需要转换为二维码的内容
    width: 200,
    height: 200,
    colorDark: "#000000",
    colorLight: "#ffffff",
  });
}

onMounted(() => {
  makeCode(androidCRef.value, "https://www.pgyer.com/app/qrcode/4tao");
  makeCode(androidPRef.value, "https://www.pgyer.com/app/qrcode/t50F");
});
</script>

<template>
  <h3 class="title">逻辑狗APP测试</h3>
  <div class="download">
    <div class="download-item">
      <div ref="androidCRef"></div>
      <div class="nowrap">android一起成长</div>
    </div>
    <div class="download-item">
      <div ref="androidPRef"></div>
      <div class="nowrap">android家园共育</div>
    </div>
    <div class="download-item">
      <img :src="iosC" alt="" />
      <div class="nowrap">ios一起成长</div>
    </div>
    <div class="download-item">
      <img :src="iosP" alt="" />
      <div class="nowrap">ios家园共育</div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.title {
  position: fixed;
  top: 20px;
  left: 0;
  width: 100%;
  text-align: center;
}
.download {
  display: flex;
  flex-wrap: wrap;
  //flex-direction: column;
  justify-content: space-around;
  align-items: center;
  width: 100%;
  height: 100vh;

  &-item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px;

    .nowrap {
      margin-top: 20px;
      white-space: nowrap;
    }
  }
}
</style>
