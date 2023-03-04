<script>
import { ref, onMounted } from "vue";

export default {
  setup() {
    const items = ref([]);

    onMounted(() => {
      const historyLS = localStorage.getItem("history");
      if (historyLS) {
        items.value = JSON.parse(historyLS);
      }
    });
   
    
    return {
      items,
    };
  },
};
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <ul class="list-group">
          <li
            v-for="(item, key) in items"
            v-bind:key="key"
            class="list-group-item"
          >
            {{ item }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .list-group-item {
    color: red;
  }
</style>
