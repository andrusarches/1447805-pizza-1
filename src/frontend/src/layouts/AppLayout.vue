<template>
  <div class="app">
    <AppLayoutHeader />
    <Index />
  </div>
</template>

<script>
import AppLayoutHeader from "@/layouts/AppLayoutHeader.vue";
import Index from "@/views/Index.vue";
export default {
  name: "AppLayout",
  components: {
    AppLayoutHeader,
    Index,
  },
};
</script>

<style></style>
