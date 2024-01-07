<template>
    <div id="info">
        <h2>MOVIE CLIP</h2>
        <div class="video_wrap">
            <div v-if="movieInfo.length > 0" v-for="(video, index) in movieInfo">
                <div class="videos" :key="index">
                    <iframe width="100%" :src="'https://www.youtube.com/embed/' + video.key" frameborder="0"
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                        allowfullscreen>
                    </iframe>
                    <p>{{ video.type }}</p>
                </div>
            </div>
            <div v-else>
                <h3>영상이 없습니다.</h3>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['movieInfo']
}
</script>
<style>
#info {
    padding: 0 1rem 0;

    h2 {
        font-weight: 700;
        font-size: 2rem;
        margin-bottom: 1rem;
        color: var(--red);
    }

    .video_wrap {
        display: flex;
        padding: 1.5rem;
        gap: 1.5rem;
        overflow: auto;
        background-color: #131313;
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

        >div {
            width: 50%;
            position: relative;
            max-width: 400px;
            min-width: 400px;
            border-radius: 10px;
            overflow: hidden;

            @media (max-width:800px) {
                min-width: 280px;
            }

            .videos {
                display: flex;
                width: 100%;
                padding-bottom: 56.25%;
                position: relative;

                iframe {
                    position: absolute;
                    top: 0;
                    left: 0;
                    width: 100%;
                    height: 100%;
                }

                p {
                    background-color: #00000073;
                    position: absolute;
                    bottom: 0;
                    padding: 0.3rem 0.5rem;
                    right: 0;
                }
            }
        }

    }
}
</style>
