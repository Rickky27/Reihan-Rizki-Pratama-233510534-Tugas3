<template>
  <div class="card child">
    <h3>Child Component</h3>
    <p>This is the child component that contains a grandchild component.</p>
    
    <!-- Slot for parent content with fallback -->
    <slot>
      <div class="slot-fallback">
        Default slot content (shown if parent doesn't provide slot content)
      </div>
    </slot>
    
    <div class="button-group">
      <button 
        class="btn-primary"
        @click="sendMessageToParent"
      >
        Send Message to Parent
      </button>
    </div>
    
    <GrandchildComponent 
      v-if="showGrandchild"
      @message-to-parent="forwardMessage"
    />
  </div>
</template>

<script>
// Using absolute path import to prevent resolution issues
import GrandchildComponent from '@/components/GrandchildComponent.vue'

export default {
  name: 'ChildComponent',
  components: {
    GrandchildComponent
  },
  data() {
    return {
      showGrandchild: true
    }
  },
  methods: {
    sendMessageToParent() {
      this.$emit('message-from-child', {
        message: 'Hello from Child Component!',
        timestamp: new Date().toISOString()
      })
    },
    forwardMessage(msg) {
      this.$emit('message-from-grandchild', {
        originalMessage: msg,
        forwarded: true,
        timestamp: new Date().toISOString()
      })
    }
  }
}
</script>

<style scoped>
.child {
  background-color: #e3f2fd;
  margin-top: 15px;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

h3 {
  color: #1976d2;
  margin-bottom: 12px;
}

.slot-fallback {
  background-color: #f5f5f5;
  padding: 12px;
  border-radius: 4px;
  margin: 12px 0;
  font-style: italic;
  color: #666;
}

.button-group {
  margin: 16px 0;
  display: flex;
  gap: 8px;
}

.btn-primary {
  background-color: #1976d2;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color