<style>
yt-live-chat-renderer {
  position: relative;
  height: 100%;
  z-index: 0;
  --color-head: #00bfa5;
  --color-body: #1de9b6;
}
@-webkit-keyframes insert {
  from {
    left: 100%;
  }
  to {
    left: 0px;
  }
}
@keyframes insert {
  from {
    left: 100%;
  }
  to {
    left: 0px;
  }
}
@-webkit-keyframes disappear {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@keyframes disappear {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
yt-live-chat-paid-message-renderer {
  position: relative;
  display: block;
  padding: 4px 24px;
  font-size: 15px;
  -webkit-animation-name: insert;
  animation-name: insert;
  -webkit-animation-duration: 1s;
  animation-duration: 1s;
}
yt-live-chat-paid-message-renderer {
}
#card {
  position: relative;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  min-width: 200px;
  overflow: hidden;
}
.close {
  font-size: 12px;
  position: absolute;
  right: 5px;
  top: 5px;
  display: none;
  z-index: 1;
}
#card:hover .close {
  display: block;
}
#header {
  position: relative;
  padding: 8px 16px;
  min-height: 20px;
  display: flex;
  flex-direction: row;
  align-items: center;
  color: var(--color-head-txt);
  background-color: var(--color-head);
}
#header-content-primary-column {
  display: flex;
  flex-direction: column;
}
#author-photo {
  width: 40px;
  height: 40px;
  overflow: hidden;
  border-radius: 50%;
  background-color: white;
  --default-src: url(https://yt3.ggpht.com/ytc/AAUvwnh3aAJX95-LepOS4z_EYe8P-Iv3l0TkhRmotxV5vBk=s176-c-k-c0x00ffffff-no-rj);
}
#author-photo #img {
  max-width: 100%;
  max-height: 100%;
}
#author-name {
  font-size: 14px;
}
#header-content {
  display: inline;
  min-width: 16px;
  padding: 0px 8px;
}
#content {
  padding: 8px 16px;
  color: var(--color-body-txt) !important;
  background-color: var(--color-body) !important;
}
#author-name {
  display: block;
  font-weight: 500;
}
#timestamp {
  display: inline;
  font-size: 13px;
}
.soundbutton {
  padding: 3px;
  font-size: 13px;
}
.text-break {
  word-wrap: break-word;
  word-break: break-word;
}
.scrank0 {
  /* rank0: blue */
  --color-head: #1565c0;
  --color-head-txt: #ffffff;
  --color-body: #1e88e5;
  --color-body-txt: #ffffff;
}
.scrank1 {
  /* rank1: light blue */
  --color-head: #00b8d4;
  --color-head-txt: #000000;
  --color-body: #00e5ff;
  --color-body-txt: #000000;
}
.scrank2 {
  /* rank2: green */
  --color-head: #00bfa5;
  --color-head-txt: #000000;
  --color-body: #1de9b6;
  --color-body-txt: #000000;
}
.scrank3 {
  /* rank3: yellow */
  --color-head: #ffb300;
  --color-head-txt: #000000;
  --color-body: #ffca28;
  --color-body-txt: #000000;
}
.scrank4 {
  /* rank4: orange */
  --color-head: #e65100;
  --color-head-txt: #ffffff;
  --color-body: #f57c00;
  --color-body-txt: #ffffff;
}
.scrank5 {
  /* rank5: purple */
  --color-head: #c2185b;
  --color-head-txt: #ffffff;
  --color-body: #e91e63;
  --color-body-txt: #ffffff;
}
.scrank6 {
  /* rank6: red */
  --color-head: #d00000;
  --color-head-txt: #ffffff;
  --color-body: #e62117;
  --color-body-txt: #ffffff;
}
.yt-small-image {
  /* this is for youtube superchat */
  max-width: 24px;
}

#contents {
  display: flex;
  flex-direction: column-reverse;
}
.sc-success {
  border-color: #28a745;
}
.sc-fail {
  border-style: solid none none none;
  border-color: #dc3545;
}
html {
  overflow-x: hidden;
}
</style>
<template>
  <yt-live-chat-renderer :class="[rank]"
    ><yt-live-chat-paid-message-renderer
      class="style-scope yt-live-chat-item-list-renderer"
      ><div id="card" class="style-scope yt-live-chat-paid-message-renderer">
        <span class="close"
          ><i class="fas fa-times" aria-hidden="true"></i
        ></span>
        <div id="header" class="style-scope yt-live-chat-paid-message-renderer">
          <yt-img-shadow
            id="author-photo"
            class="style-scope yt-live-chat-paid-message-renderer no-transition"
            ><img
              id="img"
              class="style-scope yt-img-shadow"
              v-bind:src="customize.authorImg"
          /></yt-img-shadow>
          <div
            id="header-content"
            class="style-scope yt-live-chat-paid-message-renderer"
          >
            <div
              id="header-content-primary-column"
              class="style-scope yt-live-chat-paid-message-renderer"
            >
              <div
                id="author-name"
                class="style-scope yt-live-chat-paid-message-renderer"
              >
                {{ props.author }}
              </div>
              <div
                id="purchase-amount-column"
                class="style-scope yt-live-chat-paid-message-renderer"
              >
                <div
                  id="purchase-amount"
                  class="style-scope yt-live-chat-paid-message-renderer"
                >
                  NT${{ props.cost }}
                </div>
              </div>
            </div>
          </div>
        </div>
        <div
          id="content"
          class="style-scope yt-live-chat-paid-message-renderer"
        >
          <div
            id="message"
            dir="auto"
            class="style-scope yt-live-chat-paid-message-renderer"
          >
            <span
              id="timestamp"
              class="style-scope yt-live-chat-paid-message-renderer"
              >{{ date }}</span
            ><span class="soundbutton"
              ><i class="fas fa-play" aria-hidden="true"></i
              ><!--v-if--></span
            ><span class="text-break"
              ><!-- Brute method for super sticker -->{{ props.msg }}
              <span v-show="customize.from" style="font-weight: bold"
                >來自 {{ donateFrom }}</span
              ></span
            >
          </div>
        </div>
      </div></yt-live-chat-paid-message-renderer
    ></yt-live-chat-renderer
  >
</template>
<script setup>
//
console.log(props.time);
import { computed } from "vue";
import { format } from "date-fns";
import { useStorage } from "@vueuse/core";
const style = {};
const props = defineProps(["cost", "author", "msg", "time", "from"]);
const date = computed(() => {
  var d = new Date(props.time);
  return format(d, "MM/dd p");
});
const donateFrom = computed(() => {
  const mapping = { opay: "歐付寶", ecpay: "綠界" };
  if (customize.value.from === true) {
    return mapping[props.from];
  }
  return "";
});

const customize = useStorage("customize", {});
console.log(customize.value);
const rank = computed(() => {
  if (props.cost < 30) return "scrank0";
  else if (props.cost >= 30 && props.cost < 75) return "scrank1";
  else if (props.cost >= 75 && props.cost < 150) return "scrank2";
  else if (props.cost >= 150 && props.cost < 300) return "scrank3";
  else if (props.cost >= 300 && props.cost < 750) return "scrank4";
  else if (props.cost >= 150) return "scrank5";
  return "scrank0";
});
</script>
