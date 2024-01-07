<template>
    <div class="review_wrap">
        <h1>REVIEWS</h1>
        <div v-if="movieReview.length > 0">
            <div class="reviews" v-for="review in movieReview" :key="review.id">
                <div class="review" v-if="review.content">
                    <h3><span>{{ review.author }}</span>(이)가 {{ formatDate(review.created_at) }}에 작성</h3>
                    <p class="content">{{ review.content }}</p>
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
    },
    data() {
        return {
            showFullText: false,
        }
    },
}
</script>

<style>
.review_wrap {
    padding: 1rem;

    h1 {
        font-weight: 700;
        margin-bottom: 1rem;
        color: var(--red);
    }

    .reviews {
        position: relative;

        .review {
            background-color: #131313;
            padding: 1rem;
            margin-bottom: 1rem;
            border-radius: 10px;

            h3 {
                margin-bottom: 0.5rem;
            }

            .content {
                color: #929292;
                line-height: 1.6;
                overflow-y: auto;
                max-height: 100px;

                &::-webkit-scrollbar {
                    width: 5px;
                }

                &::-webkit-scrollbar-thumb {
                    background-color: #88888848;
                    border-radius: 10px;
                }

                &::-webkit-scrollbar-track {
                    background-color: rgba(59, 59, 59, 0.61);
                    border-radius: 10px;
                }
            }

            button {
                margin-top: 0.2rem;
                background-color: transparent;
                padding: 0.5rem;
                cursor: pointer;
                position: relative;
                color: #bbbbbb;
                left: 50%;
                transform: translateX(-50%);
            }
        }
    }
}
</style>