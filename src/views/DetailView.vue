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
                style="backgroundImage:url(https://image.tmdb.org/t/p/w500/kjQBrc00fB2RjHZB3PGR4w9ibpz.jpg)">
                <div class="container">
                    <div class="left play__icon">
                        <a href="#">
                            <img src="https://image.tmdb.org/t/p/w500/vFsSluuzqxR46Ils9ib52ItdE9u.jpg" alt="dd">
                        </a>
                    </div>
                    <div class="right">
                        <h2>{{ movieInfo.original_title }}</h2>
                        <p class="desc">
                            인류를 지키기 위해 만들어진 AI가 LA에 핵폭탄을 터뜨린 후, 인류와 AI 간의 피할 수 없는 전쟁이 시작된다. 전직 특수부대 요원 ‘조슈아’는
                            실종된 아내의 단서를 얻을지도 모른다는 생각에 전쟁을 끝내기 위한 인류의 작전에 합류한다. 인류를 위협할 강력한 무기와 이를 창조한 ‘창조자’를 찾아 나서고, 그 무기가
                            아이 모습의 AI 로봇 '알피'란 사실을 알게 되는데… 인간적인가, 인간의 적인가? 10월, SF 블록버스터의 신세계가 펼쳐진다!
                        </p>
                        <p class="date">개봉 : 2023-09-27</p>
                        <p class="average">평점 : 7.1</p>
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