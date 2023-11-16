<script lang="ts" setup>
import { products } from "~/composables/constants/products";
const selectedCategory = ref("");
const allProducts = computed(() => {
    if (selectedCategory.value) {
        return products.filter((item) => item.category === selectedCategory.value);
    }
    return products;
});
</script>
<template>
    <section>
        <div class="container">
            <div class="py-10">
                <div class="mb-8 flex justify-end gap-6">
                    <NuxtLink to="/category/create"
                        class="bg-orange-500 text-white flex justifycenter items-center px-3 rounded-lg">Create Category
                    </NuxtLink>
                    <NuxtLink to="/product/create"
                        class="bg-green-500 text-white flex justify-center items-center px-3 rounded-lg">Create Products
                    </NuxtLink>
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