<template>
  <div class="container">
    <child-component>
      <!-- <p>分发的内容</p>
      <p>更多分发的内容</p> -->
      <slot></slot>
    </child-component>
  </div>
</template>
<script>
import childComponent from './subComponent/subTest.vue'
export default {
  name: 'test',
  component: {
    childComponent
  }
}
</script>

<style scoped lang="less">
  .container{
    width: 500px;
    height: 500px;
    background:red;
    margin: 0 auto;
    .title{
      background: blue;
      width: 100px;
      height: 100px;
    }
  }
</style>
