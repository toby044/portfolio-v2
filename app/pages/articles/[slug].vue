<template>
    <div>slug</div>
</template>
<script setup>
const route = useRoute();

const { data: article } = await useAsyncData(route.path, () =>
    queryContent(route.path).findOne()
);

if (!article) {
    throw createError({
        statusCode: 404,
        statusMessage: "Article not found",
        fatal: true,
    });
}
</script>
