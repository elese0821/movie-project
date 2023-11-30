<template>
    <div class="header__intro"
        :style="{ backgroundImage: 'url(https://image.tmdb.org/t/p/w500/' + movieBasic.backdrop_path + ')' }">
        <div class="container">
            <div class="left play__icon">
                <a href="#">
                    <img :src="'https://image.tmdb.org/t/p/w500/' + movieBasic.poster_path" alt="dd">
                </a>
            </div>
            <div class="right">
                <h2>{{ movieBasic.title }}</h2>
                <p class="desc">
                    {{ movieBasic.tagline }}<br />
                    <br />
                    줄거리 :
                    {{ movieBasic.overview }}
                </p>
                <p class="date">개봉 : 2023-09-27</p>
                <p class="average">평점 : 7.1</p>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: ['movieBasic'],
}
</script>