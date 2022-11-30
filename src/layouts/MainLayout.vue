<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="header" height-hint="98">
      <q-toolbar>
        <q-btn class="lt-md" dense flat round icon="menu" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.header {
    background-color: #0000001a;
    -webkit-backdrop-filter: blur(7px);
    backdrop-filter: blur(7px);
    color: #ff0080;
}
</style>
