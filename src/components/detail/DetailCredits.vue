<template>
    <div class="cre">
        <h1>주요 출연진</h1>
        <div class="cre_wrap">
            <div class="credits" v-for="(cast, key) in movieCredits.cast.slice(0, 10)" :key="key">
                <div>
                    <div class="img_wrap">
                        <div class="img">
                            <img v-if="cast.profile_path" :src="'https://image.tmdb.org/t/p/w500/' + cast.profile_path"
                                alt="movieCredits.id">
                            <div v-else class="noimg">
                                <img src="../../assets/img/noimg.svg" alt="">
                            </div>
                        </div>
                    </div>
                    <div class="credit_cont">
                        <p> {{ cast.name }}</p>
                        <span> {{ cast.character }}</span>
                    </div>
                </div>
            </div>

            더보기



        </div>

        <h1 class="hide">총 출연진 & 제작진</h1>
    </div>
</template>
<script>
export default {
    props: ['movieCredits']
}
</script>
<style>
.cre {
    padding: 1rem;

    h1 {
        font-weight: 700;
        padding: 1rem 0;
    }

    .cre_wrap {
        display: flex;
        overflow: auto;
        gap: 1.5rem;
        padding: 1.5rem;
        background-color: #131313;
        border-radius: 5px 5px 0 0;

        &::-webkit-scrollbar {
            height: 7px;
        }

        &::-webkit-scrollbar-thumb {
            background-color: #888888c9;
            border-radius: 10px;
        }

        &::-webkit-scrollbar-track {
            background-color: rgb(26, 26, 26);
            border-radius: 10px;
        }

        .credits {

            >div {

                .img_wrap {

                    .img {

                        img {
                            object-fit: cover;
                            width: 150px;
                            border-radius: 2px;
                        }

                        .noimg {
                            background-color: #ebebeba9;
                            width: 150px;
                            border-radius: 1px;
                            height: 225.33px;
                            display: flex;
                            align-items: center;

                        }
                    }
                }

                .credit_cont {
                    padding: 0.5rem;
                    min-width: 170px;

                    p {
                        color: aqua;

                    }

                    span {
                        color: #888888;
                    }
                }
            }

        }
    }

}
</style>