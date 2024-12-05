<template>
  <q-page padding>
    <h1>Popis Knjiga</h1>
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
        },
        // Dodane knjige
        {
          id: 9,
          naslov: 'Ponos i predrasude',
          autor: 'Jane Austen',
          opis: 'Roman koji istražuje društvene običaje i složenost ljubavi kroz priču o Elizabeth Bennet i gospodinu Darcyju.',
          stanje: 5
        },
        {
          id: 10,
          naslov: '1984',
          autor: 'George Orwell',
          opis: 'Distopijski roman o totalitarnom društvu i borbi pojedinca za slobodu misli i izražavanja.',
          stanje: 4
        },
        {
          id: 11,
          naslov: 'Lovac u žitu',
          autor: 'J.D. Salinger',
          opis: 'Roman o adolescentskom otuđenju i potrazi za smislom kroz priču o Holden Caulfieldu.',
          stanje: 6
        },
        {
          id: 12,
          naslov: 'Ana Karenjina',
          autor: 'Lav Tolstoj',
          opis: 'Priča o ljubavi, društvu i obiteljskim dilemama kroz tragičnu sudbinu Ane Karenjine.',
          stanje: 3
        },
        {
          id: 13,
          naslov: 'Veliki Gatsby',
          autor: 'F. Scott Fitzgerald',
          opis: 'Priča o luksuzu, ljubavi i društvenim ambicijama u 1920-im kroz lik Jaya Gatsbyja.',
          stanje: 7
        },
        {
          id: 14,
          naslov: 'Mali princ',
          autor: 'Antoine de Saint-Exupéry',
          opis: 'Filozofska pripovijetka o malom princu i njegovim putovanjima kroz svjetove, tražeći prijateljstvo i ljubav.',
          stanje: 8
        },
        {
          id: 15,
          naslov: 'Sto godina samoće',
          autor: 'Gabriel García Márquez',
          opis: 'Ep o obitelji Buendía u mitskom mjestu Macondo, koji prati generacije obitelji kroz ljubav, ratove i magijski realizam.',
          stanje: 5
        },
        {
          id: 16,
          naslov: 'Zločin i kazna',
          autor: 'Fjodor Dostojevski',
          opis: 'Roman o moralnoj dilemi i psihološkoj borbi čovjeka koji se suočava sa svojim zločinom i posljedicama.',
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
