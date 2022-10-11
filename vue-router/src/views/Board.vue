<template>
  <div class="board">이곳은 {{ boardName }}게시판입니다.</div>
</template>
<script>
export default {
  name: "BoardView",
  data() {
    return {
      boardName: "",
    };
  },
  created() {
    this.boardName = this.$route.params.id;
  },
};
</script>
<style lang=""></style>
