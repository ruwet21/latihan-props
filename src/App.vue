// File: ./App.vue

<template>
  <main class="min-h-screen bg-slate-100 p-10">
    <div class="max-w-xl mx-auto space-y-6">
      <SearchInput :keyword="keyword" @search="handleSearch" />

      <p class="font-semibold">
        Total:
        {{ filteredProducts.length }}
      </p>

      <div v-if="filteredProducts.length" class="space-y-3">
        <div
          v-for="product in filteredProducts"
          :key="product.id"
          class="rounded-lg border bg-white p-4"
        >
          {{ product.name }}
        </div>
      </div>

      <div v-else class="rounded-lg bg-red-100 p-4 text-red-700">
        Produk tidak ditemukan.
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref, computed } from "vue";
import SearchInput from "./components/SearchInput.vue";

const keyword = ref("");

const products = ref([
  { id: 1, name: "Laptop" },
  { id: 2, name: "Mouse" },
  { id: 3, name: "Keyboard" },
  { id: 4, name: "Monitor" },
  { id: 5, name: "Speaker" },
]);

const filteredProducts = computed(() => {
  return products.value.filter((product) =>
    product.name.toLowerCase().includes(keyword.value.toLowerCase()),
  );
});

const handleSearch = (value) => {
  keyword.value = value;
};
</script>
