<template>
  <q-page padding>
    <h1 class="text-center text-h4 q-mb-md">Registracija</h1>
    <p class="text-center q-mb-md">Ispunite donja polja kako biste se registrirali.</p>

    <div class="q-gutter-md">
      <q-input
        v-model="userData.username"
        label="Korisničko ime"
        outlined
        dense
        autofocus
        :rules="[val => !!val || 'Unesite korisničko ime']"
        class="q-mb-md"
      />
      <q-input
        v-model="userData.email"
        label="Email"
        type="email"
        outlined
        dense
        :rules="[val => !!val || 'Unesite email']"
        class="q-mb-md"
      />
      <q-input
        v-model="userData.password"
        label="Lozinka"
        type="password"
        outlined
        dense
        :rules="[val => !!val || 'Unesite lozinku']"
        class="q-mb-md"
      />
      <q-input
        v-model="userData.confirmPassword"
        label="Potvrdi lozinku"
        type="password"
        outlined
        dense
        :rules="[val => val === userData.password || 'Lozinke se moraju podudarati']"
        class="q-mb-md"
      />

      <q-btn
        label="Potvrdi"
        @click="registerUser"
        color="primary"
        class="full-width q-mb-md"
        size="large"
        :disable="!isFormValid"
      />
    </div>

    <!-- Prikaz poruke zahvale ako je registracija uspješna -->
    <div v-if="registrationSuccess" class="text-positive text-h6 text-center q-mt-md">
      Hvala vam na vašoj registraciji!
    </div>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      userData: {
        username: '',
        email: '',
        password: '',
        confirmPassword: ''
      },
      registrationSuccess: false, // Praćenje statusa registracije
    };
  },
  computed: {
    isFormValid() {
      return (
        this.userData.username &&
        this.userData.email &&
        this.userData.password &&
        this.userData.password === this.userData.confirmPassword
      );
    }
  },
  methods: {
    registerUser() {
      if (this.isFormValid) {
        this.registrationSuccess = true;

        // Očisti polja nakon registracije
        this.userData = {
          username: '',
          email: '',
          password: '',
          confirmPassword: ''
        };
      } else {
        alert("Provjerite unesene podatke.");
      }
    }
  }
};
</script>

<style scoped>
.q-page {
  max-width: 400px;
  margin: 0 auto;
}

.text-center {
  text-align: center;
}

.q-btn {
  margin-top: 16px;
}
</style>
