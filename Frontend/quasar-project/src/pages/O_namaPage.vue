<template>
  <q-page padding>
    <!-- content -->
    <q-card dark bordered class="my-card bg-light-pink shadow-2">
      <q-card-section>
        <q-img
          src="https://www.rijeka.hr/wp-content/uploads/2023/12/Nova-knjižnica-4-901x600.jpg"
          class="q-img-full"
        />
      </q-card-section>

      <q-card-section class="text-h3 text-center text-weight-bolder q-mb-md text-title">
        <strong>O nama</strong> <!-- Bold naslov -->
      </q-card-section>

      <q-card-section class="text-h4 text-justify text-grey-1 q-pa-md">
        <strong>{{ o_nama }}</strong> <!-- Bold tekst -->
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const o_nama = ref(
      'Gradska knjižnica Rijeka središnja je narodna knjižnica grada Rijeke i matična knjižnica za narodne i školske knjižnice Primorsko-goranske županije. Ona je informacijsko, obrazovno, kulturno, komunikacijsko i socijalno središte Rijeke i okolice usmjereno prema novom stvaralaštvu, održivom razvoju i kvaliteti razvoja zajednice i čitateljske kulture.'
    );

    return {
      o_nama
    };
  }
};
</script>

<style scoped>
.my-card {
  width: 100%;
  max-width: 900px;
  margin: auto;
  border-radius: 20px;
  overflow: hidden;
  background-color: #a07e89;
}

.q-img-full {
  width: 100%;
  height: 350px;
  object-fit: cover;
}

.text-title {
  color: white;
}

.text-grey-1 {
  color: #e0e0e0;
}

.q-card-section {
  padding: 20px;
}

.text-h3 {
  font-size: 2.5em;
  font-weight: bold;
  text-transform: uppercase;
  color: #ffffff;
}

.text-h4 {
  font-size: 1.25rem;
  font-weight: 400;
  color: #666;
}

.q-mb-md {
  margin-bottom: 15px;
}
</style>
