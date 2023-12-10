<template>
    <div class="info_box"
        :style="{ backgroundImage: 'url(https://image.tmdb.org/t/p/w500/' + movieBasic.backdrop_path + ')' }">
        <div class="container">
            <div class="left play__icon">
                <a href="#" class="info_poster">
                    <img :src="'https://image.tmdb.org/t/p/w500/' + movieBasic.poster_path" alt="dd">
                </a>
            </div>
            <div class="right">
                <div class="detail_tit">
                    <h2>{{ movieBasic.title }}</h2>
                    <p>{{ movieBasic.original_title }}, {{ movieBasic.release_date.substr(0, 4) }}</p>
                </div>

                <div class="detail_cont">
                    <div class="inner_cont">
                        <dl class="list_cont">
                            <dt>개봉</dt>
                            <dd class="dd_type">
                                {{ movieBasic.release_date }}
                            </dd>
                        </dl>


                        <dl class="list_cont">
                            <dt>장르</dt>
                            <dd class="dd_type">
                                <span v-for="(movie, index) in movieBasic.genres" :key="index">
                                    {{ movie.name }}<i v-if="index !== movieBasic.genres.length - 1">/</i>
                                </span>
                            </dd>
                        </dl>

                        <dl class="list_cont">
                            <dt>국가</dt>
                            <dd>{{ movieBasic.production_countries[0].name }}</dd>
                        </dl>
                        <dl class="list_cont">
                            <dt>등급</dt>
                            <dd>2023-09-27</dd>
                        </dl>

                        <dl class="list_cont">
                            <dt>러닝타임</dt>
                            <dd>{{ movieBasic.runtime }}분</dd>
                        </dl>

                    </div>

                    <div class="inner_cont right_cont">
                        <dl class="list_cont">
                            <dt>평점 </dt>
                            <dd>
                                <span class='ico_movie ico_star'>
                                </span>
                                {{ (Math.round(movieBasic.vote_average * 10) / 10).toFixed(1) }}
                                <span class="font_color">({{ movieBasic.vote_count }})</span>
                            </dd>
                        </dl>


                    </div>

                </div>


                <dl class="list_cont last_cont" v-if="movieBasic.overview">
                    <dt>주요정보</dt>
                    <dd class="line8">{{ movieBasic.overview }}</dd>
                </dl>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: ['movieBasic'],
}

</script>
<style>
.info_box {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    position: relative;
    padding: 30px;

    &::before {
        content: '';
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-color: #00000032;
        backdrop-filter: blur(7px);
        z-index: 1;
    }

    .container {
        display: flex;
        justify-content: flex-start;
        position: relative;
        z-index: 10;

        .left {
            width: 350px;

        }

        .right {
            width: calc(100% - 390px);
            background-color: rgba(0, 0, 0, .6);
            padding: 2rem;
            letter-spacing: 0.05rem;

            .detail_tit {

                h2 {
                    font-size: 1.8rem;
                    font-weight: 700;
                }
            }

            .detail_cont {
                display: flex;
                align-items: flex-start;
                margin-top: 2rem;

                .right_cont {
                    margin-left: 2rem;
                }

                .inner_cont {
                    display: table;
                    max-width: 60%;

                    .list_cont {
                        line-height: 1.7;
                        display: table-row;

                    }

                }

            }

            .last_cont {
                margin-top: 1rem;

                dt {
                    display: flex;
                    background-color: #c93131;
                    border-radius: 10px;
                    justify-content: center;
                    align-items: center;
                    margin-bottom: 0.5rem;
                    color: #fff;
                    padding-right: 0;
                }

                .line8 {
                    line-height: 1.8;
                    overflow: auto;
                    text-overflow: ellipsis;
                    display: -webkit-box;
                    -webkit-line-clamp: 6;
                    -webkit-box-orient: vertical;

                    &::-webkit-scrollbar {
                        width: 10px;
                    }

                    &::-webkit-scrollbar-thumb {
                        background-color: #888888;
                        border-radius: 2px;
                    }

                    &::-webkit-scrollbar-track {
                        background-color: rgb(15, 15, 15);
                        border-radius: 2px;
                    }

                }

            }
        }
    }
}



dt {
    max-width: 100px;
    font-weight: normal;
    white-space: nowrap;
    display: table-cell;
    color: rgb(122, 122, 122);
    padding-right: 1rem;

}

dd {
    display: table-cell;

    .star {
        width: 20px;
        height: 20px;
    }


    .font_color {
        color: rgb(128, 128, 128)
    }

}


.ico_movie,
.ico_logo {
    display: inline-block;
    overflow: hidden;
    font-size: 0;
    line-height: 0;
    text-indent: -9999px;
    vertical-align: top;
    background: url('../../assets/img/ico_movie.png') no-repeat 0 0;
}

.ico_star {
    width: 13px;
    height: 13px;
    margin: 6px 2px 0 0;
    background-position: -200px -40px;
}
</style>