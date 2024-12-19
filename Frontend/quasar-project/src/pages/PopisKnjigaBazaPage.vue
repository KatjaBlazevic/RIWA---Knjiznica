<template>
  <q-page padding>
    <div class="q-pa-md">
      <q-card bordered class="bg-grey-1 shadow-2">
        <q-card-section>
          <h1 class="text-center">Popis knjiga</h1>
        </q-card-section>

        <q-card-section>
          <q-table
            :rows="books"
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
                  <!-- Render regular fields -->
                  <span v-if="col.name !== 'slika' && col.name !== 'opis'">
                    {{ col.value }}
                  </span>

                  <!-- Render opis field -->
                  <div v-if="col.name === 'opis'" class="truncate max-w-200">
                    {{ props.row.opis }}
                  </div>

                  <!-- Render slika field -->
                  <q-img
                    :src="props.row.slika"
                    v-if="col.name === 'slika'"
                    size="75px"
                    class="rounded-borders shadow-2"
                    style="max-height: 75px"
                  />
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
    name: "id",
    label: "ID",
    field: "id",
    align: "left",
    sortable: true,
  },
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
  },
  {
    name: "opis",
    label: "Opis",
    field: "opis",
    align: "left",
  },
  {
    name: "slika",
    label: "Slika",
    field: "slika",
    align: "center",
  },
  {
    name: "stanje",
    label: "Stanje",
    field: "stanje",
    align: "center",
  },
];

export default {
  setup() {
    const books = ref([]);
    const pagination = ref({
      rowsPerPage: 10,
    });

    const loadBooks = async () => {
      try {
        const response = await axios.get("http://localhost:3000/api/knjiga");
        books.value = response.data || [];
      } catch (error) {
        console.error("Greška pri učitavanju knjiga:", error);
      }
    };

    // Load books when the component is mounted
    loadBooks();

    return {
      columns,
      books,
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

.truncate {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.max-w-200 {
  max-width: 200px;
}

.rounded-borders {
  border-radius: 8px;
}

.shadow-2 {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}
</style>
