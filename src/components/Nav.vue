<template>
    <div>
        <nav>
            <div>
                <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="79.041"
                    height="49" viewBox="0 0 79.041 49" @click="navFunction">
                    <defs>
                        <filter id="Path_2" x="29.194" y="0" width="49.847" height="25" filterUnits="userSpaceOnUse">
                            <feOffset dx="7" dy="3" input="SourceAlpha" />
                            <feGaussianBlur stdDeviation="3.5" result="blur" />
                            <feFlood flood-opacity="0.161" />
                            <feComposite operator="in" in2="blur" />
                            <feComposite in="SourceGraphic" />
                        </filter>
                        <filter id="Path_3" x="14.121" y="12" width="64.92" height="25" filterUnits="userSpaceOnUse">
                            <feOffset dx="7" dy="3" input="SourceAlpha" />
                            <feGaussianBlur stdDeviation="3.5" result="blur-2" />
                            <feFlood flood-opacity="0.161" />
                            <feComposite operator="in" in2="blur-2" />
                            <feComposite in="SourceGraphic" />
                        </filter>
                        <filter id="Path_4" x="0" y="24" width="79.041" height="25" filterUnits="userSpaceOnUse">
                            <feOffset dx="7" dy="3" input="SourceAlpha" />
                            <feGaussianBlur stdDeviation="3.5" result="blur-3" />
                            <feFlood flood-opacity="0.161" />
                            <feComposite operator="in" in2="blur-3" />
                            <feComposite in="SourceGraphic" />
                        </filter>
                    </defs>
                    <g id="Group_1" data-name="Group 1" transform="translate(-1720.459 -45.577)">
                        <g transform="matrix(1, 0, 0, 1, 1720.46, 45.58)" filter="url(#Path_2)">
                            <path id="Path_2-2" data-name="Path 2" d="M1780.164,52.077h-24.847"
                                transform="translate(-1720.62 -42.58)" fill="none" stroke="#fff" stroke-linecap="round"
                                stroke-width="4" />
                        </g>
                        <g transform="matrix(1, 0, 0, 1, 1720.46, 45.58)" filter="url(#Path_3)">
                            <path id="Path_3-2" data-name="Path 3" d="M1795.238,52.077h-39.92"
                                transform="translate(-1735.7 -30.58)" fill="none" stroke="#fff" stroke-linecap="round"
                                stroke-width="4" />
                        </g>
                        <g transform="matrix(1, 0, 0, 1, 1720.46, 45.58)" filter="url(#Path_4)">
                            <path id="Path_4-2" data-name="Path 4" d="M1809.359,52.077h-54.041"
                                transform="translate(-1749.82 -18.58)" fill="none" stroke="#fff" stroke-linecap="round"
                                stroke-width="4" />
                        </g>
                    </g>
                </svg>
            </div>
        </nav>
        <transition name="nav-anim" style="position: absolute;">
            <div v-if="navOpen" class="nav-open">
                <div class="nav-header">
                    <h3 @click="customRouter">Petrechere</h3>
                    <svg xmlns="http://www.w3.org/2000/svg" width="47.863" height="47.862" viewBox="0 0 47.863 47.862"
                        @click="navFunction">
                        <g id="Group_2" data-name="Group 2" transform="translate(-1717.304 -96.672)">
                            <path id="Path_8" data-name="Path 8" d="M3683.339,120.5l42.206,42.206"
                                transform="translate(-1963 -21)" fill="none" stroke="#333740" stroke-linecap="round"
                                stroke-width="4" />
                            <path id="Path_9" data-name="Path 9" d="M3725.544,120.5l-42.206,42.206"
                                transform="translate(-1963.206 -21)" fill="none" stroke="#333740" stroke-linecap="round"
                                stroke-width="4" />
                        </g>
                    </svg>
                </div>
                <div class="nav-content">
                    <div @click="customRouter">Events</div>
                    <div @click="customRouter">Artists</div>
                    <div @click="customRouter">Contact</div>
                    <div @click="customRouter">Radio</div>
                </div>
            </div>
        </transition>
        <transition name="mask-anim">
            <div v-if="navOpen" class="nav-mask"></div>
        </transition>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                navOpen: false
            }
        },
        methods: {
            close(e) {
                if (!this.$el.contains(e.target)) {
                    this.navOpen = false
                }
            },
            customRouter(e) {
                this.navOpen = false;
                let path = e.toElement.innerText;
                path = path.toLowerCase();
                let currentPath = this.$route.name;
                if(path === 'petrechere')
                {
                    path = 'home';
                }
                if(path !== currentPath)
                {
                    this.$router.push('/'+path);
                    document.body.style.overflow = "auto";
                }
            },
            navFunction()
            {
                this.navOpen = !this.navOpen;
                if(this.navOpen == true)
                {
                    document.body.style.overflow = "hidden";
                }
                else
                {
                    document.body.style.overflow = "auto";
                }
            }
        },
        mounted() {
            document.addEventListener('click', this.close);
        },
        beforeDestroy() {
            document.removeEventListener('click', this.close);
        }
    }
