<script lang="ts" setup>
import type Article from '~/types/api'

const router = useRouter()
const route = useRoute()

const { data: articles, status: articlesStatus } = await useFetch<Article[]>(
  'https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/'
)

const articlesPerPage = ref(8)
const pageAmount = computed(() =>
  articles.value ? Math.ceil(articles.value.length / articlesPerPage.value) : 0
)
const currentPage = ref(
  route.query.page
    ? parseInt(`${route.query.page}`) <= pageAmount.value
      ? parseInt(`${route.query.page}`)
      : 1
    : 1
)

const pagedArticlesArray = computed(() =>
  articles.value?.slice(
    (currentPage.value - 1) * articlesPerPage.value,
    currentPage.value * articlesPerPage.value
  )
)

const defaultLeftVisiblePageButton = computed(() =>
  currentPage.value > 2
    ? currentPage.value < pageAmount.value - 2
      ? currentPage.value - 1
      : pageAmount.value - 4
    : 1
)
const leftVisiblePageButton = ref(defaultLeftVisiblePageButton.value)

watch(currentPage, (newValue) => {
  leftVisiblePageButton.value = defaultLeftVisiblePageButton.value
  router.push({ query: { ...route.query, page: newValue } })
})
</script>

<template>
  <main class="articles">
    <h1 class="articles__title">Articles</h1>
    <template v-if="articlesStatus === 'success'">
      <div class="articles__list">
        <NuxtLink
          v-for="article in pagedArticlesArray"
          :key="article.id"
          :to="'/' + article.id"
          class="articles__article article"
        >
          <img
            class="article__image"
            :src="'https://placedog.net/640/480?id=' + article.id"
            :alt="article.title"
          />
          <p class="article__title">{{ capitalize(article.preview) }}</p>
          <p class="article__text">Read more</p>
        </NuxtLink>
      </div>
      <div class="articles__pagination pagination">
        <button
          v-if="leftVisiblePageButton > 1"
          class="pagination__button pagination__arrow-button"
          @click="leftVisiblePageButton -= 1"
        >
          <img
            class="pagination__arrow pagination__arrow_reverse"
            src="/img/pagination-arrow.svg"
            alt="Pagination arrow"
          />
        </button>
        <button
          v-for="(n, index) in leftVisiblePageButton > 1 && leftVisiblePageButton < pageAmount - 4
            ? 4
            : 5"
          :key="leftVisiblePageButton + index"
          class="pagination__button"
          :class="{ pagination__button_active: leftVisiblePageButton + index === currentPage }"
          @click="currentPage = leftVisiblePageButton + index"
        >
          {{ leftVisiblePageButton + index }}
        </button>
        <button
          v-if="leftVisiblePageButton < pageAmount - 4"
          class="pagination__button pagination__arrow-button"
          @click="leftVisiblePageButton += 1"
        >
          <img class="pagination__arrow" src="/img/pagination-arrow.svg" alt="Pagination arrow" />
        </button>
      </div>
    </template>
    <template v-else-if="articlesStatus === 'pending'">
      <Loader class="articles__loader" />
    </template>
    <template v-else>
      <p class="articles__error">Unfortunately, an error occurred when uploading the articles</p>
    </template>
  </main>
</template>

<style lang="scss" scoped>
.articles {
  max-width: 1217px;
  margin: 120px auto 140px;

  &__title {
    font-size: 84px;
  }

  &__list {
    display: flex;
    column-gap: 32px;
    row-gap: 40px;
    flex-wrap: wrap;
    margin-top: 59px;
    margin-bottom: 50px;
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

.article {
  width: 280px;
  cursor: pointer;
  overflow: hidden;
  position: relative;
  transition: transform 0.4s ease-out;

  &__image {
    width: 280px;
    height: 280px;
    object-fit: cover;
    object-position: center;
  }

  &__title {
    margin-top: 24px;
    font-size: 20px;
    line-height: 120%;

    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  &__text {
    position: absolute;
    bottom: 0;
    left: 0;
    padding-top: 12px;
    font-size: 20px;
    color: $primary-color;
    transform: translateY(100%);
    transition: transform 0.4s ease-out;
  }

  &:hover {
    transform: translateY(-20px);
    overflow: visible;
  }
}

.pagination {
  display: flex;
  gap: 8px;

  &__button {
    width: 44px;
    height: 44px;
    border-radius: 12px;
    background-color: $button-color;

    display: flex;
    justify-content: center;
    align-items: center;

    &:hover {
      background-color: $hover-color;
    }

    &_active {
      background-color: $text-color;
      color: $background-color;

      &:hover {
        background-color: $text-color;
      }
    }
  }

  &__arrow-button {
    background-color: $background-color;
    border: 1px solid $hover-color;
  }

  &__arrow {
    &_reverse {
      transform: scaleX(-1);
    }
  }
}
</style>
