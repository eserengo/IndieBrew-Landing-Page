<script>
import LayoutHeader from "../components/LayoutHeader.vue"
import LayoutFooter from '../components/LayoutFooter.vue'

export default {
  name: "SupportView",
  components: {
    LayoutHeader,
    LayoutFooter,
  }
}
</script>

<template>
  <LayoutHeader />

  <main class="support">
    <article class="article">
      <h2 class="head">Access your feed from the comfort of your phone.</h2>
      <p class="body">
        With native apps for both iOS and Android, accessing your curated
        content has never been easier.
      </p>
      <router-link
        :to="{ name: 'contact' }"
        class="btn"
      >
        <strong class="strong">Get Started</strong> - it's free!
      </router-link>
    </article>
    <figure class="hero">
      <img src="../assets/phone-mockup.png" alt="phone mockup" />
    </figure>
  </main>

  <LayoutFooter/>
</template>

<style lang="scss" scoped>
@import "../main.scss";

.support {
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
      font-size: min(9vw, 2rem);
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
  .support {
    .hero {
      width: 50%;
      align-self: center;
    }
  }
}

@media screen and (width >= 1024px) {
  .support {
    flex-direction: row;
    align-items: center;
    padding: 2rem;
    gap: 4rem;

    .article {
      width: 50%;
      gap: 1.5rem;
    }

    .hero {
      width: 50%;
    }
  }
}
</style>

