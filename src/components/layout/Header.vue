<template>
  <header>
    <nav class="navbar is-primary">
      <div class="navbar-brand">
        <a class="navbar-item" href="/">Ragnarok Raider</a>
      </div>
      <div class="navbar-end">
        <div class="navbar-item">
          <button class="button is-primary is-inverted" @click="logout">Déconnexion</button>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import firebase from 'firebase'

export default {
  methods: {
    logout() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.go({ path: this.$router.path })
        })
    }
  }
}
</script>
