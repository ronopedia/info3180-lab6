<script>
import NewsList from '@/components/NewsList.vue'

export default {
    data() {
        return {};
    },
    components: { NewsList }
}
</script>

<template>
    <div class="news container">
        <h1 class="text-center text-success fw-bold"> News </h1>
        <NewsList />
    </div>
</template>

<style>
/* Add any component specific styles here */
</style>
