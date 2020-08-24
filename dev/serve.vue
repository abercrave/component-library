<script>
import Vue from "vue";
import { MyComponent } from "@/entry";

export default Vue.extend({
  name: "ServeDev",
  components: {
    MyComponent,
  },
});
</script>

<template>
  <div id="app">
    <my-component />
  </div>
</template>
