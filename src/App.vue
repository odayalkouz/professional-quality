<template>
  <div>
    <KeyboardEvent/>  
    <MouseEvent/>
  </div>  
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import KeyboardEvent from "./components/KeyboardEvent.vue";
import MouseEvent from "./components/MouseEvent.vue";
@Options({
  components: {
    KeyboardEvent,
    MouseEvent,
  },
})
export default class App extends Vue {}
</script>

<style lang="sass">
body
  padding: 0
  margin: 0
  #app
    font-family: Avenir, Helvetica, Arial, sans-serif
    -webkit-font-smoothing: antialiased
    -moz-osx-font-smoothing: grayscale
    text-align: center
    color: #2c3e50

</style>
