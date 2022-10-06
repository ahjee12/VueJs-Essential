<template>
  <li>
    {{ text }}
    <!-- react에서는 하위에서 상위 component delete method를 전달 -->
    <!-- vue에서는 상단  -->
    <button @click="itemDelete">삭제</button>
  </li>
</template>
<script>
export default {
  props: {
    index: {
      type: Number,
    },
    text: {
      type: String,
      required: true,
      //   prop이 undefined로 전달될 때
      default: "없음!",
    },
  },
  methods: {
    itemDelete() {
      this.$emit("delete", this.index);
    },
  },
};
</script>
<style lang=""></style>
