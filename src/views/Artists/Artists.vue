<template>
    <div>
        <div class="container">
            <h2>Artists</h2>
            <div class="content">
                <div class="artist" v-for="(artist, index) in ArtistStore" :key="index" @click="artistLink(artist)">
                    <img :src="artist.imageSmall" :alt="artist.name">
                    <div class="text-mask">
                        <div class="text">{{artist.name}}</div>
                    </div>
                </div>
            </div>
        </div>
        <div style="height: 100px">

        </div>
    </div>
</template>

<script>
    import ArtistStore from '../../stores/ArtistsStore'

    export default {
        data() {
            return {
                ArtistStore: ArtistStore.data.artists
            }
        },
        methods: {
            artistLink(artist) {
                this.$router.push(`/artists/${artist.route}`);
            }
        }
    }
</script>

<style lang="scss" scoped>
    .container {
        display: grid;
        grid-template-columns: 1fr 80% 1fr;
        padding-top: 100px;
        padding-bottom: 70px;

        h2 {
            grid-column: 2/3;
            font-weight: 400;
            text-align: left;
            font-size: 2.7em;
        }

        .content {
            grid-column: 2/3;
            margin: 0;
            padding: 0;
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            grid-gap: 2em;

            .artist {
                background: #7B88D6;
                width: 100%;
                position: relative;
                overflow: hidden;
                cursor: pointer;

                img {
                    opacity: 1;
                    display: block;
                    width: 100%;
                    height: auto;
                    transition: .35s ease;
                    backface-visibility: hidden;
                    transform: scale(1);
                }

                .text-mask {
                    transition: .35s ease;
                    opacity: 0;
                    position: absolute;
                    top: 70%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    -ms-transform: translate(-50%, -50%);
                    text-align: center;

                    div {
                        font-size: 1.8em;
                    }
                }
            }

            .artist:hover img {
                opacity: 0.3;
                transform: scale(1.25);
            }

            .artist:hover .text-mask {
                opacity: 1;
            }
        }
    }

    @media only screen and (max-width: 1300px)
    {
        .container {
            .content {
                grid-template-columns: 1fr 1fr;
            }
        }
    }
</style>