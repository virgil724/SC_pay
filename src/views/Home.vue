<template>
  <v-container>
    <v-card title="輸入Opay 和Ecpay id">
      <v-card-item>
        <v-text-field
          label="opay"
          v-model="state.opay"
          :loading="loading"
          :disabled="loading"
          :error-messages="opay_error"
        ></v-text-field>

        <v-text-field
          label="ecpay"
          v-model="state.ecpay"
          :loading="loading"
          :disabled="loading"
          :error-messages="ecpay_error"
        ></v-text-field>
      </v-card-item>

      <v-card-title>自訂義區</v-card-title>
      <v-card-item>
        <v-text-field v-model="customize.authorImg" label="頭像"></v-text-field>
        <v-switch class="pl-5" label="是否顯示Donate來源" color="blue" v-model="customize.from"> </v-switch>
      </v-card-item>

      <v-card-actions>
        <v-btn variant="outlined" v-on:click="test">測試</v-btn>
        <v-btn variant="outlined" @click="routeChange">確定</v-btn>
      </v-card-actions>
    </v-card>
  </v-container>
  <super-chat author="XXX" cost="100" msg="這是一筆測試贊助~" :time="date" from="ecpay" />
</template>

<script setup>
import { useStorage } from "@vueuse/core";
import axios from "axios";
import { ref, onBeforeMount } from "vue";
import { useRoute, useRouter } from "vue-router";
import SuperChat from "@/components/SuperChat.vue";
const default_val = {
  opay: "",
  ecpay: "",
};
const customizeDefault = {
  authorImg: "https://cdn-icons-png.flaticon.com/512/1995/1995463.png",
};
const customize = useStorage("customize", customizeDefault);
const date = ref(Date.now());
const defaultRoute = "Home";
const state = useStorage("payid", default_val);
const routeVal = useStorage("routes", defaultRoute);
const loading = ref(false);
const ecpay_error = ref("");
const opay_error = ref("");
const route = useRoute();
const router = useRouter();
// onBeforeMount(()=>{
//   if (routeVal.value==="SC"){
//     routeChange();
//   }
// })
function test() {
  const options = {
    method: "POST",
    url: "https://pay.virgil246.workers.dev/test",
    headers: { "content-type": "application/json" },
    data: JSON.stringify(state.value),
  };
  ecpay_error.value = "";
  opay_error.value = "";
  loading.value = true;
  axios
    .request(options)
    .then(function (response) {
      console.log(response.data);
      loading.value = false;
      if (response.data.opay) {
        state.value.opay = "";
        opay_error.value = "請再確認一次";
      }
      if (response.data.ecpay) {
        state.value.ecpay = "";
        ecpay_error.value = "請再確認一次";
      }
    })
    .catch(function (error) {
      console.error(error);
    });
}

function routeChange() {
  routeVal.value = "SC";
  router.push({
    name: "SCLog",
  });
}
</script>
