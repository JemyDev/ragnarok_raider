<template>
  <div class="notification is-warning">
    <button class="delete" @click="close"></button>
    {{ message }}
  </div>
</template>

<script>
export default {
  props: ['message'],
  methods: {
    close() {
      this.$emit('close')
    }
  }
}
</script>
