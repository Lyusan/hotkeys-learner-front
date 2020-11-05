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
        shift: { value: "shift", pressed: false },
        control: { value: "Ctrl", pressed: false }
      }
    };
  },
  components: {
    KeyboardButton
  },
  methods: {
    async keyDownHandler(event: any) {
      if (this.keys[event.key.toLowerCase()]) {
        this.keys[event.key.toLowerCase()].pressed = true;
      }
      }
    },
    keyUpHandler(event: any) {
      if (this.keys[event.key.toLowerCase()]) {
        this.keys[event.key.toLowerCase()].pressed = false;
      }
    }
  }
})
export default class Home extends Vue {}
</script>
