<template>
  <v-main class="bg-black">
    <v-divider color="#30AEFF"></v-divider>
    <v-container>
      <v-row align="center" class="justify-center no-gutters row-aligment">
        <div cols="6">
          <v-img :src="imageUrl" height="300" width="300" rounded="circle" :class="{ 'pulse-animation': isPulsing }"/>
        </div>
        <div cols="6">
          <div>
              <h1 :class="{ 'typing-animation': isTypingTitle }" class="display-1 ">{{ title }}</h1>
              <p v-if="isTypingDescription" :class="{ 'typing-animation-delayed': isTypingDescription }" class="body-1 ">{{ description }}</p>
          </div>
        </div>
      </v-row>
    </v-container>
  </v-main>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue';

const isPulsing = ref(false);
const isTypingTitle = ref(false);
const isTypingDescription = ref(false);
const imageUrl = '/presentation.jpg';

const title = "Hi, my names is Brenno";
const description = "I'm a full stack developer, I like to work with everything and a little, curious and willing.";

function startPulsing() {
  isPulsing.value = true;
}

function stopPulsing() {
  isPulsing.value = false;
}

function startTitleTypingAnimation() {
  isTypingTitle.value = true;
}

function startDescriptionTypingAnimation() {
  nextTick(() => {
    isTypingDescription.value = true;
  });
}

onMounted(() => {
  startPulsing();
  startTitleTypingAnimation();
  setTimeout(startDescriptionTypingAnimation, 3500); 
});
</script>

<style scoped>

.row-aligment {
    margin-top: 100px;
    gap: 400px;
}

.pulse-animation {
  animation: pulse 1s infinite alternate;
}

.typing-animation {
  overflow: hidden; 
  border-right: .15em solid 30AEFF; 
  white-space: nowrap;
  margin: 0; 
  letter-spacing: .15em;
  animation: typing 4.5s steps(40, end), blink-caret .75s step-end infinite;
}

.typing-animation-delayed {
  overflow: hidden; 
  border-right: .15em solid #30AEFF; 
  white-space: nowrap;
  margin: 0;
  letter-spacing: .15em; 
  animation: typing 4.5s steps(40, end), blink-caret .75s step-end infinite;
}

@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: #30AEFF }
}
</style>
