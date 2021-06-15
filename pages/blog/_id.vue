<template>
    <div>
        <h1>pages/blog/index.vue</h1>
        <p>{{ $route.params.id}}</p>
    </div>
</template>

<script>
export default ({
    validate({ params }) {
        return Number(params.id)
    },
})
</script>
