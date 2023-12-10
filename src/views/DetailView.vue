<script>
import axios from 'axios';
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";

import DetailIntro from '@/components/detail/DetailIntro.vue';
import DetailReview from '@/components/detail/DetailReview.vue';
import DetailCredits from '@/components/detail/DetailCredits.vue';
import DetailInfo from '@/components/detail/DetailInfo.vue';
import Similarvideo from '@/components/detail/Similarvideo.vue';

export default {
    name: "MovieDetailPage",
    props: ['movieId'],

    components: {
        DetailIntro,
        DetailReview,
        DetailCredits,
        DetailInfo,
        Similarvideo,
    },

    setup() {
        const movieBasic = ref(null);
        const movieInfo = ref(null);
        const movieReview = ref(null);
        const movieCredits = ref(null);
        const similar = ref(null);

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
                movieInfo.value = resMovieInfo.data;

                const resMovieReview = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/reviews?language=en-US&page=${page}&api_key=${apiKey}`);
                movieReview.value = resMovieReview.data.results;

                const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`);
                movieCredits.value = resMovieCredits.data;

                const resSimilar = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/similar?language=${language}&page=${page}&api_key=${apiKey}`);
                similar.value = resSimilar.data;

            } catch (err) {
                console.log(err);
            }
        });
        return { movieBasic, movieCredits, movieReview, movieInfo, similar }
    }
}
</script>
<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1>Movie Star</h1>
                <nav>
                    <ul>
                        <li><a href="#">웹쓰 영화 Top10</a></li>
                        <li><a href="#">코딩 영화 Top10</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
    <main id="main">
        <DetailIntro v-if="movieBasic" :movieBasic="movieBasic" />
        <DetailCredits v-if="movieCredits" :movieCredits="movieCredits" />
        <DetailReview v-if="movieReview" :movieReview="movieReview" />
        <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
        <Similarvideo v-if="similar" :similar="similar" />
    </main>
</template>

<style lang="scss">
.movie__cont {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;

    .movie {
        width: 24%;
        margin-bottom: 1.5%;
        background-color: #ccc;
    }
}
</style>