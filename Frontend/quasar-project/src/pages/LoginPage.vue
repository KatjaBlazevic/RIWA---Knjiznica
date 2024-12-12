<template>
  <q-page padding class="flex flex-center bg-grey-1">
    <q-card flat bordered class="q-pa-lg login-card">
      <q-card-section class="text-center">
        <h1 class="text-center">Prijava</h1>
        <p class="text-dark">Unesite svoje korisničke podatke za prijavu.</p>
      </q-card-section>

      <q-card-section>
        <q-input
          v-model="username"
          label="Korisničko ime"
          outlined
          dense
          class="q-mb-md text-dark"
        />
        <q-input
          v-model="password"
          label="Lozinka"
          type="password"
          outlined
          dense
          class="q-mb-md text-dark"
        />
      </q-card-section>

      <q-card-actions align="center">
        <q-btn
          label="Potvrdi"
          color="primary"
          unelevated
          @click="loginUser"
          class="full-width text-dark"
        />
      </q-card-actions>
    </q-card>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: ''
    };
  },
  methods: {
    loginUser() {
      if (this.username && this.password) {
        console.log("Podaci za prijavu:", this.username, this.password);

        this.username = '';
        this.password = '';

        this.$router.push({ name: 'PopisKnjigaPage' });
      } else {
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
  font-size: 2.5em;
  font-weight: bold;
  text-transform: uppercase;
  color: #151629;
}
.login-card {
  max-width: 400px;
  width: 100%;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.full-width {
  width: 100%;
}

.text-dark {
  color: black !important;
}
</style>
