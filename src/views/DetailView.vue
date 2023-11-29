<script>
import { ref, onMounted } from "vue";
import { useRoute } from 'vue-router';

export default {
    props: ['movieId'],
    setup() {

        const movieInfo = ref([]);
        const route = useRoute();
        const movieId = route.params.movieId;

        const movieInfoFetch = () => {
            const apiKey = import.meta.env.VITE_API_KEY;
            const url = `https://api.themoviedb.org/3/movie/${movieId}?language=ko-KR&api_key=${apiKey}`

            fetch(url)
                .then((response) => response.json())
                .then((res) => {
                    console.log(res);
                    movieInfo.value = res;
                })
                .catch((err) => {
                    console.log(err);
                })
        }

        onMounted(() => {
            movieInfoFetch();
        })

        return { movieInfo };
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
            <div class="header__intro"
                :style="movieInfo.backdrop_path ? {
                    backgroundImage: 'url(https://image.tmdb.org/t/p/w500' + movieInfo.backdrop_path) '} : {}">
                <div class="container">
                    <div class="left play__icon">
                        <a href="#">
                            <img :src="'https://image.tmdb.org/t/p/w500' + movieInfo.poster_path"
                                :alt="movieInfo.original_title">
                        </a>
                    </div>
                    <div class="right">
                        <h2>{{ movieInfo.title }}</h2>
                        <p class="desc">
                            {{ movieInfo.overview }}
                        </p>
                        <p class="date">개봉 : {{ movieInfo.release_date }}</p>
                        <p class="average">평점 : {{ movieInfo.vote_average }}</p>
                    </div>
                </div>
            </div>
        </div>
    </header>
    <main id="main">

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