<template>
  <div id="app">
    <div class="count">{{ count }}</div>
    <button @click="increase">증가</button>
    <nav>
      <!-- link to에는 index.js에서 정의한 주소가 들어감! -->
      <!-- 객체형으로 수정할 가능성이 큰 path대신 name으로 주소 설정하기 -->
      <router-link :to="{ name: 'home' }">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link :to="{ name: 'board', params: { id: 'news' } }"
        >게시판</router-link
      >
    </nav>
    <router-view />
  </div>
</template>
<script>
import { mapState } from "vuex";

export default {
  data() {
    return {
      localCount: 100,
    };
  },
  computed: mapState({
    // arrow functions can make the code very succinct!
    count: (state) => state.count,

    // passing the string value 'count' is same as `state => state.count`
    countAlias: "count",

    // ★ 기본 - to access local state with `this`, a normal function must be used
    countPlusLocalState(state) {
      return state.count + this.localCount;
    },
  }),
  methods: {
    increase() {
      // react - dispatch() / vue - this.$store.commit()
      this.$store.commit("increment");
    },
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
