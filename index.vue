<script src="https://cdnjs.cloudflare.com/ajax/libs/axios/1.5.1/axios.min.js" integrity="sha512-emSwuKiMyYedRwflbZB2ghzX8Cw8fmNVgZ6yQNNXXagFzFOaQmbvQ1vmDkddHjm5AITcBIZfC7k4ShQSjgPAmQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>

<script>
// Importa Axios nel tuo componente
import axios from "axios";

export default {
  data() {
    return {
      dischi: [],
    };
  },
  mounted() {
    axios
      .get("index.php")
      .then((response) => {
        this.dischi = response.data.dischi;
      })
      .catch((error) => {
        console.error("Errore nella richiesta HTTP:", error);
      });
  },
};
</script>

<template>
  <div>
    <ul>
      <li v-for="disco in dischi" :key="disco.nome">
        <img :src="disco.path_immagine" alt="Copertina" />
        <p>Nome del disco: {{ disco.nome }}</p>
        <p>Autore: {{ disco.autore }}</p>
        <p>Data di pubblicazione: {{ disco.data_di_pubblicazione }}</p>
      </li>
    </ul>
  </div>
</template>
