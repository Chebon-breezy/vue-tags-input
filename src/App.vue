<script>
import TagsInput from "./components/TagsInput.vue";

export default {
  data: () => ({
    jsFrameworks: ["react.js", "Vue.js", "Angular.js"],
    backendFramework: []
  }),

  methods: {
    handleChange(tags) {
      this.jsFrameworks = [...tags];
    }
  }
};
</script>

<template>
  <h1>Your Favourite Frameworks</h1>
  <div>{{ jsFrameworks }}</div>
  <tags-input :selected-tags="jsFrameworks" @change="handleChange" />

  <div>{{ backendFramework }}</div>
  <tags-input :selected-tags="backendFramework" @change="backendFramework = [...$event]" />
</template>

<style>
h1 {
  color: blueviolet;
}
</style>
