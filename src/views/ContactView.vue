<script>
export default {
  name: "ContactView",
  
  data() {
    return {
      media: { Boolean },
    }
  },

  methods: {
    setMedia() {
      let timer;
      window.clearTimeout(timer);
      timer = window.setTimeout(
        window.matchMedia("(width < 576px)").matches
          ? this.media = false
          : this.media = true
        , 500);
    },

    handleSubmit() {
      this.$router.push({ name: "home" });
    }
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
  <header class="contact-header">
    <img
      src="../assets/logo.svg"
      alt="IndieBrew logo" 
      class="logo" 
    />

    <nav class="navbar">
      <router-link 
        :to="{ name: 'home' }"
        class="link"
      >
        <img 
          src="../assets/back-arrow.svg" 
          alt="back arrow"
          class="arrow icon"
        />
        <span v-if="media" class="text">
          Back to Homepage
        </span>
      </router-link>
    </nav>
  </header>
  <main class="contact-main">
    <article class="article">
      <h2 class="head">Create your personalized feed.</h2>
      <p class="body">
        <strong class="strong">&bull; Over 20 resources.</strong>
        With resources ranging from Reddit to IndieHackers,
        we've got all your needs covered.
      </p>
      <p class="body">
        <strong class="strong">&bull; Delivered weekly.</strong>
        Every week at exactly Tuesday 12:00 PM. EST - expect
        a value-packed digest right in your mail. 
      </p>
      <p class="body">
        <strong class="strong">&bull; Unlimited ideas.</strong>
        With all the ideas you'll be reading about, what's
        stopping you from creating a sustainable startup?
      </p>
    </article>
    <form class="form" action="#" @submit.prevent="handleSubmit">
      <h3 class="subhead">Create your IndieBrew Account</h3>
      <section>
        <label class="label" for="email">Email</label>
        <input
          type="email"
          id="email"
          placeholder="john@example.com"
          class="input"
          size="40"
          autocomplete="off"
          required
        />
      </section>
      <section>
        <label class="label" for="name">Full Name</label>
        <input
          type="text"
          id="name"
          placeholder="John Doe"
          class="input"
          size="40"
          autocomplete="off"
          required
        />
      </section>
      <section>
        <label class="label" for="password">Password</label>
        <input
          type="password"
          id="password"
          placeholder="At least 8 characters"
          class="input"
          size="40"
          autocomplete="off"
          required
        />
      </section>
      <section>
        <input
          type="checkbox"
          id="checkbox"
          class="checkbox"
          required
        />
        <label class="checkbox-label" for="checkbox">
          By creating an account on IndieBrew, you agree to
          the <em class="em">Terms & Conditions</em>.
        </label>
      </section>
      <button
        type="submit"
        class="btn"
      >
      Create an Account
      </button>
    </form>
  </main>
</template>

<style lang="scss" scoped>
@use "sass:color";
@import "../main.scss";

.contact-header {
  @include flex-row;
  justify-content: space-between;
  background-color: transparent;
  width: 100%;
  position: relative;
  left: 0;
  top: 0;
  padding: 1rem !important;

    .navbar {
    .link {
      @include flex-row;
      gap: 0.5rem;
      font-weight: 700;
      text-decoration: none;

      .icon {
        padding: 0.5rem 0.75rem;
        border: 2px solid $clr-off-gray;
        border-radius: 4px;
        box-shadow: 0px 2px 4px $clr-off-gray;
      }

      .text {
        font-size: 1.25rem;
        font-weight: 700;
        color: $clr-off-gray;
      }

      &:hover > .icon,
      &:focus > .icon {
        border-color: $clr-off-black;
      }

      &:hover > .text,
      &:focus > .text {
        color: $clr-off-black;
      }
    }
  }
}

.contact-main {
  @include flex-col;
  gap: 2rem;
  padding: 1rem;

  .article {
    @include flex-col;
    align-items: flex-start;
    gap: 1rem;

      .head {
        font-weight: 700;
        font-size: min(9vw, 2rem);
        color: $clr-off-black;
      }

      .body:not(.strong) {
        text-indent: 0.5rem;
        padding-inline: 0.5rem;
      
      .strong {
        display: inline;
        font-weight: 700;
      }
    }
  }

  .form {
    @include flex-col;
    align-items: flex-start;
    gap: 1.5rem;
    background-color: $clr-off-white;
    border-radius: 0.5rem;
    box-shadow: 0px 2px 8px $clr-off-gray;
    padding: 1.5rem;
    width: 100%;

    .subhead {
      font-weight: 700;
      font-size: min(6vw, 2rem);
      color: $clr-off-black;
    }

    .label {
      font-weight: 700;
      color: $clr-off-black;
      display: block;
    }

    .input {
      font-family: "DM Sans", sans-serif;
      font-size: 16px;
      color: $clr-off-black;
      border: 1px solid $clr-off-gray;
      border-radius: 0.25rem;
      box-shadow: 0px 2px 4px $clr-off-gray;
      padding: 0.5rem;
      margin-top: 0.25rem;

      &:placeholder {
        color: $clr-off-gray;
      }
    }

    .checkbox {
      display: inline;
      cursor: pointer;
    }

    .checkbox-label {
      display: inline;
      margin-left: 0.25rem;
      text-indent: 0.5rem;

      .em {
        color: $clr-off-sky;
        font-weight: 700;
        font-style: normal;
        text-decoration: underline;
        cursor: pointer;
      }
    }

    .btn {
      @include btn;
      align-self: center;
    }
  }
}

@media screen and (width >= 1024px) {
  .contact-header {
    padding-inline: 2rem !important;
  }

  .contact-main {
    flex-direction: row;
    padding: 2rem;
    gap: 4rem;

    .article,
    .form {
      width: 50%;
    }
  }
}
</style>
