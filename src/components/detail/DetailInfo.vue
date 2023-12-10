<template>
    <div id="info">
        <h2>영상</h2>
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
    padding: 1rem;

    h2 {
        font-weight: 700;
        font-size: 2rem;
        margin-bottom: 1rem;
    }

    .video_wrap {
        display: flex;
        padding: 1.5rem;
        gap: 1.5rem;
        overflow: auto;
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

        >div {
            width: 50%;
            position: relative;
            min-width: 500px;


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
