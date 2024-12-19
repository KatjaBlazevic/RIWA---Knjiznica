<template>
  <q-page class="flex flex-center" padding>
    <div class="q-pa-md" style="max-width: 400px; width: 100%">
      <h1 class="text-center text-h4 q-mb-md">Unesite podatke o knjizi</h1>
      <q-form class="q-gutter-md" @submit.prevent="onSubmit" @reset="onReset">
        <q-input
          filled
          v-model="naslov"
          label="Naslov knjige"
          hint="Naslov knjige"
        />
        <q-input filled v-model="autor" label="Autor" />
        <q-input filled v-model="opis" label="Opis" />
        <q-input filled v-model="slika" label="URL slike" />
        <q-input filled v-model="stanje" label="Broj knjige" />

        <q-toggle v-model="accept" label="I accept the license and terms" />

        <div class="q-mt-md flex justify-start">
          <q-btn
            label="Submit"
            type="submit"
            @click="insertBook()"
            class="submit-btn q-mr-sm"
          />
          <q-btn label="Reset" type="reset" flat class="reset-btn" />
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";
import axios from "axios";

export default {
  setup() {
    const naslov = ref(null);
    const autor = ref(null);
    const opis = ref(null);
    const slika = ref(null);
    const stanje = ref(null);
    const accept = ref(false);

    const onSubmit = () => {
      console.log("Form submitted");
      // Dodajte logiku za slanje podataka ili spremanje
    };

    const onReset = () => {
      naslov.value = "";
      autor.value = "";
      opis.value = "";
      slika.value = "";
      stanje.value = "";
      accept.value = false;
    };

    return {
      naslov,
      autor,
      opis,
      slika,
      stanje,
      accept,
      onSubmit,
      onReset,
    };
  },

  methods: {
    async insertBook() {
      const formData = {
        naslov: this.naslov,
        autor: this.autor,
        opis: this.opis,
        slika: this.slika,
        stanje: this.stanje,
      };

      try {
        const result = await axios.post(
          "http://localhost:3000/api/unos_knjiga/",
          formData
        );
        console.log(result.data);
        alert("Knjiga je uspješno unesena!");
      } catch (error) {
        console.error("Greška pri unosu knjige:", error);
        alert("Došlo je do greške pri unosu knjige.");
      }
    },
  },
};
</script>

<style scoped>
.q-page {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

h1 {
  font-size: 2.5em;
  font-weight: bold;
  text-transform: uppercase;
  color: #4a4a4a;
  margin-bottom: 32px; /* Dodan razmak između naslova i obrasca */
}

.submit-btn {
  background-color: #fce4ec; /* Postavljamo boju gumba submit */
  color: #151629; /* Boja teksta na gumbu */
}

.reset-btn {
  background-color: #fce4ec; /* Postavljamo boju gumba reset */
  color: #151629; /* Boja teksta na gumbu */
}

.q-btn {
  margin-top: 16px;
}

.full-width {
  width: 100%;
}

.q-form {
  max-width: 400px;
  width: 100%;
}

.q-input,
.q-toggle {
  margin-bottom: 16px;
}

.q-toggle {
  margin-top: 16px;
}

.flex {
  display: flex;
  justify-content: center; /* Centriramo gumbe */
  gap: 16px; /* Dodajemo razmak između gumba */
}

.q-mt-md {
  display: flex;
  justify-content: center; /* Centriramo cijeli roditeljski div za gumbe */
  width: 100%; /* Osiguravamo da roditelj zauzima cijelu širinu */
}

.q-mt-md .q-btn {
  margin-top: 0; /* Uklanjamo dodatni razmak s vrha */
}
</style>
