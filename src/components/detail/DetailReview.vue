<template>
    <div class="review_wrap">
        <h1>리뷰</h1>
        <div v-if="movieReview.length > 0">
            <div class="reviews" v-for="review in movieReview" :key="review.id">
                <div class="review" v-if="review.content">
                    <h3><span>{{ review.author }}</span>(이)가 {{ formatDate(review.created_at) }}에 작성</h3>
                    <p>{{ review.content }}</p>
                </div>
            </div>
        </div>
        <div v-else>
            <div class="reviews">
                <div class="review">
                    <h3>작성된 리뷰가 없습니다.</h3>
                </div>
            </div>
        </div>
    </div>
</template>
<script>


export default {
    props: ['movieReview'],
    methods: {
        formatDate(dateStr) {
            const date = new Date(dateStr);
            const year = date.getFullYear();
            const month = date.getMonth() + 1;
            const day = date.getDate();
            return `${year}년 ${month}월 ${day}일`;
        }
    }
}
</script>

<style>
.review_wrap {
    padding: 1rem;

    h1 {
        font-weight: 700;
        margin-bottom: 1rem;
    }

    .reviews {
        .review {
            background-color: #2929295e;
            padding: 1rem;
            margin-bottom: 1rem;

            h3 {
                margin-bottom: 0.5rem;
            }

            p {
                color: #929292;
            }
        }
    }
}
</style>