<template>
  <q-page padding>
    <div class="q-pa-md">
      <q-card bordered class="bg-grey-1 shadow-2">
        <q-card-section>
          <h1 class="text-center">Popis rezerviranih knjiga</h1>
        </q-card-section>

        <q-card-section>
          <q-table
            :rows="reservations"
            :columns="columns"
            row-key="id"
            separator="horizontal"
            table-class="bg-white text-black"
            bordered
            flat
            square
            dense
            :pagination="pagination"
          >
            <template v-slot:header="props">
              <q-tr :props="props" class="bg-red-2 text-white">
                <q-th
                  v-for="col in props.cols"
                  :key="col.name"
                  :props="props"
                  class="text-left text-bold"
                >
                  {{ col.label }}
                </q-th>
              </q-tr>
            </template>

            <template v-slot:body="props">
              <q-tr :props="props" class="hover-row">
                <q-td v-for="col in props.cols" :key="col.name" :props="props">
                  <span>
                    {{ col.value }}
                  </span>
                </q-td>
              </q-tr>
            </template>
          </q-table>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";
import axios from "axios";

const columns = [
  {
    name: "naslov",
    label: "Naslov",
    field: "naslov",
    align: "left",
    sortable: true,
  },
  {
    name: "autor",
    label: "Autor",
    field: "autor",
    align: "left",
    sortable: true,
  },
  {
    name: "korisnik",
    label: "Korisnik",
    field: "korisnik",
    align: "left",
    sortable: true,
  },
  {
    name: "datum_rezervacije",
    label: "Datum rezervacije",
    field: "datum_rezervacije",
    align: "center",
    sortable: true,
  },
];

export default {
  setup() {
    const reservations = ref([]);
    const pagination = ref({
      rowsPerPage: 10,
    });

    const loadReservations = async () => {
      try {
        const response = await axios.get(
          "http://localhost:3000/api/rezervacija"
        );
        reservations.value = response.data || [];
      } catch (error) {
        console.error("Greška pri učitavanju rezervacija:", error);
      }
    };

    // Load reservations when the component is mounted
    loadReservations();

    return {
      columns,
      reservations,
      pagination,
    };
  },
};
</script>

<style scoped>
.text-bold {
  font-weight: bold;
}

.text-center {
  text-align: center;
}

.bg-grey-1 {
  background-color: #f5f5f5;
}

h1 {
  font-size: 2.5em;
  font-weight: bold;
  text-transform: uppercase;
  color: #4a4a4a;
}

.bg-red-2 {
  background-color: #9aecef;
}

.hover-row:hover {
  background-color: #fce4ec;
}

.shadow-2 {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}
</style>
