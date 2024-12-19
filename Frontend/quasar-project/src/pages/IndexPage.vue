<template>
  <q-page class="flex flex-center q-pa-md">
    <div class="content-container">
      <h1 class="welcome-text">Dobrodošli u našu knjižnicu</h1>
      <p class="description-text">
        Ovdje možete pregledavati knjige, pretraživati literaturu i rezervirati naslove koji vas zanimaju.
        Uživajte u svijetu znanja i mašte!
      </p>
      <div class="image-container">
        <img
          alt="Slika knjižnice"
          src="~assets/library.jpg"
          class="library-image"
        />
      </div>
    </div>
  </q-page>
</template>

<script setup>
defineOptions({
  name: 'IndexPage'
});
</script>

<style scoped>
.content-container {
  max-width: 800px;
  text-align: center;
}

.welcome-text {
  font-size: 2.5em;
  font-weight: bold;
  color: #4a4a4a;
  margin-bottom: 16px;
}

.description-text {
  font-size: 1.2em;
  color: #6a6a6a;
  margin-bottom: 32px;
  line-height: 1.6;
}

.image-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 16px;
}

.library-image {
  width: 100%;
  max-width: 600px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}
</style>
