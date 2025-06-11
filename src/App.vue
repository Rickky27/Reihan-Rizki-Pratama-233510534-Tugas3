<template>
  <div class="app">
    <h1>Nested Components</h1>
    <ParentComponent />
  </div>
</template>

<script>
import ParentComponent from './components/ParentComponent.vue'

export default {
  name: 'App',
  components: {
    ParentComponent
  }
}
</script>

<style>
/* Base Styles */
:root {
  --primary: #4361ee;
  --primary-light: #4895ef;
  --secondary: #3f37c9;
  --accent: #f72585;
  --light: #f8f9fa;
  --dark: #212529;
  --success: #4cc9f0;
  --warning: #f8961e;
  --danger: #ef233c;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #f5f7fa;
}

.app {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem 1rem;
  color: var(--dark);
}

h1 {
  color: var(--primary);
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2.5rem;
  font-weight: 700;
  position: relative;
  display: inline-block;
  width: 100%;
}

h1::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 4px;
  background: linear-gradient(90deg, var(--primary), var(--accent));
  border-radius: 2px;
}

.card {
  border: none;
  border-radius: 12px;
  padding: 1.5rem;
  margin: 1rem 0;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
  background: white;
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

button {
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  cursor: pointer;
  margin: 0.5rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  font-size: 0.85rem;
  transition: all 0.3s ease;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0 7px 14px rgba(0, 0, 0, 0.1);
  background: linear-gradient(135deg, var(--primary-light), var(--primary));
}

.slot-content {
  background: linear-gradient(to right, #f8f9fa, #e9ecef);
  padding: 1.5rem;
  border-radius: 8px;
  margin-top: 1rem;
  border-left: 4px solid var(--accent);
}

.messages {
  margin-top: 1.5rem;
  padding: 1rem;
  background-color: var(--light);
  border-radius: 8px;
  border: 1px solid rgba(0, 0, 0, 0.1);
}

.messages h3 {
  color: var(--secondary);
  margin-bottom: 0.5rem;
}

.messages ul {
  list-style-type: none;
}

.messages li {
  padding: 0.5rem;
  margin: 0.25rem 0;
  background-color: white;
  border-radius: 4px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Component-specific styles will be scoped in each component */
</style>