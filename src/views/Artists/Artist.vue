<template>
    <div class="artistPage" :style="{backgroundImage: 'url('+artistImg+')'}">
        <div class="artistImage">
            <!-- <img :src="artistImg"> -->
            <div class="name">
                {{Artists[name].name}}
                {{backgroundImage}}
            </div>
        </div>
        <div class="container">
            <div class="content">
                <div class="text">
                    {{Artists[name].text1}}
                </div>
                <br>
                <br>
                <div class="text">
                    {{Artists[name].text2}}
                </div>
                <div class="book">
                    <div class="text">
                        Book now!
                    </div>
                </div>
                <iframe scrolling="no" frameborder="no" allow="autoplay" :src="soundcloudLink"></iframe>
            </div>
        </div>
    </div>
</template>

<script>
    import ArtistStore from '../../stores/ArtistsStore'

    export default {
        data() {
            return {
                Artists: ArtistStore.data.artists,
                name: this.$route.params.name
            }
        },
        computed: {
            artistImg() {
                return this.Artists[this.name].imageBig;
            },
            soundcloudLink() {
                const id = this.Artists[this.name].soundcloud;
                return `https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/${id}&color=%23ff5500&auto_play=false&hide_related=false&show_comments=false&show_user=true&show_reposts=false&show_teaser=true`;
            }
        }
    }
</script>

<style lang="scss" scoped>
    .artistPage {
        background-repeat: no-repeat;
        background-size: 100%;

        .artistImage {
            width: 100%;
            overflow: hidden;

            .name {
                font-size: 2.5em;
                letter-spacing: 0.1em;
                margin-top: 200px;
            }
        }

        .container {
            display: grid;
            grid-template-columns: 10% 1fr 10%;
            margin: 0;
            padding: 0;
            margin-top: 100px;

            .content {
                margin: 0;
                padding: 0;
                grid-column: 2/3;

                .text {
                    font-size: 1.2em;
                    text-align: left;
                }

                iframe {
                    margin-top: 80px;
                    height: 180px;
                    width: 100%;
                }

                .book {
                    margin-top: 80px;
                    display: flex;
                    justify-content: flex-end;
                }
            }
        }
    }

    @media only screen and (max-width: 800px) {
        .artistPage {
            .artistImage {
                .name {
                    margin-top: 100px;
                }
            }
        }
    }
</style>