<template>
  <div class="list">
    <div class="list__empty" v-if="!items.length">
      You have nothing to do! Don't be lazy, you can add an item now!
    </div>

    <ul>
      <li v-for="(item, index) in items" :key="index">
        <span>
          {{ item }}
        </span>

        <div class="actions">
          <button @click="deleteItem(index)">
            <Trash />
          </button>

          <button @click="editItem(item, index)">
            <Edit />
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import Trash from "../ui/icons/trash";
import Edit from "../ui/icons/edit";

export default {
  props: {
    items: Array,
    deleteItem: Function,
    editItem: Function
  },
  components: {
    Trash,
    Edit
  }
};
</script>
