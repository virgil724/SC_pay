<style></style>
<template>
  <div id="contents" class="style-scope yt-live-chat-app ">
    <super-chat
      v-for="(data, index) in dataArray"
      :author="data.name"
      :cost="data.amount"
      :msg="data.msg"
      :time="data.time"
      :key="index"
    />
  </div>
  <!-- <v-btn @click="period_post"></v-btn> -->
  
</template>
<script setup>
import SuperChat from "@/components/SuperChat.vue";
import { useStorage, useIntervalFn } from "@vueuse/core";
import axios from "axios";
import { reactive, computed } from "vue";
import { unionBy } from "lodash-es";
const data = reactive({ opay: [], ecpay: [] });
const state = useStorage("payid");
const { pause, resume, isActive } = useIntervalFn(async() => {
  /* your function */
  await period_post()
}, 5000)
const dataArray = computed(() => {
  return [
    ...data.ecpay.map((v) => ({ ...v, from: "ecpay" })),
    ...data.opay.map((v) => ({ ...v, from: "opay" })),
  ];
});
async function period_post() {
  console.log(data);
  const options = {
    method: "POST",
    url: "https://pay.virgil246.workers.dev/",
    headers: {
      "content-type": "application/json",
    },
    data: JSON.stringify(state.value),
  };
  axios
    .request(options)
    .then(function (response) {
      console.log(response.data);
      data.opay = unionBy(
        response.data.opay.map((v) => ({ ...v, time: Date.now() })),
        data.opay,
        "donateid"
      );
      data.ecpay = unionBy(
        response.data.ecpay.map((v) => ({ ...v, time: Date.now() })),
        data.ecpay,
        "donateid"
      );
    })
    .catch(function (error) {
      console.error(error);
    });
}
</script>
