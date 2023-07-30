<template>
  <section>
    <div 
      :style="{ backgroundColor: `hsl(${mouseX}, 80%, 50%)` }">Mouse is moving in position ( X : {{ mouseX }}, Y: {{ mouseY }} )
    </div>
  </section>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
//import Alert Message
import  { showAlert }  from "@/mixin/message"
export default class MouseEvents extends Vue {
  mouseX: number = 0;
  mouseY: number = 0;

  // created hook
  created() {
    document.addEventListener("mousemove", this.handleMouseMove);
  }
  // Before destroy hook
  beforeDestroy() {
    document.removeEventListener("mousemove", this.handleMouseMove);
  }
  // handle mouse move and mouse right click 
  handleMouseMove = (event: MouseEvent): void => {
    this.mouseX = event.clientX;
    this.mouseY = event.clientY;
    if (event.which === 3 || event.button === 2) {
       showAlert('Mouse is clicked on right button');
    }
  }
}
</script>
<style lang="sass" scoped>
 section
  display: flex
  align-items: center
  justify-content: center
  height: 100vh
  div
   display: block
   width: 100%
   background-color: -webkit-linear-gradient(45deg, #09009f, #00ff95 80%)
   background-clip: text
   -webkit-background-clip: text
   -webkit-text-fill-color: transparent
   font-size: 2.5vw
   transition: 0.3s background-color ease
</style>