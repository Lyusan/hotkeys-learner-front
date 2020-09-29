<template>
  <div class="hello">
    <h1>AOE 2 hotkey tool</h1>
    <p>
      Improve your knowledge and skill of your Age Of Empire II hotkeys.
    </p>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    msg: String
  }
})
export default class HelloWorld extends Vue {
  msg!: string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