</script>

<style lang="scss" scoped>
    $dark: #333740;
    $white: #ffffff;
    $secondary: #7B88D6;

    nav {
        position: fixed;
        top: 0;
        min-height: 5vh;
        width: 100%;
        margin: auto;
        padding: 35px 0px;
        z-index: 1000;
        display: grid;
        grid-template-columns: 1fr 90% 1fr;
        // animation-name: nav-load;
        // animation-duration: 0.35s;
        // opacity: 0;
        // animation-delay: 1s;
        // animation-fill-mode: forwards;

        div {
            grid-column: 2/3;

            svg {
                display: block;
                float: right;
                cursor: pointer;
                color: $dark;
            }
        }
    }

    .nav-open {
        width: 60%;
        height: 100vh;
        position: fixed;
        background-color: $white;
        z-index: 1000;
        right: 0;
        padding: 0;

        .nav-header {
            margin: 0 10%;
            margin-top: 35px;
            display: flex;
            justify-content: space-between;
            height: auto;

            h3 {
                cursor: pointer;
                font-size: 2.2em;
                margin: 0;
                color: $dark;
            }

            svg {
                cursor: pointer;
                height: 100%;
            }
        }

        .nav-content {
            margin: 0 10%;
            margin-top: 80px;
            display: grid;
            grid-template-columns: 1fr;
            grid-gap: 1.5em;

            div {
                cursor: pointer;
                margin: 0 20%;
                font-size: 2em;
                border-bottom: 2px solid $secondary;
                padding-bottom: 15px;
                color: $dark;
            }
        }
    }

    .nav-mask {
        height: 100vh;
        margin: 0;
        width: 60%;
        height: 100vh;
        right: 0;
        z-index: 900;
        position: fixed;
        background-color: $secondary;
    }

    .nav-anim-enter-active {
        animation: nav-anim .35s;
        animation-timing-function: ease-out;
    }

    .nav-anim-leave-active {
        animation: nav-anim .35s reverse;
        animation-timing-function: ease-out;
    }

    @keyframes nav-anim {
        0% {
            transform: translateY(-100%);
        }

        100% {
            transform: translateY(0);
        }
    }

    .mask-anim-enter-active {
        animation: mask-anim-in .35s;
    }

    .mask-anim-leave-active {
        animation: mask-anim-in .35s reverse;
    }

    @keyframes mask-anim-in {
        0% {
            transform: translateY(100%);
        }

        100% {
            transform: translateY(0);
        }
    }

    @media only screen and (max-width: 800px)
    {
        .nav-open {
            width: 100%;

            .nav-header {
                h3 {
                    font-size: 1.7em;
                }
            }

            .nav-content {
                div {
                    font-size: 1.5em;
                }
            }
        }


        .nav-mask {
            width: 100%;
        }
    }

    // @keyframes nav-load {
    //     from {
    //         opacity: 0;
    //     }

    //     to {
    //         opacity: 1;
    //     }
    // }
</style>