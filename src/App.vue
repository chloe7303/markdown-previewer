<template>
  <i-container id="app">
    <i-row>
      <i-column sm="6" class="border-right">
        <h1 class="_text-primary">Markdown
          <i-button @click="toggleDarkMode">
          <i-icon icon="light" />
        </i-button>
        </h1>
        <i-textarea v-model="value" placeholder="Type something..." clearable/>
      </i-column>
      <i-column sm="6">
        <h1 class="_text-primary _border-bottom _border-color-primary _padding-bottom-1">Rendered Text</h1>
        <vue-markdown :source="value">{{ value }}</vue-markdown>
      </i-column>
    </i-row>
  </i-container>   
</template>

<script>
import VueMarkdown from '@adapttive/vue-markdown'

export default {
  name: 'App',
  components: {
    VueMarkdown
  },
  data: () => ({
    value: 
    `#  h1 Heading
---
## h2 Heading
---
### h3 Heading
---

**This is bold text**

This is unordered lists
+ Create a list by starting a line with +, -, or *
+ Sub-lists are made by indenting 2 spaces:
  - Marker character change forces new list start:
    * Ac tristique libero volutpat at
    + Facilisis in pretium nisl aliquet
    - Nulla volutpat aliquam velit
+ Very easy!
    `
  }),
  methods: {
    toggleDarkMode() {
      this.$inkline.config.variant = this.$inkline.config.variant === 'light' ? 'dark' : 'light';
    }
  }
}
</script>

<style scoped>
textarea {
  padding: 15px;
}

.border-right {
  border-right: 1px solid #888;
}

</style>