<template>
    <div class="cre">
        <div class="credits" v-for="actor in movieCredits">

            {{ actor.character }}<br />
            {{ actor.name }}<br />
            <div class="img_wrap">
                <div class="img">
                    <img :src="'https://image.tmdb.org/t/p/w500/' + actor.profile_path" alt="dd">
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['movieCredits']
}
</script>
<style>
.cre {
    display: flex;
    width: 100%;
    overflow: hidden;
}
</style>