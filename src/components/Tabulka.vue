<template>
  <table>
    <thead>
      <tr class="popis">
        <th :key="sloupec.key" v-for="sloupec in obsah.sloupce">{{ sloupec.nazev }}</th>
      </tr>
    </thead>
    <tbody>
      <tr :key="radek.id" v-for="radek in obsah.radky">
        <Radek @zmenit-radek="zmenitRadek" @smazat-radek="smazatRadek" :radek="radek" :sloupce="obsah.sloupce" />
      </tr>
    </tbody>
  </table>
  <div class="additem">
    <form @submit="pridatRadek" class="add-form">
      <input type="text" :name="[sloupec.key]" v-model="obsahPridavani[sloupec.key]" :key="sloupec.key" v-for="sloupec in obsah.sloupce.filter((sloupec) => sloupec.key != 'id')" :placeholder="[sloupec.nazev]" />
      <IconButton type="submit" icon="plus-square" color="green" />
    </form>
  </div>
</template>

<script>
import Radek from "./Radek";
import IconButton from "./IconButton";

export default {
  name: "Tabulka",
  components: {
    Radek,
    IconButton,
  },
  data() {
    return {
      obsah: {},
      obsahPridavani: {},
    };
  },
  methods: {
    pridatRadek(e) {
      e.preventDefault();
      let novyRadek;
      if (this.obsah.radky.length > 0) {
        novyRadek = {
          id: this.obsah.radky[this.obsah.radky.length - 1].id + 1,
        };
      } else {
        novyRadek = {
          id: 1,
        };
      }
      for (let i = 1; i < this.obsah.sloupce.length; i++) {
        const sloupecKey = this.obsah.sloupce[i].key;
        novyRadek[sloupecKey] = this.obsahPridavani[sloupecKey];
      }
      this.obsahPridavani = {};
      this.obsah.radky = [...this.obsah.radky, novyRadek];
    },
    zmenitRadek(id) {
      for (let i = 1; i < this.obsah.sloupce.length; i++) {
        let sloupec = this.obsah.sloupce[i];
        let novaHodnota = prompt("Zadejte novou hodnotu pro sloupec " + sloupec.nazev + " na řádku s ID " + id);
        let staryRadek = {};
        for (let i = 0; i < this.obsah.radky.length; i++) {
          const element = this.obsah.radky[i];
          if (element.id == id) {
            staryRadek = element;
          }
        }
        let novyRadek = {};
        for (let i = 0; i < this.obsah.sloupce.length; i++) {
          const element = this.obsah.sloupce[i];
          if (element.key == sloupec.key) {
            novyRadek[element.key] = novaHodnota;
          } else {
            novyRadek[element.key] = staryRadek[element.key];
          }
        }
        this.obsah.radky = this.obsah.radky.map((radek) => (radek.id === id ? novyRadek : radek));
      }
    },
    smazatRadek(id) {
      this.obsah.radky = this.obsah.radky.filter((radek) => radek.id !== id);
    },
  },
  created() {
    this.obsah = {
      radky: [
        {
          id: 1,
          jmeno: "Jaroslav",
          prijmeni: "Čekal",
        },
        {
          id: 2,
          jmeno: "Josef",
          prijmeni: "Marek",
        },
        {
          id: 3,
          jmeno: "Pavel",
          prijmeni: "Dočkal",
        },
      ],
      sloupce: [
        {
          key: "id",
          nazev: "ID",
        },
        {
          key: "jmeno",
          nazev: "Jméno",
        },
        {
          key: "prijmeni",
          nazev: "Příjmení",
        },
      ],
    };
  },
};
</script>

<style scoped>
table,
thead,
tbody,
tr {
  width: 100%;
}

.popis {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  margin-bottom: 0.5rem;
}

.popis th {
  font-size: 1.5rem;
  font-weight: 700;
  display: inline-block;
  margin-right: 0.5rem;
}

form {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  justify-content: flex-start;
}

form input {
  padding: 0.7rem;
  font-size: 18px;
  border-radius: 0.5rem;
  border: 1px solid black;
  outline: none;
  margin-bottom: 0.5rem;
}

form button {
  align-self: flex-end;
}
</style>
