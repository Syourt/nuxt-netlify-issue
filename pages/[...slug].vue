<template>
  <div>
    <NuxtLink to="/">Back Home</NuxtLink>
    <h1>This page should contain some content</h1>
  </div>
  <div>
    <ContentRenderer v-if="page" :value="page" />
  </div>
</template>

<script setup>
const route = useRoute();

const { data: page } = await useAsyncData(route.path, () => {
  return queryCollection('content').path(route.path).first();
});
</script>
