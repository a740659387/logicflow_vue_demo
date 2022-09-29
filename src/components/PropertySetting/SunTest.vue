<template>
  <div>
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="组件名称">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  name: 'SunTest',
  props: {
    nodeData: Object,
    lf: Object || String,
  },
  mounted() {
    const { properties } = this.$props.nodeData
    if (properties) {
      this.$data.form = Object.assign({}, this.$data.form, properties)
    }
  },
  data() {
    return {
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!');
      // const { id } = this.$props.nodeData
      // this.$props.lf.setProperties(id, this.$data.form);
      const nodeData = this.$props.nodeData
      nodeData.properties = this.$data.form
      this.$props.lf.setProperties(nodeData.id, this.$data.form);
      this.$emit('onClose')
    }
  }
}
</script>
<style scoped>
</style>
