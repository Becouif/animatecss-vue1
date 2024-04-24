<script setup>
import {ref} from 'vue';
import ButtonAnimate from './components/ButtonAnimate.vue';
import BaseDialog from './components/BaseDialog.vue';
import VideoPlayer from './components/VideoPlayer0.vue';
import Paragraph from './components/Paragraph.vue';
import VideoPlayer1 from './components/VideoPlayer1.vue';


const dialogIsVisible = ref(false);

function showDialog(){
  dialogIsVisible.value = true;
}
function hideDialog(){
  dialogIsVisible.value = false;
}

</script>

<template>
  <!-- start div -->
  <div>
    <ButtonAnimate />

    <!-- open is a props from basedialog  -->
    <div class="container">
      <BaseDialog @close="hideDialog" :open="dialogIsVisible">
        <p>This is test dialog</p>
        <button @click="hideDialog">Close it!</button>
      </BaseDialog> 
      <div>
        <button @click="showDialog">Show Dialog</button>
      </div>
    </div>

    <!-- start of paragraph  -->
    <Paragraph />
    <!-- start of video show  -->
    <!-- youtube video player embedded  -->
    <VideoPlayer />

    <!-- music video player from a downloaded video  -->
    <VideoPlayer1 />


    <!-- end div  -->
  </div>
</template>



<style>
.container {
  max-width: 40rem;
  margin: 2rem auto;
  display: flex;
  justify-content: center;
  align-items:center;
  flex-direction: column;
  padding: 2rem;
  border:2px solid #ccc;
  border-radius: 12px;
}
</style>