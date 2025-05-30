<template>
  <div class="wrapper">
    <header>
      <h2>Playable PIANO</h2>
      <div class="column volume-slider">
        <span>Volume</span>
        <input type="range" class="slider">
      </div>
      <div class="column keys-checkbox">
        <span>show keys</span>
        <input type="checkbox" @click="showKeys">
      </div>
    </header>
    <ul class="piano-keys">
      <li class="key white" @click="() => playNote('A')"><span  :class="{hidden: isChecked}">a</span></li>
      <li class="key black" @click="() => playNote('W')"><span  :class="{hidden: isChecked}">w</span></li>
      <li class="key white" @click="() => playNote('S')"><span  :class="{hidden: isChecked}">s</span></li>
      <li class="key black" @click="() => playNote('E')"><span  :class="{hidden: isChecked}">e</span></li>
      <li class="key white" @click="() => playNote('D')"><span  :class="{hidden: isChecked}">d</span></li>
      <li class="key white" @click="() => playNote('F')"><span  :class="{hidden: isChecked}">f</span></li>
      <li class="key black" @click="() => playNote('T')"><span  :class="{hidden: isChecked}">t</span></li>
      <li class="key white" @click="() => playNote('G')"><span  :class="{hidden: isChecked}">g</span></li>
      <li class="key black" @click="() => playNote('Y')"><span  :class="{hidden: isChecked}">y</span></li>
      <li class="key white" @click="() => playNote('H')"><span  :class="{hidden: isChecked}">h</span></li>
      <li class="key black" @click="() => playNote('U')"><span  :class="{hidden: isChecked}">u</span></li>
      <li class="key white" @click="() => playNote('J')"><span  :class="{hidden: isChecked}">j</span></li>
      <li class="key white" @click="() => playNote('K')"><span  :class="{hidden: isChecked}">k</span></li>
      <li class="key black" @click="() => playNote('O')"><span  :class="{hidden: isChecked}">o</span></li>
      <li class="key white" @click="() => playNote('L')"><span  :class="{hidden: isChecked}">l</span></li>
      <li class="key black" @click="() => playNote('P')"><span  :class="{hidden: isChecked}">p</span></li>
      <li class="key white" @click="() => playNote(';')"><span  :class="{hidden: isChecked}">;</span></li>
      
    </ul>
  :class="{hidden: 'isChecked'}"
  </div>
</template>

<script setup>
  import {ref} from 'vue'

  let isChecked = ref(true)

  const showKeys = () => {
    isChecked.value = !isChecked.value
  }

  // test audio
  const notes = {
    A: new Audio("/piano-mp3/A0.mp3"),
    W: new Audio("/piano-mp3/A1.mp3"),
    S: new Audio("/piano-mp3/B0.mp3"),
    E: new Audio("/piano-mp3/B4.mp3"),
    D: new Audio("/piano-mp3/C1.mp3"),
    F: new Audio("/piano-mp3/D1.mp3"),
    T: new Audio("/piano-mp3/D1.mp3"),
    G: new Audio("/piano-mp3/E1.mp3"),
    Y: new Audio("/piano-mp3/F1.mp3"),
    H: new Audio("/piano-mp3/F1.mp3"),
    U: new Audio("/piano-mp3/G1.mp3"),
    J: new Audio("/piano-mp3/C3.mp3"),
    K: new Audio("/piano-mp3/A2.mp3"),
    O: new Audio("/piano-mp3/A2.mp3"),
    L: new Audio("/piano-mp3/B2.mp3"),
    P: new Audio("/piano-mp3/C2.mp3"),
    ";" : new Audio("/piano-mp3/D2.mp3")
  }
  const playNote = (note) => {
    const sound = notes[note]
    if (sound){
      const audio = new Audio(sound.src)
      audio.play()
    }
  }
</script>

<style scoped>
.hidden{
  display: none;
}
</style>