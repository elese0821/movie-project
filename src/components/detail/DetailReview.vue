<template>
    <div class="review" v-for="review in movieReview" :key="review.id">
        <p>{{ review.author }}</p>
        <p>{{ review.content }}</p>
        <p>{{ review.created_at }}</p>
    </div>
</template>
<script>
export default {
    props: ['movieReview'],
}
</script>