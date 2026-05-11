<script lang="ts" setup>
import type Article from '~/types/api'

const route = useRoute()
const articleId = computed(() => route.params.id)

const {
  data: article,
  status: articleStatus,
  error: articleError
} = await useFetch<Article>(
  `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${articleId.value}`
)
</script>

<template>
  <main class="article">
    <template v-if="articleStatus === 'success' && article">
      <h1 class="article__title">{{ capitalize(article.preview) }}</h1>
      <img
        class="article__image"
        :src="'https://picsum.photos/seed/' + article.id + '/640/480'"
        alt="article.title"
      />
      <p class="article__subtitle">About</p>
      <p class="article__text">{{ article.description }}</p>
    </template>
    <template v-else-if="articleStatus === 'pending'">
      <Loader class="article__loader" />
    </template>
    <template v-else>
      <p v-if="articleError?.status === 404" class="article__error">
        Unfortunately, there is no article with this id
      </p>
      <p v-else class="article__error">
        Unfortunately, an error occurred when uploading the articles
      </p>
    </template>
  </main>
</template>

<style lang="scss" scoped>
.article {
  max-width: 1217px;
  margin: 120px auto 80px;

  &__title {
    font-size: 84px;
  }

  &__image {
    width: 100%;
    height: 700px;
    object-fit: cover;
    object-position: center;
    margin-top: 73px;
    margin-bottom: 80px;
  }

  &__subtitle {
    font-size: 16px;
    margin-bottom: 32px;
  }

  &__text {
    font-size: 36px;
    line-height: 124%;
    width: 695px;
  }

  &__loader {
    margin: 59px auto 0;
  }

  &__error {
    margin-top: 59px;
    font-size: 52px;
    text-align: center;
  }
}
</style>
