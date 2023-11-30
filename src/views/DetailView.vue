<script>
import axios from 'axios';
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";

import DetailIntro from "../components/detail/DetailIntro.vue";
import DetailInfo from "../components/detail/DetailInfo.vue";
import DetailReview from "../components/detail/DetailReview.vue";
import DetailCredits from "../components/detail/DetailCredits.vue";

export default {
    name: "MovieDetailPage",

    components: {
        DetailIntro,
        DetailInfo,
        DetailReview,
        DetailCredits
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

            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieBasic.value = resMovieBasic.data;
                console.log(resMovieBasic.data);

                const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}videos?language=${language}&api_key=${apiKey}`);
                movieInfo.value = resMovieInfo.data;
                console.log(resMovieInfo.data);

                const resMovieReview = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/reviews?language=en-US&page=${page}&api_key=${apiKey}`);
                movieReview.value = resMovieReview.data.results;
                console.log(resMovieReview.data.results);

                const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`);
                movieCredits.value = resMovieCredits.data.cast;
                console.log(resMovieCredits.data);
            } catch (err) {
                console.log(err);
            }
        });
        return { movieBasic, movieInfo, movieReview, movieCredits }
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
        <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
        <DetailReview v-if="movieReview" :movieReview="movieReview" />
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