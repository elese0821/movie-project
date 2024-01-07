<template>
    <div class="cre">
        <h1>CAST</h1>
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
        padding: 0 0 1rem;
        color: var(--red);
    }

    .cre_wrap {
        display: flex;
        overflow: auto;
        gap: 0.5rem;
        padding: 1rem;
        background-color: #0202024f;
        border-radius: 10px;

        &::-webkit-scrollbar {
            height: 5px;
        }

        &::-webkit-scrollbar-thumb {
            background-color: #88888848;
            border-radius: 10px;
        }

        &::-webkit-scrollbar-track {
            background-color: rgba(59, 59, 59, 0.61);
            border-radius: 10px;
        }

        .credits {

            >div {
                display: flex;
                flex-direction: column;
                height: 100%;

                .img_wrap {
                    height: calc(100% - 40px);

                    .img {
                        height: 100%;
                        display: flex;
                        overflow: hidden;
                        align-items: end;
                        min-width: 100px;
                        border-radius: 10px;

                        img {
                            object-fit: cover;
                            width: 100%;
                            height: 100%;
                        }

                        .noimg {
                            background-color: #ebebeb00;

                            img {
                                transform: scale(1.2);
                                opacity: 0.2;
                            }
                        }
                    }
                }

                .credit_cont {
                    padding: 0.5rem;
                    font-size: 0.7rem;
                    word-break: keep-all;
                    height: 40px;
                    display: flex;
                    flex-direction: column;
                    overflow: hidden;
                    text-overflow: ellipsis;
                    display: -webkit-box;
                    -webkit-line-clamp: 2;
                    -webkit-box-orient: vertical;

                    &::-webkit-scrollbar {
                        width: 5px;
                    }

                    &::-webkit-scrollbar-thumb {
                        background-color: #88888818;
                        border-radius: 10px;
                    }

                    &::-webkit-scrollbar-track {
                        background-color: rgb(26, 26, 26);
                        border-radius: 10px;
                    }

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