<template>
  <section class="hero is-fullheight">
    <div class="hero-body">
      <div class="container has-text-centered">
        <div class="column is-4 is-offset-4">
          <h3 class="title has-text-grey">Connectez vous au raider !</h3>
          <div class="box">
            <Notification v-if="errMessage.length > 0" :message="errMessage" @close="closeNotification" />
            <form>
              <div class="field">
                <div class="control">
                  <input class="input is-large" type="email" placeholder="Email" v-model="email">
                </div>
              </div>

              <div class="field">
                <div class="control">
                  <input class="input is-large" type="password" placeholder="Mot de passe" v-model="password">
                </div>
              </div>
              <div class="field">
                <label class="checkbox">
                  <input type="checkbox">
                  Se souvenir de moi
                </label>
              </div>
              <button @click="login" class="button is-block is-primary is-large is-fullwidth">Connexion</button>
            </form>
          </div>
          <p class="has-text-grey">
           <router-link to="/register">S'inscrire</router-link>
         </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import firebase from 'firebase'
import Notification from '@/components/ui/Notification'

export default {
  components: { Notification },
  data() {
    return {
      email: '',
      password: '',
      errMessage: ''
    }
  },
  methods: {
    login(e) {
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            this.$router.go({ path: this.$router.path })
          },
          err => {
            this.errMessage = err.message
          }
        )
      e.preventDefault()
    },
    closeNotification() {
      this.errMessage = ''
    }
  }
}
</script>

<style>
</style>
