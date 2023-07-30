<template>
  <div></div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
//import Alert Message
import { showAlert }  from "@/mixin/message";
//import Interface
import { Keyboard }  from "@/assets/interfaces/keyboard";
let keyboard: Keyboard = {
  keyCodeValue: 0,
  keyValue: "",
  FilterResult: true,
  EnabledkeyboardButtons: [48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105, 13, 45, 35, 40, 34, 37, 12, 39, 36, 33, 38, 81, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90]
}
export default class KeyboardEvents extends Vue {
  // created hook
  created() {
    document.addEventListener("keydown", this.handleKeyDown);
  }
  // Before destroy hook
  beforeDestroy() {
    document.removeEventListener("keydown", this.handleKeyDown);
  }
  // handle clicks on keyboard
  handleKeyDown = (event: KeyboardEvent): void => {
    keyboard.keyCodeValue = event.keyCode;
    keyboard.keyValue = event.key;
    keyboard.FilterResult = keyboard.EnabledkeyboardButtons.includes(keyboard.keyCodeValue);

    if (keyboard.FilterResult) {
        showAlert(`you click on the keyboard button: { ${keyboard.keyValue} }`);
    }
  }
}
</script>