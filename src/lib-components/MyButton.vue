<template>
  <button class="my-button" v-bind="$attrs" v-on="$listeners">
    <slot />
  </button>
</template>

<script>
export default {
  name: "MyButton",
};
</script>

<style scoped>
.my-button {
  border: 1px solid red;
}
</style>