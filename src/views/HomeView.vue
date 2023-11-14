<script>
import LayoutHeader from "../components/LayoutHeader.vue"
import LayoutFooter from '../components/LayoutFooter.vue'

export default {
  name: "HomeView",
  components: {
    LayoutHeader,
    LayoutFooter,
  }
}
</script>

<template>
  <LayoutHeader />

  <main class="home">
    <article class="article">
      <h1 class="head">Your weekly personal feed digest.</h1>
      <p class="body">
        With IndieBrew, get personal feeds from resources all around the web,
        including Reddit, HackerNews, IndieHackers and much more.
      </p>
      <router-link
        :to="{ name: 'contact' }"
        class="btn"
      >
        <strong class="strong">Get Started</strong> - it's free!
      </router-link>
      <figure class="avatars">
        <img src="../assets/user-avatars.svg" alt="user avatars" />
      </figure>
      <p class="body">
        Join <em class="em">32,642</em> IndieBrewers in curating their personal digest.
      </p>
    </article>
    <figure class="hero">
      <img src="../assets/feed-mockup.png" alt="feed mockup" />
    </figure>
  </main>

  <LayoutFooter/>
</template>

<style lang="scss" scoped>
@import "../main.scss";

.home {
  @include flex-col;
  align-items: flex-start;
  padding: 2rem 1rem 4rem;
  gap: 2rem;

  .article {
    order: 2;
    @include flex-col;
    align-items: flex-start;
    gap: 1rem;

    .head {
      font-weight: 700;
      font-size: min(12vw, 3rem);
      color: $clr-off-black;
    }

    .body {
      color: $clr-off-gray;

      .em {
        color: $clr-off-sky;
        font-weight: 700;
        font-style: normal;
      }
    }

    .btn {
      @include btn;
    }
  }

  .hero {
    order: 1;
    padding-inline: 1rem;
  }
}

@media screen and (width >= 576px) {
  .home {
    
    .hero {
      width: 50%;
      align-self: center;
      padding: 0;
    }
  }
}

@media screen and (width >= 1024px) {
  .home {
    flex-direction: row;
    align-items: center;
    gap: 0;
    padding: 2rem;

    .article {
      order: 1;
      width: 50%;
      padding: 0;
      gap: 1.5rem;
    }

    .hero {
      order: 2;
    }
  }
}
</style>
