<template>
  <Layout>
    <router-view />
  </Layout>
</template>

<script>
import Layout from './components/layout/Layout'
export default {
  components: { Layout },
  data() {
    return {}
  }
}
</script>

<style lang="scss">
@import '~bulma/css/bulma.css';
</style>
