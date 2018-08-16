<template>
  <button class="g-button"><slot></slot></button>
</template>
<script>
  export default {
  
  }
</script>
<style lang="scss">
  .g-button {
    font-size: var(--font-size);
    height: var(--button-height);
    padding: 0 1em;   /*不直接设置按钮的宽度，用padding来做*/
    border-radius: var(--border-radius);
    border: 1px solid var(--border-color);
    background: var(--button-bg);
    &:hover {
      border-color: var(--border-color-hover);
    };
    &:active {
      background: var(--button-active-bg);
    };
    &:focus {
      outline: none;
    };
  }
</style>