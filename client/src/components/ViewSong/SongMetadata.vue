<template>
    <div>
        <panel title="Song Metadata">
            <v-layout>
                <v-flex xs6>
                    <div class="song-title">
                        {{song.title}}
                    </div>
                    <div class="song-artist">
                        {{song.artist}}
                    </div>
                    <div class="song-genre">
                        {{song.genre}}
                    </div>

                    <v-btn dark class="cyan" @click="navigateTo({
                        name: 'song-edit',
                        params: {
                            songId: song.id
                        }
                    })"> View </v-btn>
                </v-flex>

                <v-flex xs6>
                    <img :src="song.albumImageUrl" alt="Album Image" class="album-image">
                    <br>
                    {{song.album}}
                </v-flex>
            </v-layout>
        </panel>
    </div>
</template>

<script>
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'

export default {
    props: ['song'],
    components: {
        Panel
    },
    methods: {
        navigateTo (route) {
            this.$router.push(route)
        }
    }
}
</script>

<style scoped>
    .song {
        padding: 20px;
        height: 330px;
        overflow: hidden;
    }
    .song-title {
        font-size: 30px;
    }
    .song-artist {
        font-size: 24px;
    }
    .song-genre {
        font-size: 18px;
    }
    .album-image {
        width: 70%;
        margin: 0 auto;
    }
</style>
