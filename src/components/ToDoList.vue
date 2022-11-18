<template>
  <ul>
    <li v-for="(item, index) in toDoList" :key="index">
      <input
        type="checkbox"
        :id="item.name"
        :value="item.name"
        v-model="checkedItems"
      />
      <!--{{ item.name }}-->
      <span :class="{ done: checkedItems.includes(item.name) }">{{item.name}}</span>

      <span class="delete" @click="deleteItem(index)">X</span>
    </li>
  </ul>
</template>

<script>
import { ref } from 'vue';
export default {
  props: {
    deleteItem: {
      type: Function,
      required: true,
    },
    toDoList: {
      type: Array,
      required: true,
    },
  },
  setup() {
    const checkedItems = ref([]);
    return { checkedItems };
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  font-family: courier;
}
ul li {
  margin: 5px;
  cursor: pointer;
}
ul li :hover {
  opacity: 0.4;
}

.done {
  text-decoration: line-through;
}

.delete {
  background-color: red;
  color: white;
  padding-top: 2px;
  padding-bottom: 2px;
  /*padding: 10 0 10px;*/
  padding-left: 10px;
  padding-right: 10px;
  line-height: 1;
  border-radius: 5px;
  cursor: pointer;
}
</style>