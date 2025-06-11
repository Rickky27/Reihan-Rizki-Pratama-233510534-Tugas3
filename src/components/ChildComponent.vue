<template>
  <div class="card child">
    <h3>Child Component</h3>
    <p>This is the child component that contains a grandchild component.</p>
    
    <!-- Slot for parent content -->
    <slot></slot>
    
    <button @click="sendMessageToParent">Send Message to Parent</button>
    
    <GrandchildComponent @message-to-parent="forwardMessage" />
  </div>
</template>

<script>
import GrandchildComponent from './components/GrandchildComponent.vue'

export default {
  name: 'ChildComponent',
  components: {
    GrandchildComponent
  },
  methods: {
    sendMessageToParent() {
      this.$emit('message-from-child', 'Hello from Child Component!')
    },
    forwardMessage(msg) {
      this.$emit('message-from-grandchild', msg)
    }
  }
}
</script>

<style scoped>
.child {
  background-color: #e3f2fd;
  margin-top: 15px;
}
</style>