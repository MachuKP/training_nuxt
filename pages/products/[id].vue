<template>
    <ProductDetails :product="product" />
</template>

<script setup>
definePageMeta({
    layout: 'product'
})

const { id } = useRoute().params
const uri = 'https://fakestoreapi.com/products/' + id
const { data: product } = await useFetch(uri, { key: id })
if (!product.value) {
    throw createError({ statusCode: 404, statusMassage: 'Product not found' })
}
</script>