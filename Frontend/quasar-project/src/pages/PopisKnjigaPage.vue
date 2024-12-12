<template>
  <q-page padding>
    <h1 class="text-center">Popis Knjiga</h1>
    <p>Ovdje možete pronaći popis svih knjiga u našoj knjižnici.</p>
    <q-table
      :rows="books"
      :columns="columns"
      row-key="id"
    />
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      books: [
        {
          id: 1,
          naslov: 'Kraljica tame',
          autor: 'Sarah J. Maas',
          opis: 'Fantastični roman u kojem se prati Feyre, mlada žena koja postaje zarobljenica u zemlji Faeyre kako bi spasila svoju obitelj.',
          stanje: 5
        },
        {
          id: 2,
          naslov: 'Nešto strašno',
          autor: 'Colleen Hoover',
          opis: 'Romantična drama o složenim odnosima između dvije osobe, koje se suočavaju s emocionalnim traumama iz prošlosti.',
          stanje: 3
        },
        {
          id: 3,
          naslov: 'Dvorac od karata',
          autor: 'Sarah J. Maas',
          opis: 'U ovom napetom fantasy romanu, Celaena Sardothien je najbolja ubojica koja postaje šampionica kralja, ali s temnim tajnama koje prijete svemu što voli.',
          stanje: 4
        },
        {
          id: 4,
          naslov: 'It Ends with Us',
          autor: 'Colleen Hoover',
          opis: 'Roman o ljubavi, gubitku i teškim odlukama koje donosimo u životu, i snazi žene koja mora izabrati između prošlosti i budućnosti.',
          stanje: 6
        },
        {
          id: 5,
          naslov: 'A Court of Thorns and Roses',
          autor: 'Sarah J. Maas',
          opis: 'Feyre se nađe u zemlji Faeyre, prepunoj magije i opasnosti, gdje je prisiljena da surađuje s faeyre koji je zarobljeni princ.',
          stanje: 7
        },
        {
          id: 6,
          naslov: 'Verity',
          autor: 'Colleen Hoover',
          opis: 'Psihološki triler o autorici koja se suočava s misterioznim, mračnim tajnama prošlosti koja prijeti njezinoj karijeri i životu.',
          stanje: 8
        },
        {
          id: 7,
          naslov: 'Throne of Glass',
          autor: 'Sarah J. Maas',
          opis: 'Knjiga koja slijedi priču o Celaeni, mladoj ženi koja se bori za svoju slobodu i osvetu, dok se bori u smrtonosnim bitkama i rješava misterije.' ,
          stanje: 5
        },
        {
          id: 8,
          naslov: 'Ugly Love',
          autor: 'Colleen Hoover',
          opis: 'Strastvena i emotivna priča o dvoje ljudi koji se bore s prošlošću i neizbježnim osjećajima prema drugima.',
          stanje: 4
        }
      ],
      columns: [
        { name: 'id', label: 'ID', field: 'id', align: 'left' },
        { name: 'naslov', label: 'Naslov', field: 'naslov', align: 'left' },
        { name: 'autor', label: 'Autor', field: 'autor', align: 'left' },
        { name: 'opis', label: 'Opis', field: 'opis', align: 'left' },
        { name: 'stanje', label: 'Stanje', field: 'stanje', align: 'left' }
      ]
    };
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
</style>