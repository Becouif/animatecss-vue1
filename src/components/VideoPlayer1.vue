<script setup>
import BaseDialog from './BaseDialog.vue';
import {ref} from 'vue';

const videoIsVisible = ref(false);
function showVideo(){
  videoIsVisible.value = true;

}

function hideVideo() {
  videoIsVisible.value = false;
}

</script>

<template>
  <div>
    <!-- from basedialog we need to emit close and send props open  -->
    <BaseDialog :open="videoIsVisible">
    <!-- video html  -->
    <video controls width="250" class="myvideo">
      <!-- <source src="/media/cc0-videos/flower.webm" type="video/webm" /> -->

      <source src="../assets/videos/song.mp4" type="video/mp4" />

      <!-- Download the -->
      <!-- <a href="/media/cc0-videos/flower.webm">WEBM</a> -->
      <!-- or -->
      <a href="../assets/videos/song.mp4">MP4</a>
      video.
    </video>

    <!-- button to close the dialog  -->
    <button @click="hideVideo">Close it</button>
    
    </BaseDialog>

    <div class="container">
      <button @click="showVideo">Show Music Video</button>
    </div>

  </div>
</template>

<style scoped>
.myvideo {
  width: 480px;
  height: 300px;

  /* width="450" height="320" */
}


</style>