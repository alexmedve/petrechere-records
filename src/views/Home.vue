<template>
  <section class="container">
    <div class="content">
      <h2>Petrechere<br>Records</h2>
      <div class="home-menu">
        <router-link :to="menuItem.link" v-for="(menuItem, index) in menuItems" :key="index" tag="div">
          {{menuItem.title}}
        </router-link>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'home',
    data() {
      return {
        menuItems: [{
            title: "Events",
            link: '/events'
          },
          {
            title: "Artists",
            link: '/artists'
          },
          {
            title: "Contact",
            link: '/contact'
          },
          {
            title: "Radio",
            link: '/radio'
          }
        ]
      }
    }
  }
</script>

<style lang="scss">
  section.container {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100vh;
    display: grid;
    grid-template-columns: 1fr 80% 1fr;

    .content {
      grid-column: 2/3;

      h2 {
        font-size: 3em;
        text-align: center;
        display: none;
        margin: 0 auto;
        margin-top: 100px;
        font-weight: 400 !important;
        letter-spacing: 0.1em;
      }

      .home-menu {
        margin: 0 auto;
        margin-top: 80px;
        display: grid;
        grid-template-columns: 1fr;
        grid-gap: 2em;
        margin-top: 20vh;
        margin-bottom: 15vh;

        div {
          padding: 20px 0;
          border: 2px solid #ffffff;
          cursor: pointer;
          font-size: 1.75em;
          opacity: 0;
          transform: translateY(40px);
          animation-name: menu-item-anim;
          animation-duration: 0.35s;
          animation-delay: 0.75s;
          animation-fill-mode: forwards;
        }

        div:hover {
          background-color: #7B88D6;
        }
      }
    }
  }

  @media only screen and (max-width: 800px) {
    section.container {
      background: url('../assets/landing_page_dj_dark.jpg') center center;
      background-size: cover;
      background-repeat: no-repeat;

      .content {
        h2 {
          display: block;
          font-size: 2.5em;
          margin-bottom: 45px;
        }

        .home-menu {
          margin-top: 0;

          div {
            font-size: 1.3em;
            padding: 10px;
          }
        }
      }
    }
  }

  @keyframes menu-item-anim {
    from {
      opacity: 0;
      transform: translateY(40px);
    }

    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
</style>