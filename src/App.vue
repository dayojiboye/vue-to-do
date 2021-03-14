<template>
  <div class="layout">
    <Header />
    <main class="main">
      <div class="main-wrapper">
        <div class="input-wrapper">
          <Input v-model="text" :attr="attr" />
          <button @click="addItem" :disabled="!text">
            Submit
          </button>
        </div>

        <List :items="items" :deleteItem="deleteItem" :editItem="editItem" />
      </div>
    </main>
  </div>
</template>

<script>
import Header from "./components/ui/header/header.vue";
import Input from "./components/ui/input/input.vue";
import List from "./components/list/list.vue";

export default {
  name: "App",
  components: {
    Header,
    Input,
    List
  },
  data() {
    return {
      items: [],
      text: "",
      attr: {
        type: "text"
      }
    };
  },
  methods: {
    addItem() {
      this.items.unshift(this.text);
      this.text = "";
    },
    deleteItem(id) {
      this.items = this.items.filter((_, index) => {
        return index !== id;
      });
    },
    editItem(item, id) {
      this.deleteItem(id);
      this.text = item;
    }
  }
};
</script>

<style lang="scss">
.layout {
  width: var(--full);
  max-width: var(--wrapper-max-width);
  min-width: var(--wrapper-min-width);
  margin: 0 auto;

  .main {
    width: var(--full);

    .main-wrapper {
      width: var(--full);
      padding: 32px 16px;

      .input-wrapper {
        width: 90%;
        max-width: 500px;
        margin: 0 auto;

        > input {
          background: var(--white);
          border: 1px solid var(--fade);
          border-radius: var(--border-radius-mini);
          padding: 16px 12px;
        }

        > button {
          background: var(--goldish);
          margin-top: 20px;
          width: 100px;
          padding: 16px 10px;
          font-weight: 600;
          border: 1px solid var(--goldish);
          border-radius: var(--border-radius-mini);

          &:disabled {
            background: var(--fade);
            border: 1px solid var(--fade);
            color: var(--white);
            cursor: not-allowed;
          }
        }
      }
    }
  }
}
</style>
