<script setup>
import Pig from './Pig.vue'
import { Icon } from '@iconify/vue';
import { ref, onMounted, Transition } from "vue"

const softwareQualifiers = ref(['free', 'innovative', 'competitive', 'open source', 'efficient']);
const societalQualifiers = ref(['a happier', 'a better', 'an intentional'])
const activeSoftwareQualifier = ref('free')
const activeSocietalQualifier = ref('a happier')
const turn = ref(true);

const getNextIndex = (softwareQualifiers, activeSoftwareQualifier) => {
  const currentIndex = softwareQualifiers.value.indexOf(activeSoftwareQualifier.value);
  const next = softwareQualifiers.value[currentIndex + 1]
  return next ? currentIndex + 1 : 0;
}

const shuffleQualifiers = () => {
  const next = getNextIndex(softwareQualifiers, activeSoftwareQualifier)

  setTimeout(() => {
    activeSoftwareQualifier.value = softwareQualifiers.value[next];
  }, 500);

  activeSoftwareQualifier.value = null;
}

const shuffleOther = () => {
  const next = getNextIndex(societalQualifiers, activeSocietalQualifier)
  setTimeout(() => {
    activeSocietalQualifier.value = societalQualifiers.value[next];
  }, 500);

  activeSocietalQualifier.value = null;
}

onMounted(() => {
  setInterval(() => {
    if (turn.value) {
      shuffleQualifiers();
      turn.value = false
    }
  }, 5000)

  setInterval(() => {
    if (!turn.value) {
      shuffleOther()
      turn.value = true
    }
  }, 2500)
})


</script>

<template>
  <div id="container">
    <div id="container__landing">
      <Pig size="507"/>
      <div class="container__landing__welcome">
        <div id="heading">
          <div>Our mission</div>
          <div>is to make</div>
          <Transition name="slide" mode="out-in">
            <div class="green" v-if="activeSoftwareQualifier">{{ activeSoftwareQualifier }}</div>
            <div v-else></div>
          </Transition>
          <div>software for</div>
          <Transition name="slide" mode="out-in">
            <div class="green" v-if="activeSocietalQualifier">{{ activeSocietalQualifier}}</div>
          </Transition>
          <div>society.</div>
        </div>
      </div>
      <div id="cloud__container">
        <div class="cloud"></div>
      </div>
      <div id="cloud__container_2">
        <div class="cloud"></div>
      </div>
    </div>

  </div>
</template>

<style>
#container {
  width: 100%;
  margin-top: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  position: relative;
}

#container__landing, img, .container__landing__welcome {
  z-index: 2;
  font-family: 'gilroy-extrabold', serif;
}

.container__landing__welcome div#heading {
  overflow: hidden;
}

.container__landing__welcome div#heading div.green {
  color: var(--tea-green);
  font-size: 60px;
  font-weight: bold;
  margin: 10px 0px;
}

.container__landing__welcome div#heading div {
  width: 500px;
  overflow: hidden;
  height: 67px;
  font-size: 50px;
  display: flex;
  align-items: center;
  margin: 7px 0px;
}

#container__landing {
  width: 80%;
  height: calc(100vh - 50px);
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}
#container__landing div[id^="cloud"] {
  width: 300px;
  margin-left: 30px;
}
.container__about {
  padding-top: 100px;
  width: 80%;
  color: white;
  height: calc(100vh - 50px);
}
img {
  box-shadow: 10px 10px rgba(0,0,0,0.2);
}
.cloud {
  background: rgba(255, 255, 255);
  width: 300px;
  height: 100px;
  border-radius: 150px;
  box-shadow: 10px 10px rgba(0,0,0,0.2);
  animation: move 3s infinite;
}

.cloud:after {
  content: '';
  background: rgba(255, 255, 255);
  position: absolute;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  top: -50px;
  left: 50px;
}

.cloud:before {
  content: '';
  background: rgba(255, 255, 255);
  position: absolute;
  width: 170px;
  height: 150px;
  border-radius: 50%;
  top: -90px;
  right: 40px;
}

#cloud__container {
  z-index: 1;
  position: absolute;
  top:40%;
  left:23%;
  transform: translate(-50%,-50%);
}
#cloud__container_2 {
  z-index: 1;
  position: absolute;
  top: 70%;
  left: 50%;
  transform: translate(-50%,-50%);
}

#cloud__container_2 .cloud {
  transform: scale(3.9);
}
.block {
  width: 40%;
}
.slide-enter-active,
.slide-leave-active {
  transition: all .6s ease;
}

.slide-enter-from {
  transform: translateX(100%);
  opacity: 0;
}
.slide-enter-to, .slide-leave-from {
  transform: translateX(0%);
}
.slide-leave-to {
  transform: translateX(-100%);
  opacity: 0;
}
.svg {
  filter: drop-shadow(3px 3px rgb(0, 0, 0, 0.2));
}
</style>