<template>
  <div>
    <KeyboardButton :keyb="keys.q" />
    <KeyboardButton :keyb="keys.Shift" />
    <KeyboardButton :keyb="keys.Control" />
    <input v-on:keyUp="keyUpHandler" v-on:keyDown="keyDownHandler" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import KeyboardButton from "@/components/KeyboardButton.vue"; // @ is an alias to /src

@Options({
  data: () => {
    return {
      keys: {
        q: { value: "q", pressed: false },
        Shift: { value: "shift", pressed: false },
        Control: { value: "Ctrl", pressed: false }
      }
    };
  },
  components: {
    KeyboardButton
  },
  methods: {
    keyDownHandler(event: any) {
      if (this.keys[event.key]) {
        this.keys[event.key].pressed = true;
      }
    },
    keyUpHandler(event: any) {
      if (this.keys[event.key]) {
        this.keys[event.key].pressed = false;
      }
    }
  }
})
export default class Home extends Vue {}
</script>
