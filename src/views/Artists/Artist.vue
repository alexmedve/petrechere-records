<template>
    <div class="container">
        <div class="content">
            {{ArtistStore[name].text}}
        </div>
    </div>
</template>

<script>
    import ArtistStore from '../../stores/ArtistsStore'

    export default {
        data() {
            return {
                ArtistStore: ArtistStore.data.artists,
                name: this.$route.params.name,
            }
        }
    }
</script>

<style lang="scss" scoped>
    .container {
        display: grid;
        grid-template-columns: 10% 1fr 10%;
        margin: 0;
        padding: 0;
        .content {
            margin: 0;
            padding: 0;
            grid-column: 2/3;

            img {
                padding-top: 50px;
                max-width: 100%;
            }

            h2 {
                text-align: left;
                font-weight: 500;
                font-size: 2.2em;
            }

            p {
                text-align: left;
                font-size: 1.5em;
                font-weight: 300 !important;
            }
        }
    }
</style>