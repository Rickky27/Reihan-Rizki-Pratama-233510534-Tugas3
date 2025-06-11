<template>
  <div class="card child">
    <h3 class="child-title">Child Component</h3>
    <p class="child-description">This is the child component that contains a grandchild component.</p>
    
    <!-- Slot for parent content with fallback -->
    <slot>
      <div class="slot-fallback">
        Default slot content (shown if parent doesn't provide slot content)
      </div>
    </slot>
    
    <div class="button-group">
      <button 
        class="btn btn-primary"
        @click="sendMessageToParent"
      >
        <span class="btn-text">Send Message to Parent</span>
      </button>
    </div>
    
    <GrandchildComponent 
      v-if="showGrandchild"
      @message-to-parent="forwardMessage"
      class="grandchild-wrapper"
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
        timestamp: new Date().toISOString(),
        component: 'ChildComponent'
      })
    },
    forwardMessage(msg) {
      this.$emit('message-from-grandchild', {
        ...msg,
        forwarded: true,
        forwardedAt: new Date().toISOString(),
        forwardedBy: 'ChildComponent'
      })
    }
  }
}
</script>

<style scoped>
.child {
  background-color: #e3f2fd;
  margin: 20px 0;
  padding: 24px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.child:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.15);
}

.child-title {
  color: #1565c0;
  margin-bottom: 16px;
  font-size: 1.5rem;
  font-weight: 600;
}

.child-description {
  color: #424242;
  margin-bottom: 16px;
  line-height: 1.6;
}

.slot-fallback {
  background-color: #f5f5f5;
  padding: 16px;
  border-radius: 8px;
  margin: 16px 0;
  font-style: italic;
  color: #616161;
  border-left: 4px solid #90caf9;
}

.button-group {
  margin: 24px 0;
  display: flex;
  gap: 12px;
}

.btn {
  border: none;
  padding: 12px 24px;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn-primary {
  background-color: #1976d2;
  color: white;
  box-shadow: 0 2px 4px rgba(25, 118, 210, 0.3);
}

.btn-primary:hover {
  background-color: #1565c0;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(25, 118, 210, 0.4);
}

.btn-text {
  font-weight: 500;
  letter-spacing: 0.5px;
}

.grandchild-wrapper {
  margin-top: 20px;
  border-top: 1px solid #bbdefb;
  padding-top: 20px;
}
</style>