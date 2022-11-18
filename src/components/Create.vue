<template>
  <div id = "emptyInput">
    t
  </div>
  <form @submit.prevent="doCreate">
    <input type="text" v-model="item" placeholder="Add ToDo Item" />
    <button>Create</button>
  </form>
</template>

<script>
import { ref } from "vue";
export default {
  props: {
    create: { type: Function, required: true }
  },
  setup(props) {
    let item = ref("");
    function doCreate() {
      if(item.value != ""){
        console.log("Create..." + item.value);
        props.create(item.value);
      }
      else{
        const div = document.getElementById('emptyInput');
        console.log("Input has to be set first");
        div.innerHTML = "Please insert an item to add";
      }
    }
    return { item, doCreate };
  }
};
</script>

<style scoped>
input{
  font-family: courier;
}

button{
  font-family: courier;
}
</style>
