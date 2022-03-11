<script setup>
import { ref } from "vue";
import { nanoid } from 'nanoid';
import ItemsList from "../components/ItemsList.vue";

const item = ref("");
const itemsList = ref([]);

function addItem() {
  if (item.value !== "") {
    itemsList.value.push({
      id: item.value + nanoid(),
      name: item.value,
      checkmarked: false,
    });
    item.value = "";
  }
}

function removeItem(deleteItem) {
  itemsList.value = itemsList.value.filter((item) => item !== deleteItem);
}
</script>

<template>
  <div class="input-container">
    <input
      class="input-box"
      type="text"
      placeholder="..."
      v-model="item"
      @keyup.enter="addItem"
    />
    <button class="add-button" @click="addItem">
      <img class="add-pic" src="../assets/add.svg" alt />
    </button>
  </div>
  <ItemsList :items="itemsList" @remove="removeItem" />
</template>

<style>
.input-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 1.6em;
}

.input-box {
  width: 100%;
  height: 1.2em;
  font-size: 1.5rem;
  padding: 0.04168em;
}

.add-button {
  display: flex;
  padding: 0;
  font-size: 1.5rem;
}

.add-button {
  margin-left: 0.2em;
}

.add-pic {
  width: 1.2em;
  height: 100%;
  padding: 0.04168em;
}
</style>
