<template>
  <!--变量不能作为key，用"[ ]"计算出变量的值，再作为key-->
  <button class="g-button" :class="{[`icon-${iconPosition}`]: true}">
    <svg v-if="icon" class="icon">
      <use :xlink:href="`#i-${icon}`"></use>
    </svg>
    <!--不能直接给slot加class-->
    <div class="content">
      <slot></slot>
    </div>
  </button>
</template>
<script>
  export default {
    props: {
      icon: {},
      loading: {
        type: Boolean,
        default: false
      },
      iconPosition: {
        type: String,
        default: 'left',
        validator (value) {
          return value === 'left' || value === 'right'
        }
      }
    }
  }
</script>
<style lang="scss">
  .g-button {
    font-size: var(--font-size);
    height: var(--button-height);
    weight: 300px;
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
    // 使用弹性盒子，才能使用 order
    display: inline-flex; justify-content: center; align-items: center;
    > .content {
      order: 2;
    }
    > .icon {
      order: 1;
      margin-right: .4em;
    }
    &.icon-right{
      > .content {
        order: 1;
      }
      > .icon {
        order: 2;
        margin-right: 0;
        margin-left: .4em;
      }
    }
    vertical-align: middle;
  }
</style>