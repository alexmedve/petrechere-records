<template>
    <div>
        <transition name="slide" mode="out-in">
            <router-view></router-view>
        </transition>
    </div>
</template>

<style lang="scss" scoped>
    .slide-leave-active {
        transition: opacity 0.5s ease;
        opacity: 0;
        animation: slide-out 0.5s ease-out forwards;
    }

    .slide-leave {
        opacity: 1;
        transform: translateX(0);
    }

    .slide-enter-active {
        animation: slide-in 0.5s ease-out forwards;
    }

    @keyframes slide-out {
        0% {
            transform: translateY(0);
        }

        100% {
            transform: translateY(-30px);
        }
    }

    @keyframes slide-in {
        0% {
            transform: translateY(-30px);
        }

        100% {
            transform: translateY(0);
        }
    }
</style>