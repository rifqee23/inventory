<template>
  <div class="user-view">
    <div v-if="!showForm">
      <div class="scrollable-content">
        <TransactionList
          v-if="currentComponent === 'items'"
          @edit-item="showEditForm"
        />
        <HistoryList v-if="currentComponent === 'history'" />
      </div>
    </div>

    <div v-if="showForm" class="form-container">
      <ItemForm />
    </div>
  </div>
</template>

<script>
import HistoryList from "../components/user/history/HistoryList.vue";
import ItemForm from "../components/user/item/ItemForm.vue";
import ItemList from "../components/user/item/ItemList.vue";
import TransactionList from "../components/user/transaction/TransactionList.vue";

export default {
  components: {
    HistoryList,
    ItemForm,
    ItemList,
    TransactionList,
  },

  data() {
    return {
      showForm: false,
      currentComponent: "items",
    };
  },

  methods: {
    showEditForm() {
      this.showForm = true;
      this.currentComponent = "items";
    },
  },
};
</script>
