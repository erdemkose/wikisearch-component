<template>
  <div class="pages">
    <div v-for="responseItem in searchResponse" v-bind:key="responseItem.id">
      <WikiSearchResponseItem
          :item="responseItem"
      />
    </div>
  </div>
</template>

<script>
import WikiSearchResponseItem from "@/components/WikiSearchResponseItem";

export default {
  name: "WikiSearchResponse",
  props: {
    searchResponse: Array,
  },
  components: {
    WikiSearchResponseItem,
  },
}
</script>

<style scoped>

.pages {
  border: darkgray 1px solid;
  border-bottom: none;
}

</style>
