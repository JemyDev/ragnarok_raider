<template>
  <section>
    <article class="hero is-primary">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Bienvenue {{ username }} !
          </h1>
        </div>
      </div>
    </article>
  </section>
</template>

<script>
import firebase from 'firebase'

export default {
  data() {
    return {}
  },
  computed: {
    username() {
      return firebase.auth().currentUser.displayName
    }
  }
}
</script>

<style>
section {
  margin: 2em 0;
}
</style>
