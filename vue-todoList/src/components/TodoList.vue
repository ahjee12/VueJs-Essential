<template>
  <div>
    <!-- react는 useState, e.target or ref onChange함수 필요-->
    <input type="text" v-model="inputValue" />
    <!-- react는 onClick={} 중괄호에 method 넣음-->
    <button @click="addItem">추가하기</button>
    <ul>
      <!-- : 앞에 한 칸 띄우기/ 변수 넣을 땐 쌍점, inline일 땐 기본 html 방식과 같음-->
      <ListItem
        v-for="(value, i) in listArray"
        :key="i"
        :index="i"
        :text="sendMsg(value)"
        @delete="catchDeleteItem"
      />
    </ul>
  </div>
</template>
<script>
import ListItem from "./ListItem";
export default {
  data() {
    return {
      inputValue: "",
      listArray: [],
      style: { color: "red" },
    };
  },
  components: {
    ListItem,
  },
  methods: {
    addItem() {
      this.listArray.push(this.inputValue);
      this.inputValue = "";
    },
    sendMsg(value) {
      return value === "" ? undefined : value;
    },
    catchDeleteItem(i) {
      console.log(i);
      //   this.listArray.splice(undefined, 1);
      this.listArray.splice(i, 1);
    },
  },
};
</script>
<style lang=""></style>
