<template>
  <div class="container">
    <Header v-if="isUser"/>
    <main>
      <slot></slot>
    </main>
    <Footer v-if="isUser"/>
  </div>
</template>

<script>
import firebase from 'firebase'
import Header from './Header'
import Footer from './Footer'

export default {
  props: ['showLayout'],
  components: { Header, Footer },
  data() {
    return {
      isUser: false
    }
  },
  methods: {
    getAuthUser() {
      let user = firebase.auth().currentUser
      if (user) {
        this.isUser = true
      } else {
        this.isUser = false
      }
    }
  },
  created() {
    this.getAuthUser()
  }
}
</script>
