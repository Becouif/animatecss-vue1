<script setup>
import {ref} from 'vue'

let animateBlock = ref(false);

function handleBlock(){
  animateBlock.value = true;
}
</script>

<template>
  <div class="container">
    <div class="block" :class="{animate: animateBlock}">Hello world</div>
    <button @click="handleBlock">Animate</button>

  </div>
</template>

<style scoped>


.block {
  width: 8rem;
  height: 8rem;
  background-color: #290033;
  margin-bottom: 2rem;

}

/* we use keyframes to handle this stuff  */
.animate {
animation: slide-scale 0.5s ease-out forwards;
}
@keyframes slide-scale {
  0% {
    transform: translateX(0) scale(1);
  }

  70% {

    transform: translateX(-120px) scale(1.1)
  }

  100% {
    transform: translateX(-150px) scale(1);
  }
}
</style>