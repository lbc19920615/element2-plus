<template>
<draggable v-model="innerTags"
           class="draggable-tags"
@change="onChange"
>
  <el-tag
      :key="tag"
      v-for="tag in innerTags"
      :disable-transitions="false">
    {{tag}}
  </el-tag>
</draggable >
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'DraggableTags',
  props: {
    tags: Array
  },
  components: {
    draggable,
  },
  data() {
    return {
      innerTags: []
    }
  },
  mounted() {
    this.innerTags = this.tags
  },
  watch: {
    tags(newVal) {
      this.innerTags = newVal
    }
  },
  methods: {
    onChange() {
      this.$emit('input', this.innerTags)
    }
  }
};
</script>

<style scoped>

</style>
