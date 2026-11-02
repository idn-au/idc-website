<script setup lang="ts">

</script>

<template>
    <div class="mx-auto max-w-4xl text-center my-16">
        <h2><slot name="title" mdcUnwrap="p" /></h2>
        <div class="text-lg">
            <slot />
        </div>
    </div>
</template>

<style scoped>

</style>
