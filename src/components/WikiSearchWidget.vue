<template>
  <div>

    <WikiSearchResponse
        :searchResponse="searchResponse"
    />

    <div class="searchbox">
      <form @submit.prevent="searchWiki()">
        <input v-model="query" type="text" placeholder="Search for pages containing [x]…">
      </form>
    </div>
  </div>
</template>

<script>
import WikiSearchResponse from "@/components/WikiSearchResponse";

export default {
  name: "WikiSearchWidget",
  data() {
    return {
      query: "",
      searchResponse: [],
    }
  },
  methods: {
    searchWiki() {
      let encodedQuery = encodeURIComponent(this.query)
      let endpoint = `https://en.wikipedia.org/w/rest.php/v1/search/title?q=${encodedQuery}&limit=10`

      fetch(endpoint)
        .then(response => response.json())
        .then(data => this.searchResponse = data.pages)
        .catch(error => {
          this.searchResponse = []
          console.error('Error:', error);
        })
    },
  },
  components: {
    WikiSearchResponse,
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
