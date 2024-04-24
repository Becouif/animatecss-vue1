<script setup> 
import {ref} from 'vue'
// datas 
const paragraphIsToggle = ref(false);
const enterInterval = ref(null);
const leaveInterval = ref(null);

// methods 
function toggleParagraph(){
  paragraphIsToggle.value = !paragraphIsToggle.value;
}
// the done parameter will be use as done function to tell vue we are done with an event 
function enterPara(element, done){
  // this element show the element of the div transition is in control of 
  let round = 1;
  enterInterval.value = setInterval(()=> {
    element.style.opacity = round * 0.01;
    round++;
    if(round > 100){
      clearInterval(enterInterval.value);
      done()
    }
  }, 20);

}
function leavePara(element, done){
  window.console.log('para');

  let round = 1;
  leaveInterval.value = setInterval(()=> {
    element.style.opacity = 1- round * 0.01;
    round++;
    if(round > 100){
      clearInterval(leaveInterval.value);
      done()
    }
  }, 20);
}

function enterCancelled(){
  // we use clearInterval function in js 
  clearInterval(enterInterval.value);
}
function leaveCancelled(){
  clearInterval(leaveInterval.value);
}

</script>



<template>
  <!-- here we use transition event to handle the animation instead of using css  -->
  <div class="container">
    <transition :css="false" @enter="enterPara" @leave="leavePara" @enter-cancelled="enterCancelled" @leave-cancelled="leaveCancelled" mode="out-in">
      <div v-if="paragraphIsToggle">
        <h1>This is the heading</h1>
        <p>this is a paragraph</p>
      </div>

    </transition>

    <button @click="toggleParagraph">Toggle Paragraph</button>
  </div>
</template>