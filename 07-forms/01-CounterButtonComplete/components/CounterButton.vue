<template>
  <button @click="() => localCount++">{{localCount}}</button>
</template>

<script>
export default {
  name: 'CounterButton',

  props: {
    count: Object,
  },

  data() {
    return {
      localCount: this.count || 0,
    };
  },

  watch: {
    count: {
      handler() {
        this.localCount = this.count;
      }
    },
    localCount: {
      handler() {
        this.$emit('update:count', this.localCount);
      },
    },
  },
};
</script>
