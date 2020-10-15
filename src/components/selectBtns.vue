<template>
  <a-tree-select
    @focus="expand"
    v-model="value"
    show-search
    :dropdownMatchSelectWidth=true
    tree-data-simple-mode
    style="width: 150PX"
    :dropdown-style="{ maxHeight: '100px', overflow: 'scroll' }"
    :tree-data="treeData"
    placeholder="Please select"
    :load-data="onLoadData"
  />
</template>

<script>
export default {
  data () {
    return {
      value: undefined,
      treeData: [
        { id: 1, pId: 0, value: '1', title: 'Expand to load' },
        { id: 2, pId: 0, value: '2', title: 'Expand to load' },
        { id: 3, pId: 0, value: '3', title: 'Tree Node', isLeaf: true }
      ]
    }
  },
  watch: {
    value (value) {
      console.log(value)
    }
  },
  mounted () {
    // setTimeout(() => {
    //   this.goBottomEvent()
    // }, 3000)
  },
  methods: {
    expand () {
      debugger
      console.log(126)
    },
    genTreeNode (parentId, isLeaf = true) {
      const random = Math.random()
        .toString(36)
        .substring(2, 6)
      return {
        id: random,
        pId: parentId,
        value: random,
        title: isLeaf ? 'Tree Node' : 'Expand to load',
        isLeaf
      }
    },
    onLoadData (treeNode) {
      return new Promise(resolve => {
        const { id } = treeNode.dataRef
        setTimeout(() => {
          this.treeData = this.treeData.concat([
            this.genTreeNode(id, false),
            this.genTreeNode(id, true)
          ])
          resolve()
        }, 300)
      })
    },
    goBottomEvent () {
      let ele = document.querySelector('.ant-select-dropdown')
      debugger
      ele.onscroll = function () {
        var scrollT = ele.scrollTop
        var scrollH = ele.scrollHeight
        var clientH = ele.clientHeight
        // console.log(scrollT +"+"+scrollH+"+"+clientH);
        if (scrollT === scrollH - clientH) {
          console.log('到底部了')
        } else if (scrollT === 0) {
          console.log('到顶部了')
        }
      }
    }
  }
}
</script>
