<template>
  <div class="keyboard-key" :class="keyb.pressed ? 'pressed' : ''">
    <p>
      {{ keyb.value }}
    </p>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    keyb: String
  }
})
export default class HelloWorld extends Vue {
  keyb!: string;
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.keyboard-key {
  width: 3em;
  height: 3em;
  margin: 1em;
  border: 1px solid;
  border-radius: 3px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.pressed {
  background-color: rgb(105, 25, 25);
}
.pressed > p {
  color: azure;
}
</style>
