<script lang="ts" setup>
const route = useRoute()

const articleId = computed(() => route.params.id)
</script>

<template>
  <div>
    {{ articleId }}
  </div>
</template>

<style scoped></style>
