<script>
import LayoutHeader from "../components/LayoutHeader.vue"
import LayoutFooter from '../components/LayoutFooter.vue'

export default {
  name: "PricingView",
  components: {
    LayoutHeader,
    LayoutFooter,
  }
}
</script>

<template>
  <LayoutHeader />

  <main class="pricing">
    <article class="article">
      <h2 class="head">Curate your feed from dozens of resources.</h2>
      <p class="body">
        We cover all major platforms where one could want to curate their feed
        from, Reddit,ProductHunt, IndieHackers, and so much more.
      </p>
      <router-link
        :to="{ name: 'contact' }"
        class="btn"
      >
        <strong class="strong">Get Started</strong> - it's free!
      </router-link>
    </article>
    <figure class="hero">
      <img src="../assets/social-media-icons.png" alt="social media icons" />
    </figure>
  </main>

  <LayoutFooter/>
</template>

<style lang="scss" scoped>
@import "../main.scss";

.pricing {
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
    }

    .btn {
      @include btn;
    }
  }

  .hero {
    order: 1;
  }
}

@media screen and (width >= 576px) {
  .pricing {
    .hero {
      width: 75%;
      align-self: center;
    }
  }
}

@media screen and (width >= 1024px) {
  .pricing {
    flex-direction: row;
    align-items: center;
    padding: 2rem;
    gap: 4rem;

    .article {
      order: 1;
      width: 50%;
      gap: 1.5rem;
    }

    .hero {
      order: 2;
      width: 50%;
    }
  }
}
</style>
