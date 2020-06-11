<template>
    <div class="details embed-responsive embed-responsive-16by9">
        <iframe v-if="video" class="embed-responsive-item" :src="getVideoURL" />
        <iframe v-else src="" />
    </div>
</template>

<script>
export default {
    name: "VideoDetail",
    props: {
        video: Object,
    },
    computed: {
        getVideoURL: function() {
            return `https://www.youtube.com/embed/${this.video.id.videoId}`
        },
    },
}
</script>

<style scoped>
.details {
    margin-top: 10px;
    /* margin-left: 40px; */
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
}
</style>
