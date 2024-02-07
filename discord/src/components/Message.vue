<template>
  <div class="message-box">
    <b-icon-plus class="icon-add" />
    <input class="message-input" type="text" v-model="chat" />
    <span class="right-buttons">
      <b-icon-gift-fill class="icons icon-gift" />
      <emoji
        set="twitter"
        :emoji="{ id: randomEmoji }"
        :size="22"
        @mouseenter="switchEmoji"
        @click="showPicker = !showPicker"
        class="icons"
        :style="{ display: 'inline' }"
      />
      <picker
        @select="pushEmoji"
        set="twitter"
        :style="{ position: 'absolute', right: '10px' }"
        v-show="showPicker"
      />
    </span>
  </div>
</template>

<script>
import { BIconGiftFill, BIconPlus } from "bootstrap-vue";
import { Emoji, Picker } from "emoji-mart-vue";
import { smileys } from "@/assets/smileyList.js";

export default {
  name: "Emojis",
  components: { BIconPlus, BIconGiftFill, Emoji, Picker },
  data: () => {
    return {
      chat: "",
      showPicker: false,
      randomEmoji: "santa",
    };
  },
  methods: {
    switchEmoji() {
      let random = Math.floor(Math.random() * Math.floor(smileys.length));
      this.randomEmoji = smileys[random];
    },
    pushEmoji(emoji) {
      this.chat += emoji.native;
      this.showPicker = !this.showPicker;
    },
  },
};
</script>

<style lang="scss">
.icon-add {
  cursor: pointer;
  border: none;
  border-radius: 999px;
  background: rgb(87, 80, 80);
  background-color: white;
  font-size: 18px;
  margin: 0px 10px 0px 20px;
}
.message-box {
  background: #99aab5;
  display: flex;
  align-items: center;
  padding: 5px;
  border-radius: 7px;
  height: auto;
  margin: auto auto;
}
.message-input {
  margin: 5px 10px;
  border: none;
  border-radius: 99px;
  background: inherit;
  width: 100%;
  font-size: 18px;
  color: white;
  &:focus {
    outline: none;
  }
}

.right-buttons {
  margin-left: auto;
}
.emoji {
  cursor: pointer;
}
.icon-gift {
  color: #2c2f33;
  font-size: 20px;
}
.icons {
  display: inline;
  color: lightgray;
  margin-right: 20px;
  &:hover {
    color: white;
  }
}
</style>
