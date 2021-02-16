<template>
  <div>
    <Navbar />
    <Nuxt />
    <Footer />
    <button class="btn btn-float" @click="scrollTop">
      ▲
    </button>
  </div>
</template>
<script>
import { appConfig } from "@/env";
import Navbar from "~/components/Navbar";
import Footer from "~/components/Footer";
export default {
  components: {
    Navbar,
    Footer
  },
  methods: {
    scrollTop() {
      window.scroll({
        top: 0,
        left: 0,
        behavior: "smooth"
      });
    }
  },
  head() {
    return {
      title: "Rick And Morty | CCDEV",
      noscript: [{ innerHTML: "Body No Scripts", body: true }],
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Rick And Morty API"
        },
        /* Facebook */
        { property: "og:image", content: appConfig.logo },
        { property: "og:url", content: appConfig.urlOficial },
        { property: "og:title", content: appConfig.title },
        { property: "og:type", content: appConfig.type },
        { property: "og:site_name", content: appConfig.title },
        { property: "og:description", content: appConfig.description },

        /* Whatsapp */
        { property: "og:image", content: appConfig.logoWhatsapp },
        { property: "og:url", content: appConfig.urlOficial },
        { property: "og:title", content: appConfig.title },
        { property: "og:site_name", content: appConfig.title },
        { property: "og:description", content: appConfig.description },

        /* Twitter */
        { name: "twitter:url", content: appConfig.urlOficial },
        { name: "twitter:image", content: appConfig.logo },
        { name: "twitter:title", content: appConfig.title },
        { name: "twitter:description", content: appConfig.description }
      ]
    };
  }
};
</script>
<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
.btn-float {
  position: fixed;
  border-radius: 50%;
  padding: 0.4rem 0.6rem;
  bottom: 1rem;
  right: 1rem;
}
</style>
