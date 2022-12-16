<template>
  <aside class="menu-column column no-wrap">
    <q-btn label="Стартовая страничка" flat style="color: #ff0080" @click="goToIndexPage" />
    <q-btn label="ToDo лист" flat style="color: #ff0080" />
    <q-btn label="Музыкальная" flat style="color: #ff0080" @click="goToMusicPage" />
    <q-btn label="and more..." flat style="color: #ff0080" />
  </aside>
</template>

<script>
export default {
  methods: {
    goToMusicPage() {
      this.$router.push("/music");
    },
    goToIndexPage() {
      this.$router.push("/");
    }
  },
};
</script>

<style lang="scss" scoped>
</style>
