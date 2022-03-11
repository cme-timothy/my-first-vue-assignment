<script setup>
const props = defineProps(["items"]);
const $emit = defineEmits(["remove"]);

function checkmarked(Clickedcheckbox) {
  props.items.forEach((item) => {
    if (item.id === Clickedcheckbox) {
      item.checkmarked = !item.checkmarked;
    }
  });
}
</script>

<template>
  <div class="item" v-for="item in props.items" :key="item.id">
    <button class="checkbox" @click="checkmarked(item.id)">
      <img v-if="item.checkmarked" class="checkmark-pic" src="../assets/checkmark.svg" alt="" />
      <img v-else class="checkmark-pic" src="../assets/empty.svg" alt="" />
    </button>
    <li class="item-name">{{ item.name }}</li>
    <button class="delete-button" @click="$emit('remove', item)">
      <img class="bin-pic" src="../assets/bin.svg" alt="" />
    </button>
  </div>
</template>

<style>
.item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1em;
}

.item-name {
  margin-left: 0.7em;
  text-align: left;
  width: 100%;
  list-style-type: none;
  font-size: 1.5rem;
}

.checkbox,
.delete-button {
  display: flex;
  padding: 0;
  font-size: 1.5rem;
}

.delete-button {
  margin-left: 0.2em;
}

.checkmark-pic,
.bin-pic {
  width: 1.2em;
  height: 100%;
  padding: 0.04168em;
}
</style>
