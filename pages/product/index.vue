<script lang="ts" setup>
import { useProductsStore } from "~/stores/products";

const productStore = useProductsStore();
const allProducts = ref([]);

productStore.getAllProducts().then(() => {
    allProducts.value = productStore.products;
});

const selectedCategory = ref("");
</script>
<template>
    <section>
        <div class="container">
            <div class="py-10">
                <div class="mb-8 flex justify-end gap-6">
                    <Dropdown @selected-category="selectedCategory = $event" />
                </div>
                <div class="flex gap-10 flex-wrap ml-28">
                    <template v-for="(item, index) in allProducts" :key="index">
                        <CardsCardProduct :product="item" class="w-[calc(83%/4)]" />
                    </template>
                </div>
            </div>
        </div>
        <br />
        <br />
        <br />
    </section>
</template>