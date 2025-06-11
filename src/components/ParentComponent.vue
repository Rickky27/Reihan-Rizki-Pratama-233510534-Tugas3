<template>
  <div class="card parent">
    <h2>Parent Component</h2>
    <p>Message from child: {{ childMessage }}</p>
    
    <ChildComponent 
      @message-from-child="handleChildMessage"
      @message-from-grandchild="handleGrandchildMessage"
    >
      <template #default>
        <div class="slot-content">
          <h3>Content passed from Parent to Child via Slot</h3>
          <p>This is some content inserted into the child component's slot.</p>
          <p>You can pass any HTML or components here!</p>
        </div>
      </template>
    </ChildComponent>
    
    <div v-if="messages.length" class="messages">
      <h3>All Messages:</h3>
      <ul>
        <li v-for="(msg, index) in messages" :key="index">{{ msg }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue'

export default {
  name: 'ParentComponent',
  components: {
    ChildComponent
  },
  data() {
    return {
      childMessage: '',
      messages: []
    }
  },
  methods: {
    handleChildMessage(msg) {
      this.childMessage = msg
      this.messages.push(`Child says: ${msg}`)
    },
    handleGrandchildMessage(msg) {
      this.messages.push(`Grandchild says: ${msg}`)
    }
  }
}
</script>

<style scoped>
.parent {
  background-color: #e8f5e9;
}
.messages {
  margin-top: 20px;
  padding: 10px;
  background-color: #fff;
  border-radius: 4px;
}
</style>