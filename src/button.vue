<template>
  <button class="g-button" :class="{[`icon-${iconPosition}`]:true}" @click="$emit('click')">
    <g-icon class="icon" v-if="icon && !loading" :name="icon"></g-icon>
    <g-icon class="loading icon" v-if="loading" name="loading"></g-icon>
    <div class="content"><slot/></div>
  </button>
</template>
<script>
export default {
  props:{
    loading:{
      type:Boolean,
      default: false
    },
    icon:{},
    iconPosition:{
      type:String,
      default:'left',
      validator(value){ //属性的检查器
        return value === 'left' || value === 'right';
      }
    }
  }
}
</script>
<style lang="scss">
.g-button {
  @keyframes spin {
      0%{transform: rotate(0deg)}
      100%{transform: rotate(360deg)}
  }
  font-size:var(--font-size); height: var(--button-height); padding: 0 1em;
  border-radius: var(--border-radius); border: 1px solid var(--border-color);background: var(--button-bg);
  display: inline-flex;justify-content: center;align-items: center;
  vertical-align: middle;//内联元素行居中
  &:hover {border-color: var(--border-color-hover);}
  &:active {background-color: var(--button-active-bg);}
  &:focus {outline: none;}
  > .icon{order:1;margin-right:.1em;}
  > .content{order:2;}
  &.icon-right{
    > .icon {order:2;margin-right:0;margin-left: .1em}
    > .content{order:1;}
  }
  .loading{
    animation: spin 2s infinite linear;
  }
}
</style>
