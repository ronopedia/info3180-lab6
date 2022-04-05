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
        <h2 class="text-center text-success fw-bold"> Latest News </h2>
        <NewsList />
    </div>
</template>

<style>
/* Add any component specific styles here */
</style>