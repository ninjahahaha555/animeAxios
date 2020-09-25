<template>
  <div class="'row text-light">
    <div class="col-sm"></div>

    <div class="col-sm">
      <input type="text" v-model="textSearch" placeholder="ค้นหาการ์ตูน" />
      <b-button @click="searchData()" variant="danger">Search Anime</b-button
      ><br /><br />
      <b-card-group columns>
        <b-card
          v-for="data in animeData.slice(
            (currentPage - 1) * perPage,
            (currentPage - 1) * perPage + perPage
          )"
          :key="data.mal_id"
          style="width: 450px"
          class="mb-3"
        >
          <b-row>
            <b-col md="4">
              <a :href="data.url">
                <b-card-img :src="data.image_url"></b-card-img>
              </a>
              Episode : {{ data.episodes }}
            </b-col>
            <b-col md="8">
              <b-card-body :title="data.title">
                <b-card-text>{{ data.synopsis }}</b-card-text>
              </b-card-body>
            </b-col>
          </b-row>
        </b-card>
      </b-card-group>

      <div v-if="run == true">
        <b-pagination
          v-model="currentPage"
          :total-rows="animeData.length"
          :per-page="perPage"
          first-text="First"
          prev-text="Prev"
          next-text="Next"
          last-text="Last"
        ></b-pagination>
      </div>
    </div>

    <div class="col-sm"></div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      animeData: "",
      textSearch: "",
      perPage: 9,
      currentPage: 1,
      run: false,
    };
  },
  methods: {
    searchData() {
      axios
        .get("https://api.jikan.moe/v3/search/anime?q=" + this.textSearch + "")
        .then((response) => {
          (this.animeData = response.data.results), (this.run = true);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>
.card {
  background-color: slategrey;
}
.pagination {
  justify-content: center;
}
</style>