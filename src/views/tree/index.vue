<template>
  <div class="app-container">
    <el-input placeholder="Filter keyword" v-model="filterText" style="margin-bottom:30px;"></el-input>

    <el-tree class="filter-tree" :data="data2" :props="defaultProps" default-expand-all :filter-node-method="filterNode" ref="tree2"></el-tree>

  </div>
</template>

<script>
export default {
  watch: {
    filterText(val) {
      this.$refs.tree2.filter(val)
    }
  },

  methods: {
    filterNode(value, data) {
      if (!value) return true
      return data.label.indexOf(value) !== -1
    }
  },

  data() {
    return {
      filterText: '',
      data2: [{
        id: 1,
        label: '一级目录 1',
        children: [{
          id: 4,
          label: '二级目录 1-1',
          children: [{
            id: 9,
            label: '三级目录 1-1-1'
          }, {
            id: 10,
            label: '三级目录 1-1-2'
          }]
        }]
      }, {
        id: 2,
        label: '一级目录 2',
        children: [{
          id: 5,
          label: '二级目录 2-1'
        }, {
          id: 6,
          label: '二级目录 2-2'
        }]
      }, {
        id: 3,
        label: '一级目录 3',
        children: [{
          id: 7,
          label: '二级目录 3-1'
        }, {
          id: 8,
          label: '二级目录 3-2'
        }]
      }],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    }
  }
}
</script>

