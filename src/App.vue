<script>
import { RouterLink, RouterView } from "vue-router";
import axios from "axios";
import { ref } from "vue";

export default {
  setup() {
    const covid = ref("");

    // const load = async () => {
    //   try {
    //     const response = await axios.get(
    //       "https://yummly2.p.rapidapi.com/feeds/list/"
    //     );
    //     quote.value = response.data.quote;
    //   } catch (err) {
    //     console.log(err);
    //   }
    // };

    // load();

    // const load = async () => {
    //   try {
    //     const options = {
    //       method: "GET",
    //       headers: {
    //         "X-RapidAPI-Key":
    //           "7e17b4541cmshe095df1f9ca212fp13dfedjsn53491f70a14f",
    //         "X-RapidAPI-Host": "yummly2.p.rapidapi.com",
    //       },
    //     };
    //     let data = await fetch(
    //       "https://yummly2.p.rapidapi.com/feeds/list?limit=24&start=0",
    //       options
    //     );
    //     if (!data.ok) {
    //       throw Error("Data not found");
    //     }
    //     recipe.value = await data.title;
    //   } catch (err) {
    //     console.log(err);
    //   }
    // };

    // const options = {
    //   method: "GET",
    //   url: "https://yummly2.p.rapidapi.com/feeds/auto-complete",
    //   params: { q: "chicken soup" },
    //   headers: {
    //     "X-RapidAPI-Key": "7e17b4541cmshe095df1f9ca212fp13dfedjsn53491f70a14f",
    //     "X-RapidAPI-Host": "yummly2.p.rapidapi.com",
    //   },
    // };

    // axios
    //   .request(options)
    //   .then(function (response) {
    //     console.log(response.data);
    //     recipe.value = response.data.searches;
    //   })
    //   .catch(function (error) {
    //     console.error(error);
    //   });

    // const options = {
    //   method: "GET",
    //   url: "https://coronavirus-smartable.p.rapidapi.com/stats/v1/US/",
    //   headers: {
    //     "X-RapidAPI-Key": "7e17b4541cmshe095df1f9ca212fp13dfedjsn53491f70a14f",
    //     "X-RapidAPI-Host": "coronavirus-smartable.p.rapidapi.com",
    //   },
    // };

    // axios
    //   .request(options)
    //   .then(function (response) {
    //     console.log(response.data);
    //     covid.value = response.data.stats;
    //   })
    //   .catch(function (error) {
    //     console.error(error);
    //   });

    const options = {
      method: "GET",
      headers: {
        "X-RapidAPI-Key": "7e17b4541cmshe095df1f9ca212fp13dfedjsn53491f70a14f",
        "X-RapidAPI-Host": "coronavirus-smartable.p.rapidapi.com",
        "Content-Type": "application/json",
      },
    };

    fetch("https://coronavirus-smartable.p.rapidapi.com/stats/v1/US/", options)
      .then((response) => response.json())
      .then((response) => ((covid.value = response), console.log(response)))
      .catch((err) => console.error(err));

    return { covid };
  },
};
</script>

<template>
  <nav>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink>
  </nav>
  <div>
    <i>{{ covid }}</i>
  </div>

  <RouterView />
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}
</style>
