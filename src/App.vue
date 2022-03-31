<template>
  <div id="app">
    <ListHeader />
    <router-view />
  </div>
</template>

<script>
import ListHeader from "@/components/global/ListHeader.vue";

export default {
  name: "Title",
  components: {
    ListHeader,
  },
};
</script>

<style lang="scss"></style>
