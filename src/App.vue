<template>
  <div id="app">
    <app-nav></app-nav>
    <div class="main">
      <div class="home">
        <header>
          <div class="header-text">
            <h2>Petrechere<br>records</h2>
          </div>
        </header>
      </div>
      <div class="test">
        <transition name="slide" mode="out-in">
          <router-view></router-view>
        </transition>
      </div>
    </div>
  </div>
</template>
<script>
  import Nav from './components/Nav.vue'

  export default {
    components: {
      'app-nav': Nav
    }
  }
</script>
<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat&display=swap');

  html,
  body {
    margin: 0;
    padding: 0;
    height: 100%;
    background: #333740;
    font-weight: 400 !important;
  }

  #app {
    font-family: 'Montserrat', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ffffff;
    margin: 0;
    padding: 0;
    overflow: hidden;
  }

  .main {
    margin: 0;
    padding: 0;
    position: relative;
    height: 100vh;
    width: 100%;
    display: grid;
    grid-template-columns: 40% 60%;
    overflow: hidden;

    header {
      top: 0;
      left: 0;
      height: 100vh;
      width: 100%;
      background: url('./assets/landing_page_dj_purple.jpg') center center;
      background-size: cover;
      background-repeat: none;

      .header-text {
        padding-top: 35vh;

        h2 {
          display: block;
          margin-top: 0 !important;
          font-weight: 400 !important;
          font-size: 2.7em;
          letter-spacing: 0.2em;
          text-align: center;
          animation-name: header-anim;
          opacity: 0;
          transform: translateY(-40px);
          animation-duration: 0.35s;
          animation-delay: 0.5s;
          animation-fill-mode: forwards;
        }
      }
    }

    .test {
      margin: 0;
      padding: 0;
      height: 100vh;
      overflow-y: auto;
    }
  }

  ::-webkit-scrollbar {
    width: 15px;
  }

  /* Track */
  ::-webkit-scrollbar-track {
    background: #333740;
  }

  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: #888;
  }

  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }

  @media only screen and (max-width: 800px) {
    ::-webkit-scrollbar {
      width: 10px;
    }

    .main {
      grid-template-columns: 1fr;

      .home {
        display: none;
      }
    }
  }

  @keyframes header-anim {
    from {
      opacity: 0;
      transform: translateY(-40px);
    }

    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

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
    animation-delay: 0.5s;
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