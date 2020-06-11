<template>
    <div class="video-list">
        <ul>
            <li
                class="list-group-item"
                v-for="(video, index) in videos"
                :key="index"
                name="video"
                @click="onVideoSelect(video)"
            >
                <img :src="video.snippet.thumbnails.default.url" />
                {{ video.snippet.title }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "VideoList",
    props: {
        videos: Array,
        getSelectedVideo: Function,
    },
    mounted: function() {},
    methods: {
        onVideoSelect: function(video) {
            this.getSelectedVideo(video)
        },
    },
}
</script>

<style scoped>
li {
    display: flex;
    cursor: pointer;
}
ul {
    padding-left: 0px;
}
.video-list {
    /* position: absolute;
    right: 0px; */
}
</style>
