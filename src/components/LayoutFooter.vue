<script>
export default {
  name: "LayoutFooter", 
  }
</script>

<template>
  <footer class="footer">
    <article class="info">
      <h3 class="head">IndieBrew</h3>
      <p class="body">
        With IndieBrew, get personal feeds from <br />
        resources all around the web, including <br />
        Reddit, HackerNews and much more.
      </p>
      <p class="body">
        Made with &hearts; in the UK.
      </p>
    </article>

    <nav class="navbar">
      <h3 class="head">Sitemap</h3>
      <router-link
        :to="{ name: 'home' }"
        class="link"
      >
        Home
      </router-link>
      <router-link
        :to="{ name: 'pricing' }"
        class="link"
      >
        Pricing
      </router-link>
      <router-link
        :to="{ name: 'support' }"
        class="link"
      >
        Support
      </router-link>
    </nav>
  </footer>
</template>

<style lang="scss">
@use "sass:color";
@import "../main.scss";

.footer {
  @include flex-col;
  align-items: flex-start;
  position: relative;
  bottom: 0;
  left: 0;
  padding: 1rem !important;
  gap: 2rem;

  .info {
    @include flex-col;
    align-items: flex-start;
    gap: 1rem;

    .head {
      color: $clr-off-black;
      font-weight: 700;
    }

    .body {
      color: $clr-off-gray;
    }
  }

  .navbar {
    @include flex-col;
    align-items: flex-start;

    .head {
      color: $clr-off-black;
      font-weight: 700;
    }

    .link {
      font-weight: 700;
      color: color.adjust($clr-off-gray, $alpha: -0.25);
      text-decoration: none;
      padding-block: 1rem;

      &:hover:not(.router-link-active),
      &:focus:not(.router-link-active) {
        color: $clr-off-gray;
      }
    }

    .router-link-active {
      color: $clr-off-black;
      border-bottom: 0.2rem solid $clr-off-black;
      padding-bottom: calc(1rem - 0.2rem);
    }
  }
}

@media screen and (width >= 576px) {
  .footer {
    flex-direction: row;
    justify-content: space-between;
  }
}

@media screen and (width >= 1024px) {
  .footer {
    padding-inline: 2rem !important;
  }
}
</style>
