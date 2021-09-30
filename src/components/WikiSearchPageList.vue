<template>
  <div class="page-list">
    <div v-for="page in pages" :key="page.id">
      <div :id="page.id" class="page">

        <img v-if="page.thumbnail" class="page-thumbnail" :alt="page.title" :src="page.thumbnail.url">
        <img v-else class="page-thumbnail" :alt="page.title" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAQAAAAAYLlVAAAAPElEQVR42u3OMQEAAAgDINfc5hpjDyQge1MVAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBgXbgAQzcYAEuE5tqAAAAAElFTkSuQmCC">

        <div class="page-info">
          <a :href="pageUrl(page.key)" target="_blank">
            <div class="page-title">{{page.title}}</div>
          </a>
          <div class="page-description">{{page.description}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WikiSearchPageList",
  props: {
    pages: Array,
  },
  methods: {
    pageUrl(key) {
      let uriEncodedPageKey = encodeURIComponent(key)
      return `https://en.wikipedia.org/wiki/${uriEncodedPageKey}`
    },
  },
}
</script>

<style scoped>
a {
  text-decoration: none;
  color: #2c3e50;
}

.page-list {
  border: darkgray 1px solid;
  border-bottom: none;
}

.page {
  display: flex;
  align-items: flex-start;
  padding: 5px;
  min-height: 4rem;
  border-bottom: darkgray 1px solid;
}

.page-thumbnail {
  width: 64px;
  height: 64px;
  margin-right: 5px;
}

.page-info {
  flex: 1;
}

.page-title {
  line-height: 1;
  font-size: large;
  font-weight: bolder;
  margin-bottom: 5px;
}
</style>
