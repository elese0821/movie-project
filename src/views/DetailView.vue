<script>
import axios from 'axios';
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";

import DetailIntro from '@/components/detail/DetailIntro.vue';
import DetailReview from '@/components/detail/DetailReview.vue';
import DetailCredits from '@/components/detail/DetailCredits.vue';
import DetailInfo from '@/components/detail/DetailInfo.vue';
import HeaderSection from '../components/section/HeaderSection.vue';

export default {
    name: "MovieDetailPage",
    props: ['movieId'],

    components: {
        DetailIntro,
        DetailReview,
        DetailCredits,
        DetailInfo,
        HeaderSection
    },

    setup() {
        const movieBasic = ref(null);
        const movieInfo = ref(null);
        const movieReview = ref(null);
        const movieCredits = ref(null);

        const route = useRoute();

        onMounted(async () => {
            const movieId = route.params.movieId;
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = "ko-KR";
            const page = "1"
            // 
            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieBasic.value = resMovieBasic.data;

                const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/videos?api_key=${apiKey}&language=${language}`);
                movieInfo.value = resMovieInfo.data.results;

                const resMovieReview = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/reviews?language=en-US&page=${page}&api_key=${apiKey}`);
                movieReview.value = resMovieReview.data.results;

                const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`);
                movieCredits.value = resMovieCredits.data;
            } catch (err) {
                console.log(err);
            }
        });
        return {
            movieBasic, movieCredits, movieReview, movieInfo,
        }
    }
}
</script>
<template>
    <HeaderSection />
    <main id="main">
        <DetailIntro v-if="movieBasic" :movieBasic="movieBasic" />
        <DetailCredits v-if="movieCredits" :movieCredits="movieCredits" />
        <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
        <DetailReview v-if="movieReview" :movieReview="movieReview" />
    </main>
</template>