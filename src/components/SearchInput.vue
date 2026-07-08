// ====================================================== // MINI PROJECT (Fill
in the Blank) // Reusable Search Input // Props + Emits //
====================================================== // File:
./components/SearchInput.vue

<template>
  <input
    :value="keyword"
    @input="updateKeyword"
    type="text"
    placeholder="Cari produk..."
    class="w-full rounded-lg border p-3"
  />
</template>

<script setup>
const props = defineProps({
  keyword: String,
});

const emit = defineEmits(["search"]);

const updateKeyword = (event) => {
  emit("search", event.target.value);
};
</script>
