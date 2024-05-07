<script setup>
import { ref } from 'vue'

  const message = ref('Selamat Datang di Pembelajaran M. Rafli Azriansyah!')
  const message_color = ref('color')
  const warning = ref('')
  const counter = ref(0)
  const color_warning = ref('warning')
  const text_baru = ref('')
  const text_length = ref(0)
  
  function increment(){
    if(counter.value < 0){
      counter.value = 0
    }
    counter.value++
  }
  
  function reset(){
    counter.value = 0
  }

  function decrement(){
    counter.value--
    if(counter.value < 0){
      warning.value = "Gagal karena Kurang dari 0!"
    }
  }

  function ubahMerah(){
    color_warning.value = ref('warning')
  }
</script>

<template>
  <h1 :class="message_color">
    {{ message }}
  </h1>
  <hr>
  <h2>
    Ini adalah Proses Hitung Angka. Ketika kurang dari 0, maka text peringatan berubah warna merah
  </h2>
  <button @click="increment">
    Increment
  </button>
  <br>
  <br>
  <button @click="reset">
    Reset
  </button>
  <br>
  <br>
  <button @click="decrement">
    Decrement
  </button>
  <br>
  <br>
  <h3 v-if="counter >= 0">
    Angka Terhitung : {{ counter }}
  </h3>
  <h3 v-else :class="color_warning">Danger : {{ warning }}</h3>
  <hr>
  <h2>
    Ini adalah Proses Ketik Input Data dan ditampilkan secara reactive dengan v-model
  </h2>
  <input v-model="text_baru">
  <br>
  <br>
  <p>Text yang Diinput : {{ text_baru }}</p>
  <p>Panjang Karakter yang Diinput : {{ text_baru.length }}</p>
</template>

<style scoped>
/* Ini untuk kebutuhan Melakukan class Binding dan Style Binding */
  .warning {
    color: red;
  }

  .fontsize {
    font-size: 30px;
  }

  .color {
    color: aqua;
  }
</style>