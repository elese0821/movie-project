<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import HeaderSection from '@/components/section/HeaderSection.vue';
import FooterSection from '@/components/section/FooterSection.vue';

const movies = ref([]);
const searchKeyword = ref('');
const currentCategory = ref('latest');

const fetchMovies = async (category, event) => {
  if (event) event.preventDefault();
  currentCategory.value = category;
  // console.log(currentCategory)

  let url = 'https://api.themoviedb.org/3/movie/popular';

  switch (category) {
    case 'latest':
      url = 'https://api.themoviedb.org/3/movie/now_playing';
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

const serachMovies = async () => {
  try {
    const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: '9278d13f704ad0fe53c2263b692efd89',
        language: 'ko-KR',
        query: searchKeyword.value
      }
    });
    movies.value = response.data.results;
  } catch (err) {
    console.error(err);
  }
}

onMounted(async () => {
  await fetchMovies('latest');
});
</script>

<template>
  <HeaderSection />
  <div class="info_box" style="backgroundImage: url(https://image.tmdb.org/t/p/w500/kjQBrc00fB2RjHZB3PGR4w9ibpz.jpg)">
    <div class="container">
      <div class="left play__icon">
        <a href="#" class="info_poster">
          <img src='https://image.tmdb.org/t/p/w500//vFsSluuzqxR46Ils9ib52ItdE9u.jpg' alt="dd">
        </a>
      </div>
      <div class="right">
        <div>
          <div class="detail_tit">
            <h2>크리에이터</h2>
            <p>The Creator, 2023</p>
          </div>
          <div class="detail_cont">
            <div class="inner_cont">
              <dl class="list_cont">
                <dt>개봉</dt>
                <dd class="dd_type">
                  2023-09-27
                </dd>
              </dl>

              <dl class="list_cont">
                <dt>장르</dt>
                <dd class="dd_type">
                  <span>
                    액션/모험/드라마
                  </span>
                </dd>
              </dl>

              <dl class="list_cont">
                <dt>국가</dt>
                <dd>Canada</dd>
              </dl>

              <dl class="list_cont">
                <dt>러닝타임</dt>
                <dd>134분</dd>
              </dl>

            </div>

            <div class="inner_cont right_cont">
              <dl class="list_cont">
                <dt>평점 </dt>
                <dd>
                  <span class='ico_movie ico_star'>
                  </span>
                  7.1
                </dd>
              </dl>
            </div>
          </div>

        </div>
        <dl class="list_cont last_cont">
          <dt>주요정보</dt>
          <dd class="line8">인류를 지키기 위해 만들어진 AI가 LA에 핵폭탄을 터뜨린 후, 인류와 AI 간의 피할 수 없는 전쟁이 시작된다. 전직 특수부대 요원
            ‘조슈아’는 실종된 아내의 단서를 얻을지도 모른다는 생각에 전쟁을 끝내기 위한 인류의 작전에 합류한다. 인류를 위협할 강력한 무기와 이를 창조한 ‘창조자’를 찾아
            나서고, 그 무기가 아이 모습의 AI 로봇 '알피'란 사실을 알게 되는데… 인간적인가, 인간의 적인가? 10월, SF 블록버스터의 신세계가 펼쳐진다!</dd>
        </dl>
      </div>
    </div>
  </div>
  <main id="main" role="main">
    <div class="container">
      <div class="movie__inner">
        <div class="movie__tag">
          <ul>
            <li>
              <a href="#" :class="{ active: currentCategory === 'latest' }" @click="fetchMovies('latest', $event)">최신
                영화</a>
            </li>
            <li>
              <a href="#" :class="{ active: currentCategory === 'popular' }" @click="fetchMovies('popular', $event)">인기
                영화</a>
            </li>
            <li>
              <a href="#" :class="{ active: currentCategory === 'upcoming' }" @click="fetchMovies('upcoming', $event)">개봉
                예정</a>
            </li>
            <li>
              <a href="#" :class="{ active: currentCategory == 'toprated' }" @click="fetchMovies('toprated', $event)">최고
                평점</a>
            </li>
          </ul>
        </div>
        <!-- //movie__tag -->
        <section class="movie__search">
          <h2 class="blind">검색하기</h2>
          <input type="search" v-model="searchKeyword" placeholder="검색어를 입력해주세요!" @keyup.enter="serachMovies">
          <button type="submit" @click="serachMovies">검색</button>
        </section>
        <!-- //movie__search -->

        <section class="movie__cont">
          <h2 class="blind">영화</h2>
          <div class="movie play__icon" v-for="movie in movies" :key="movie.id">
            <a :href="'/detail/' + movie.id">
              <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" :alt="movie.title">
            </a>
          </div>
        </section>
        <!-- //movie__cont -->

      </div>
    </div>
  </main>
  <FooterSection />
</template>
<style lang="scss">
html {
  overflow: auto;
  min-height: 100vh;

  &::-webkit-scrollbar {
    width: 10px;
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

.movie__search {
  margin: 0 0 2rem;
  position: relative;
  padding: 0 1rem;

  @media (max-width:500px) {
    margin: 0;
  }

  input {
    padding: 1rem 2rem;
    width: 100%;
    border-radius: 50px;
    background-color: #ffffff8a;

    &:active,
    &:focus {
      outline: none;
    }

    &::placeholder {
      color: #2e2e2ecb;
    }

    @media (max-width:500px) {
      font-size: 0.9rem;
      padding: 0.8rem;
    }
  }

  button {
    position: absolute;
    right: 1.4rem;
    top: 0.3rem;
    width: 40px;
    height: 40px;
    background-color: var(--black);
    color: #fff;
    border-radius: 50%;
    cursor: pointer;
    font-size: 14px;
    transition: background-color 0.3s;

    @media (max-width:500px) {
      font-size: 0.8rem;
      height: 29px;
      border-radius: 15px;
    }

    &:hover {
      background-color: #00000075;
    }
  }
}

.movie__tag {
  ul {
    display: flex;
    margin: 0 1rem;

    @media(max-width:500px) {
      font-size: 0.8rem;
    }

    li {
      a {
        border: 1px solid var(--black);
        padding: 0.5rem 1.3rem;
        display: inline-block;
        border-radius: 50px;
        margin-bottom: 20px;
        margin-right: 10px;
        margin-top: 20px;
        transition: all 0.3s;
        background-color: #ffffff0a;

        @media(max-width:500px) {
          padding: 0.5rem;
          margin: 0.5rem 0;
        }

        &:hover,
        &.active {
          color: var(--red);
          background-color: #ffffff18;
        }
      }
    }
  }
}

.movie__cont {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 1rem;

  .movie {
    width: 24%;
    margin-bottom: 1.5%;
    background-color: #0000006c;
    display: flex;
    align-items: center;

    @media (max-width:800px) {
      width: 32%;
    }

    @media (max-width:500px) {
      width: 49%;
    }
  }
}
</style>
