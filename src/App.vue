<template>
  <CountryCatalogue
    v-if="tableData"
    :data="tableData"
    :config="config"
  ></CountryCatalogue>
</template>

<script>
import CountryCatalogue from "./components/CountryCatalogue.vue";

export default {
  name: "App",
  components: {
    CountryCatalogue,
  },
  data: () => ({
    tableData: undefined,
    config: [
      {
        key: "flag",
        title: "國旗",
        type: "img",
      },
      {
        key: "name",
        title: "國家名稱",
        type: "text",
      },
      {
        key: "alpha2Code",
        title: "2位國家代碼",
        type: "text",
      },
      {
        key: "alpha3Code",
        title: "3位國家代碼",
        type: "text",
      },
      {
        key: "nativeName",
        title: "母語名稱",
        type: "text",
      },
      {
        key: "altSpellings",
        title: "替代國家名稱",
        type: "list",
      },
      {
        key: "callingCodes",
        title: "國際電話區號",
        type: "textArray",
      },
    ],
  }),
  mounted() {
    this.axios.get("https://restcountries.com/v2/all").then((response) => {
      console.log(response.data.length);
      this.tableData = response.data;
      console.log(response);
    });
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
