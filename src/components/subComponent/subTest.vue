<template>
  <div class="child">
    <slot>
      <p>如果父组件没有插入内容，我将作为默认出现</p>
    </slot>
  </div>
</template>
<script>
export default {
  name: 'child-component',
  component: {

  }
}
</script>

<style scoped>
  .child{
    /*width: 500px;
    height: 500px;
    background:red;
    margin: 0 auto;*/
  }
