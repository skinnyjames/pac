<script setup>
 import { Icon } from '@iconify/vue';

</script>

<template>
  <nav>
    <ul>
      <li class="active">Pig Admirers Club</li>
      <li>Mission</li>
      <li>Handbook</li>
      <li>News</li>
      <li>Our work</li>
      <!--
      <li class="active"><Icon icon="twemoji:pig-face" /> Pig Admirers Club</li>
      <li><Icon icon="twemoji:globe-showing-americas" /> Mission</li>
      <li><Icon icon="twemoji:green-book"/> Handbook</li>
      <li><Icon icon="twemoji:newspaper" /> News</li>
      <li><Icon icon="twemoji:light-bulb" /> Our work</li>
      -->
    </ul>
  </nav>
</template>

<style scoped>
  nav {
    width: 100%;
    height: 60px;
    display: flex;
    align-items: flex-end;
    color: var(--cultured);
    padding: 0px;
    justify-content: center;
    font-weight: bold;
    position: fixed;
    z-index: 5;
    background-color: var(--bluesky-light);
    top: 0;
    font-family: 'gilroy-extrabold', serif;

  }

  nav ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
    display: flex;
    height: 50px;
  }

  nav ul li {
    padding: 0;
    width: 160px;
    margin: 0;
    height: 80%;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 10px;
  }

  li:hover, li.active {
    cursor: pointer;
    background-color: var(--bluesky);
    color: var(--cultured);
    border-radius: 20px;
  }

  li svg {
    margin-right: 5px;
  }
</style>