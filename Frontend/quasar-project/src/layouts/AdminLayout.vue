<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="custom-header">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title class="text-center-h1 custom-title">Knjižnica (admin)</q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label header>
          Essential Links
        </q-item-label>

        <q-item
          v-for="link in linksList"
          :key="link.title"
          clickable
          @click="navigateTo(link.link)"
        >
          <q-item-section avatar>
            <q-icon :name="link.icon" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ link.title }}</q-item-label>
            <q-item-label caption>{{ link.caption }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

defineOptions({
  name: 'AdminLayout'
});

const linksList = [
  { title: 'Početna', caption: 'Početna stranica', icon: 'home', link: '/admin' },
  { title: 'Popis knjiga', caption: 'Popis svih knjiga u knjižnici', icon: 'book', link: '/admin/popisKnjiga' },
  { title: 'Pretraživanje', caption: 'Tražiš knjigu?', icon: 'search', link: '/admin/Pretrazivanje' },
  { title: 'Rezervirane knjige', caption: 'Rezervacija knjige', icon: 'book', link: '/admin/Rezervacija' },
  { title: 'Popis korisnika', caption: 'Popis korisnika', icon: 'favorite', link: '/admin/PopisKorisnika' },
  { title: 'Unos knjiga', caption: 'Unos nove knjige', icon: 'local_library', link: '/admin/UnosKnjiga' },
  { title: 'Logout', caption: 'Logout', icon: 'login', link: '/admin/Logout' }
]

const leftDrawerOpen = ref(false)
const router = useRouter()

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}

function navigateTo(route) {
  router.push(route)
}
</script>

<style>
.custom-header {
  background-color: #fce4ec;
  color: white;
}

.custom-title {
  font-weight: bold;
  font-size: 2.5em;
  text-transform: uppercase;
  color: #ffffff;
}
</style>
