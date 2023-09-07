<script setup>
import { ref } from 'vue'

const imgUrl = ref(new URL('./assets/default.png', import.meta.url).href)
const imgUrl2 = ref(new URL('./assets/default.png', import.meta.url).href)
const rd1 = ref(Math.floor(Math.random() * 4) + 1)
const rd2 = ref(Math.floor(Math.random() * 4) + 1)
const score1 = ref(0)
const score2 = ref(0)

const resetGame = () => {
  score1.value = 0
  score2.value = 0
  imgUrl.value = new URL('./assets/default.png', import.meta.url).href
  imgUrl2.value = new URL('./assets/default.png', import.meta.url).href
}

const randomizeImages = () => {
  rd1.value = Math.floor(Math.random() * 4) + 1
  rd2.value = Math.floor(Math.random() * 4) + 1

  if (rd1.value === 1 && rd2.value === 2) {

    score2.value += 1 
  } else if (rd2.value === 2 && rd1.value === 1) {
    score1.value += 1 
  } 
  
  else if (rd1.value === 2 && rd2.value === 3) {
    score2.value += 1 
  } else if (rd1.value === 3 && rd2.value === 2) {
    score1.value += 1 
  }
  
  else if (rd1.value === 3 && rd2.value === 1) {
    score2.value += 1 
  } else if (rd2.value === 3 && rd1.value === 1) {
    score1.value += 1 
  }

  
  else if (rd1.value === 1 && rd2.value === 2) {
    score2.value += 1 
  } else if (rd2.value === 1 && rd1.value === 2) {
    score1.value += 1 
  }

  if (rd1.value === 4) {
    score1.value += 1 
  }
  if (rd2.value === 4) {
    score2.value += 1 
  }


  if (rd1.value === 1) {
    imgUrl.value = new URL('./assets/rock.png', import.meta.url).href
  } else if (rd1.value === 2) {
    imgUrl.value = new URL('./assets/paper.jpg', import.meta.url).href
  } else if (rd1.value === 3) {
    imgUrl.value = new URL('./assets/scissors.jpg', import.meta.url).href
  } else {
    imgUrl.value = new URL('./assets/heart.png', import.meta.url).href
  }

  if (rd2.value === 1) {
    imgUrl2.value = new URL('./assets/rock.png', import.meta.url).href
  } else if (rd2.value === 2) {
    imgUrl2.value = new URL('./assets/paper.jpg', import.meta.url).href
  } else if (rd2.value === 3) {
    imgUrl2.value = new URL('./assets/scissors.jpg', import.meta.url).href
  } else {
    imgUrl2.value = new URL('./assets/heart.png', import.meta.url).href
  }
}
</script>

<template>
  <div class="container">
    <div class="image-container">
      <img :src="imgUrl" class="game-image" />
      <span class="score">คะแนน: {{ score1 }}</span>
    </div>
    <div class="image-container">
      <img :src="imgUrl2" class="game-image" />
      <span class="score">คะแนน: {{ score2 }}</span>
    </div>
    <div class="button">
    <button @click="randomizeImages" class="random-button">เริ่มเกม</button>
    <button @click="resetGame" class="reset-button">เริ่มใหม่</button>
  </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.buttons {
  display: flex;
  gap: 20px;
  margin-top: 20px;
}

.game-image {
  max-width: 200px;
  height: auto;
  margin: 10px;
}

.score {
  font-size: 18px;
  font-weight: bold;
}

.random-button {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
  border-radius: 5px;
  margin-top: 20px;
}

.reset-button {
  background-color: #ff0004;
  color: #fff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 16px;
  border-radius: 5px;
  margin-top: 20px;
  margin-left: 50px;
}

.random-button:hover {
  background-color: #0056b3;
}
</style>

