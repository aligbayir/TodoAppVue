<template>
  <div>
    <div class="app">
      <div class="card">
        <div class="header">
          <h1 class="title">To-Do List</h1>
          <button class="delete-all" @click="deleteAll">Delete All</button>
        </div>
        <div class="body">
          <ul class="list">
            <li v-for="(item, index) in items" :key="index">
              <label>
                <input type="checkbox" v-model="item.done" />
                <span class="name">{{ item.name }}</span>
              </label>
              <button class="delete-item" @click="deleteItem(index)">
                Delete
              </button>
            </li>
          </ul>
          <div class="add-item">
            <input
              type="text"
              class="input"
              v-model="newItem"
              placeholder="Add a new task"
              @keydown.enter="addItem"
            />
            <button class="add-button" @click="addItem">Add</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      newItem: "",
    };
  },
  methods: {
    addItem() {
      if (this.newItem.trim() !== "") {
        this.items.push({
          name: this.newItem,
          done: false,
        });
        this.newItem = "";
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1);
    },
    deleteAll() {
      this.items = [];
    },
  },
};
</script>
<style>
.app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f5f5f5;
}

.card {
  width: 450px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  background-color: #1976d2;
  color: #fff;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.title {
  margin: 0;
  font-size: 24px;
}

.delete-all {
  border: none;
  background: transparent;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
  outline: none;
}

.body {
  padding: 20px;
}

.list {
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

label {
  display: flex;
  align-items: center;
}

input[type="checkbox"] {
  margin-right: 10px;
}

.name {
  margin-left: 10px;
  font-size: 16px;
  text-decoration: none;
  color: #333;
}
input {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
button {
    width: 75px;
    height: 50px;
    background-color: #136fcc;
    border-radius: 5px;
    color: white;
    border: 1px solid #ddd;
    text-align: center;
    align-items: center;
    margin-top: 5px;
}
button:hover {
    background-color: #117ce7;
    cursor: pointer;
}
</style>
