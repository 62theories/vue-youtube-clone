<template>
    <div class="container">
        <SearchBar :onSearchInputChanged="onSearchInputChanged" />
        <div class="row">
            <div class="col-md-8"><VideoDetail :video="video" /></div>
            <div class="col-md-4">
                <VideoList
                    :videos="videos"
                    :getSelectedVideo="getSelectedVideo"
                />
            </div>
        </div>
    </div>
</template>

<script>
import SearchBar from "./SearchBar"
import VideoList from "./VideoList"
import VideoDetail from "./VideoDetail"
import axios from "axios"
import key from "./config"
export default {
    name: "App",
    data: function() {
        return {
            video: null,
            videos: [],
        }
    },
    components: {
        SearchBar,
        VideoList,
        VideoDetail,
    },
    methods: {
        onSearchInputChanged: function(value) {
            axios
                .get("https://www.googleapis.com/youtube/v3/search", {
                    params: {
                        key: key,
                        type: "video",
                        part: "snippet",
                        q: value,
                    },
                })
                .then((res) => {
                    this.videos = res.data.items
                })
        },
        getSelectedVideo: function(video) {
            this.video = video
        },
    },
}
</script>

<style scoped></style>
