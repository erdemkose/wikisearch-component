<template>
  <div>

    <WikiSearchPageList :pages="pages"/>

    <div class="searchbox">
      <form @submit.prevent="searchWiki()">
        <input v-model="query" type="text" placeholder="Search for pages containing [x]…">
      </form>
    </div>
  </div>
</template>

<script>
import WikiSearchPageList from "@/components/WikiSearchPageList";

export default {
  name: "WikiSearchWidget",
  data() {
    return {
      query: "",
      pages: [],
    }
  },
  methods: {
    searchWiki() {
      let encodedQuery = encodeURIComponent(this.query)
      let endpoint = `https://en.wikipedia.org/w/rest.php/v1/search/title?q=${encodedQuery}&limit=10`

      fetch(endpoint)
        .then(response => response.json())
        .then(data => this.pages = data.pages)
        .catch(error => {
          this.pages = []
          console.error('Error:', error);
        })
    },
  },
  components: {
    WikiSearchPageList,
  },
}
</script>

<style scoped>
.searchbox {
  padding: 5px;
  border: darkgray 1px solid;
  border-top: none;
}
.searchbox input {
  border: none;
  outline: none;
  width: 100%;
}
</style>
