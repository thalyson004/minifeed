<template>
  <div class="pagination">
    <span
      v-for="i in pages"
      class="pagination-item"
      :class="{ 'pagination-item-active': i == modelValue }"
      @click="changePage(i)"
      :key="`page-${i}`"
      >{{ i }}</span
    >
  </div>
</template>

<script>
export default {
  props: {
    modelValue: {
      type: Number,
      required: true,
    },
    pages: {
      type: Number,
      required: true,
    },
  },
  methods: {
    changePage(page) {
      console.log("Clicked" + page);
      this.$emit("update:modelValue", page);
    },
  },
};
</script>

<style lang="scss" scoped>
.pagination {
  margin-top: 20px;
}

.pagination-item {
  padding-top: 5px;
  padding-bottom: 5px;
  padding-left: 10px;
  padding-right: 10px;

  margin-left: 5px;
  margin-right: 5px;

  font-size: 1.5rem;
  cursor: pointer;
  border-radius: 4px;

  color: #999999;
}

.pagination-item-active {
  background-color: #42b983;
  color: white;
}
</style>
