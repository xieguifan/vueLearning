<template>
  <div>
    <a-button type="primary" @click="showModal">
      Modal
    </a-button>
    <a-modal v-model="visible" title="Modal" ok-text="确认" cancel-text="取消" @ok="hideModal">
      <p>Bla bla ...</p>
      <p>Bla bla ...</p>
      <p>Bla bla ...</p>
    </a-modal>
    <br />
    <br />
    <a-button @click="confirm">
      Confirm
    </a-button>
  </div>
</template>
<script>
export default {
  data () {
    return {
      visible: false
    }
  },
  methods: {
    showModal () {
      this.visible = true
    },
    hideModal () {
      this.visible = false
    },
    confirm () {
      this.$confirm({
        title: 'Confirm',
        content: 'Bla bla ...',
        okText: '确认',
        cancelText: '取消'
      })
    }
  }
}
</script>
