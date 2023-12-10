<template>
    <div v-for="(video, index) in movieInfo">
        <div v-if="video.key" :key="index">
            <iframe width="560" height="315" :src="'https://www.youtube.com/embed/' + video.key" frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen>
            </iframe>
        </div>
    </div>
</template>

<script>
export default {
    props: ['movieInfo']
}
</script>
