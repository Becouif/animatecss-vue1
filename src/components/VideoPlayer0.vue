<script setup>
import BaseDialog from './BaseDialog.vue';

import {ref} from 'vue';

const videoIsVisible = ref(false);
function showVideo(){
  videoIsVisible.value = true;
}

function hideVideo(){
  videoIsVisible.value = false;
}
</script>


<template>
  <div>
    <!-- we will emit close and send open props  -->
    <!-- transition is applied in VideoPlayer is in BaseDialog  -->
    <BaseDialog @close="hideDialog" :open="videoIsVisible"> 
      <iframe width="450" height="320" src="https://www.youtube.com/embed/-X64GJ0hpiQ?si=dVAQONo8eQHwhX4_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

      <button @click="hideVideo">Close it</button>
    </BaseDialog>
    <div class="container">
      <button @click="showVideo">Show Clip</button>
    </div>
  </div>
</template>