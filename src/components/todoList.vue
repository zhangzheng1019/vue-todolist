<template>
  <div class="todoList">
    <h1 v-text="title"></h1>
    <input type="text" name="item" v-model="newItem" @keyup.enter="addItem">
    <ul>
      <li v-bind:class="{finished:item.isFinished}" v-for="item in items" v-on:click="toggleFinish(item)" v-on:mouseenter="toggleDel(item)">{{item.label}}<span> {{item.isDelete}}</span></li>
    </ul>
  </div>
</template>
<script>
import Store from '../store.js'

// new Vue({})
export default {
  name: 'todoList',
  data: function() {
    return {
      title: "This is a todo List",
      items: Store.fetch(),
      newItem: ''
    }
  },
  watch: {
    items: {
      handler: function(items) {
        Store.save(items);
      },
      deep: true
    }
  },
  methods: {
    toggleFinish: function(item) {
      item.isFinished = !item.isFinished;
    },
    addItem: function() {
      this.items.push({
        label: this.newItem,
        isFinished: false,
        isDelete: false
      });
      this.newItem = '';
    },
    toggleDel: function(item) {

    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  border: 1px solid #42b983;
  border-radius: 2px;
  font-size: 20px;
  height: 30px;
  line-height: 30px;
  outline: none;
}

ul {
  list-style: none;
}

li {
  font-size: 20px;
}

a {
  color: #42b983;
  text-decoration: none;
}

.finished {
  text-decoration: line-through;
}
</style>
