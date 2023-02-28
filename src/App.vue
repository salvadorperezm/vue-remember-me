<template>
  <page-layout></page-layout>
</template>

<script>
import PageLayout from "./components/PageLayout.vue"

export default {
  components: {
    'page-layout': PageLayout
  }
}
</script>

<style>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --black: #000000;
  --orange: #c5641f;
  --purple: #592593;
  --white: #ffffff;
  --wine: #932525;
}

html {
  font-family: sans-serif;
}

section {
  border-radius: 10px;
  margin-block: 40px;
  padding: 40px;
  box-shadow: rgba(17, 17, 26, 0.1) 0px 4px 16px, rgba(17, 17, 26, 0.05) 0px 8px 32px;
}
</style>
