<template>
  <div class="container">
    <header>
      <h1 :class="message_color">{{ message }}</h1>
    </header>
    <hr />

    <section class="counter-section">
      <h2>Proses Hitung Angka, Terdapat Class dan Style Binding (Pada Danger)</h2>
      <br />
      <div class="buttons">
        <button @click="increment">Increment (+)</button>
        <button @click="reset">Reset</button>
        <button @click="decrement">Decrement (-)</button>
      </div>
      <div class="counter">
        <p v-if="counter >= 0" class="counter-value">{{ counter }}</p>
        <p v-else class="warning-text">Danger: {{ warning }}</p>
      </div>
    </section>

    <hr />

    <section class="input-section">
      <h2>Proses Ketik Input Data dan Ditampilkan secara Reactive dengan v-model</h2>
      <br />
      <input v-model="text_baru" placeholder="Ketik sesuatu di sini...">
      <div class="input-details">
        <p class="input-text">Text yang Diinput: {{ text_baru }}</p>
        <p class="input-length">Panjang Karakter yang Diinput: {{ text_length }}</p>
      </div>
    </section>
  </div>
</template>

<script setup>
  import { ref, computed } from 'vue';

  const message = ref('Selamat Datang di Pembelajaran M. Rafli Azriansyah!');
  const message_color = ref('color');
  const warning = ref('');
  const counter = ref(0);
  const text_baru = ref('');
  const text_length = computed(() => text_baru.value.length);

  function increment() {
    if (counter.value < 0) {
      counter.value = 0;
      warning.value = '';
    }
    counter.value++;
  }

  function reset() {
    counter.value = 0;
    warning.value = '';
  }

  function decrement() {
    counter.value--;
    if (counter.value < 0) {
      warning.value = "Gagal karena Kurang dari 0!";
    } else {
      warning.value = '';
    }
  }
</script>

<style scoped>
  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 20px;
    align-content: center;
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    font-family: 'Montserrat', sans-serif;
    color: #313154;
  }

  header {
    text-align: center;
    margin-bottom: 2rem;
  }

  h1 {
    font-size: 2.5rem;
    color: #3A82EE;
  }

  hr {
    margin: 2rem 0;
    border: none;
    border-top: 1px solid #ddd;
  }

  .counter-section,
  .input-section {
    margin-bottom: 2rem;
  }

  h2 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  .buttons {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .buttons button {
    padding: 1rem 2rem;
    font-size: 1.2rem;
    background-color: #3A82EE;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .buttons button:hover {
    background-color: #1A61D6;
  }

  .counter {
    text-align: center;
  }

  .counter-value {
    font-size: 2rem;
    margin-top: 0.5rem;
  }

  .warning-text {
    color: red;
    font-size: 1.2rem;
    font-weight: bold;
    margin-top: 0.5rem;
  }

  .input-section input {
    width: 95%;
    padding: 20px;
    font-size: 1.2rem;
    border: 1px solid #ccc;
    border-radius: 5px;
    transition: border-color 0.3s ease;
  }

  .input-details {
    margin-top: 1rem;
  }

  .input-text,
  .input-length {
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
  }
</style>
