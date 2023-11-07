<script>
export default {
  name: "LayoutHeader", 

  data() {
    return {
      media: { Boolean },
      isActive: false,
    }
  },

  methods: {
    setMedia() {
      let timer;
      window.clearTimeout(timer);
      timer = window.setTimeout(
        window.matchMedia("(width < 576px)").matches
          ? this.media = true
          : this.media = false
        , 500);
    },
    toggleIsActive() {
      this.isActive = !this.isActive;
    },
  },

  mounted() {
    this.setMedia();
    window.addEventListener("resize", () => this.setMedia());
  },

  unmounted() {
    window.removeEventListener("resize", () => this.setMedia());
  },
}
</script>

<template>
  <header class="header">
    <img
      src="../assets/logo.svg"
      alt="IndieBrew logo" 
      class="logo" />

    <nav v-if="media">
      <section 
        v-if="isActive" 
        class="mobile navbar"
      >
        <img 
          src="../assets/icon-close.svg" 
          alt="close icon" 
          @click="toggleIsActive" 
          @keyup.enter="toggleIsActive"
          class="close icon" 
          tabindex=0 
        />
        <router-link 
          :to="{ name: 'home' }" 
          @click="toggleIsActive" 
          class="link"
        >
          Home
        </router-link>
        <router-link 
          :to="{ name: 'pricing' }" 
          @click="toggleIsActive" 
          class="link"
        >
          Pricing
        </router-link>
        <router-link 
          :to="{ name: 'support' }" 
          @click="toggleIsActive" 
          class="link"
        >
          Support
        </router-link>
      </section>
      <img 
        v-else 
        src="../assets/hamburger-menu.svg" 
        alt="hamburger icon"
        @click="toggleIsActive"
        @keyup.enter="toggleIsActive" 
        class="hamburger icon" 
        tabindex=0 
      />
    </nav>

    <nav 
      v-else 
      class="full navbar">
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
  </header>
</template>

<style lang="scss">
@use "sass:color";
@import "../main.scss";

.header {
  @include flex-row;
  justify-content: space-between;
  background-color: transparent;
  width: 100%;
  position: relative;
  left: 0;
  top: 0;
  padding: 1rem !important;

  .logo {
    margin-bottom: 0.25rem;
  }
   
  .icon {
    cursor: pointer;
  }

  .hamburger.icon {
    margin-top: 0.25rem;
  }

  .navbar {
    .link {
      font-weight: 700;
      color: color.adjust($clr-off-gray, $alpha: -0.5);
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

  .mobile.navbar {
    @include flex-col;
    justify-content: space-evenly;
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: $clr-off-white;
    padding: 20vh 10vw;
    z-index: 10;

    .close.icon {
      align-self: flex-end;
    }
  }
}

@media screen and (width >=576px) {
  .full.navbar {
    @include flex-row;
    justify-content: space-between;
    gap: 2rem;
  }
}

@media screen and (width >= 1024px) {
  .header {
    padding-inline: 2rem !important;
  }
}
</style>
