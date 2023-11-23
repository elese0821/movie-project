<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const movies = ref([]);

onMounted(async () => {
  // 초기 페이지 로딩 시 최신 영화를 가져옴
  await fetchMovies('latest');
});

const fetchMovies = async (category) => {
  let url = 'https://api.themoviedb.org/3/movie/popular';

  switch (category) {
    case 'latest':
      url = "https://api.themoviedb.org/3/movie/now_playing";
      break;
    case 'popular':
      url = 'https://api.themoviedb.org/3/movie/popular'
      break;
    case 'upcoming':
      url = 'https://api.themoviedb.org/3/movie/upcoming'
      break;
    case 'toprated':
      url = 'https://api.themoviedb.org/3/movie/top_rated'
      break;
  }

  try {
    const response = await axios.get(url, {
      params: {
        api_key: 'b7abb2107f0ffe0549f78058d75127f8',
        language: 'ko-KR',
        page: '1'
      }
    });
    movies.value = response.data.results;
  } catch (err) {
    console.log(err)
  }
}

const searchQuery = ref('');

const searchMovies = async () => {
  let url = 'https://api.themoviedb.org/3/search/movie';
  try {
    const response = await axios.get(url, {
      params: {
        api_key: 'b7abb2107f0ffe0549f78058d75127f8',
        language: 'ko-KR',
        page: '1',
        include_adult: 'false',
        query: searchQuery.value,  // 검색어를 query 파라미터로 사용
      }
    });
    movies.value = response.data.results;
  } catch (err) {
    console.log(err)
  }
}



</script>

<template>
  <main>
    <div class="movie__container">

      <div class="movie__inner">
        <section class="movie_search">
          <h2 class="blind">검색하기</h2>
          <input type="search" v-model="searchQuery" placeholder="검색어를 입력해주세요!">
          <button type="submit" @click="searchMovies">검색</button>
        </section>
        <div class="movie_tag">
          <ul>
            <li><a href="#" @click="fetchMovies('latest')">최신 영화</a></li>
            <li><a href="#" @click="fetchMovies('popular')">인기 영화</a></li>
            <li><a href="#" @click="fetchMovies('upcoming')">개봉 예정</a></li>
            <li><a href="#" @click="fetchMovies('toprated')">최고 평점</a></li>
          </ul>

        </div>
        <section class="movie_cont">
          <h2 class="blind">영화</h2>
          <div class="movie" v-for="movie in movies" :key="movie.id">
            <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" :alt="movie.title">
            <p class="title">{{ movie.title }}</p>
          </div>
        </section>

      </div>
    </div>
  </main>
</template>

<style lang="scss">
.movie_search {
  padding: 20px;

  input {
    border: 2px solid var(--black600);
    padding: 1rem;
    width: 100%;
    border-radius: 50px;
    background-color: transparent;
    color: #fff;
  }

  button {
    position: absolute;
    right: 25px;
    top: 24px;
    border-radius: 100%;
    width: 45px;
    height: 45px;

  }
}

.movie_tag {
  ul {
    display: flex;
    width: 100%;

    li {
      a {
        border: 1px solid var(--black);
        padding: 0.5rem 1rem;
        display: block;
        border-radius: 50px;
        margin-bottom: 20px;
        margin-right: 10px;
        margin-top: 20px;

        &:hover {
          background-color: var(--black300);

        }
      }
    }
  }
}

.movie__inner {
  .movie_cont {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .movie {
    width: 24%;
    background-color: #fff;
    margin-left: 5px;
    margin-bottom: 2%;
    background-color: #ccc;
  }
}
</style>
