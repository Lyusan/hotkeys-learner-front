<template>
  <div>
    <KeyboardButton :keyb="keys.q" />
    <KeyboardButton :keyb="keys.shift" />
    <KeyboardButton :keyb="keys.control" />
    <input v-on:keyUp="keyUpHandler" v-on:keyDown="keyDownHandler" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import KeyboardButton from "@/components/KeyboardButton.vue"; // @ is an alias to /src
import * as fs from "fs";; // Load the File System to execute our common tasks (CRUD)
import { remote, dialog } from 'electron';

// eslint-disable-next-line
// @ts-ignore
import * as genieHki from "genie-hki";
const filepath = "C:/Users/leoch/Dev/hotkeys-learner-front/Hotkeys.hkit";


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
    KeyboardButton,
  },
  methods: {
    async keyDownHandler(event: any) {
      if (this.keys[event.key.toLowerCase()]) {
        this.keys[event.key.toLowerCase()].pressed = true;
      }
      const filepath = "C:/Users/leoch/Dev/hotkeys-learner-front/Hotkeys.hkit";
      await dialog.showOpenDialog(browserWindow => {
        // fileNames is an array that contains all the selected
        if(fileNames === undefined){
            console.log("No file selected");
            return;
        }

        fs.readFile(filepath, 'utf-8', (err, data) => {
            if(err){
                alert("An error ocurred reading the file :" + err.message);
                return;
            }

            // Change how to handle the file content
            console.log("The file content is : " + data);
        });
      });
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
