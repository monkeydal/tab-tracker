<template>
    <div>
        <panel title="Lyrics">
            <textarea
            readonly
            v-model="song.lyrics"></textarea>
        </panel>
    </div>
</template>

<script>
import SongMetadata from './SongMetadata'
import YouTube from './YouTube'
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'

export default {
    data () {
        return {
            song: {}
        }
    },
    async mounted() {
        const songId = this.$store.state.route.params.songId
        this.song = (await SongsService.show(songId)).data
    },
    components: {
        Panel,
        SongMetadata,
        YouTube
    }
}
</script>

<style scoped>
    textarea {
        width: 100%;
        font-family: monospace;
        border: none;
        height: 600px;
        border-style: none;
        border-color: transparent;
        overflow: auto;
        padding: 20px;
    }
</style>
