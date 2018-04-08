<template>
  <section class="hero is-fullheight">
    <div class="hero-body">
      <div class="container has-text-centered">
        <div class="column is-4 is-offset-4">
          <h3 class="title has-text-grey">Inscrivez vous au raider !</h3>
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
              <button class="button is-block is-primary is-large is-fullwidth" @click="register">S'inscrire</button>
            </form>
          </div>
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
    register(e) {
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .then(
          user => {
            this.$router.go({ path: '/login' })
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
