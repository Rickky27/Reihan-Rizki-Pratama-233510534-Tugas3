<template>
  <div class="card grandchild">
    <h4>Grandchild Component</h4>
    <p>This is the deepest nested component.</p>
    <button @click="sendMessageToParent">Send Message to Parent</button>
  </div>
</template>

<script>
export default {
  name: 'GrandchildComponent',
  methods: {
    sendMessageToParent() {
      this.$emit('message-to-parent', 'Greetings from Grandchild!')
    }
  }
}
</script>

<style scoped>
.grandchild {
  background-color: #f3e5f5;
  margin-top: 15px;
}
</style>