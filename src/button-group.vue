<template>
  <div class="g-button-group"><slot/></div>
</template>
<script>
export default {
  name:"BaiButtonGroup",
  mounted(){
    for(let node of this.$el.children){
      let newNode = node.nodeName.toLowerCase()
      if(newNode !== 'button'){
        console.warn(`g-button-group的子级元素为g-button,而你使用的是${newNode}`)
      }
    }
  }
}
</script>
<style lang="scss" scoped>
  .g-button-group{
    display: inline-flex;
    vertical-align: middle;
    > .g-button{
      border-radius: 0;
      &:not(.first-child){
      margin-left:-1px;
      }
      &:first-child{
        border-top-left-radius: var(--border-radius);
        border-bottom-left-radius: var(--border-radius);
      }
      &:last-child{
        border-top-right-radius: var(--border-radius);
        border-bottom-right-radius: var(--border-radius);
      }
      &:hover{
        position: relative;
        z-index: 1;
      }
    }
  }
</style>
