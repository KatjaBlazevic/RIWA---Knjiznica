<template>
  <q-page padding class="flex flex-center bg-grey-1">
    <q-card flat bordered class="q-pa-lg login-card shadow-2">
      <q-card-section>
        <h1 class="text-center">Prijava</h1>
        <p class="text-center text-dark">Unesite svoje korisničke podatke za prijavu.</p>
      </q-card-section>

      <q-card-section>
        <q-input
          v-model="username"
          label="Korisničko ime"
          outlined
          dense
          class="q-mb-md"
        />
        <q-input
          v-model="password"
          label="Lozinka"
          type="password"
          outlined
          dense
          class="q-mb-md"
        />
      </q-card-section>

      <q-card-actions align="center">
        <q-btn
          label="Prijava"
          class="bg-red-2 text-white full-width"
          unelevated
          @click="loginUser"
        />
      </q-card-actions>
    </q-card>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      username: "",
      password: ""
    };
  },
  methods: {
    loginUser() {
      if (this.username.trim() && this.password.trim()) {
        console.log("Podaci za prijavu:", this.username, this.password);

        // Resetiraj unos nakon prijave
        this.username = "";
        this.password = "";

        // Preusmjeri na stranicu popisa knjiga
        this.$router.push({ name: "PopisKnjigaPage" });
      } else {
        // Prikaži obavijest za grešku
        this.$q.notify({
          color: "negative",
          position: "top",
          message: "Molimo unesite korisničko ime i lozinku.",
          timeout: 3000
        });
      }
    }
  }
};
</script>

<style scoped>
h1 {
  font-size: 2em;
  font-weight: bold;
  text-transform: uppercase;
  color: #4a4a4a;
}

p {
  font-size: 1.1em;
  margin-bottom: 1em;
}

.login-card {
  max-width: 400px;
  width: 100%;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  border-radius: 8px;
}

.full-width {
  width: 100%;
}

.bg-grey-1 {
  background-color: #f5f5f5;
}

.shadow-2 {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}

.text-dark {
  color: #333;
}

/* Dodatno za ružičastu boju gumba */
.bg-red-2 {
  background-color: #fce4ec;
}

.text-white {
  color: white !important;
}
</style>
