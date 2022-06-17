<template>
  <section
    v-show="currentCard === index"
    v-for="(page, index) in pages"
    :key="index"
    :index="index"
    :currentCard="currentCard"
  >
    <the-nav @back-home="firstSlide"></the-nav>
    <div class="img-main-container">
      <transition name="img-slide">
        <img
          class="img-main-desktop"
          :src="page.urlMainDesktop"
          :alt="page.alt"
        />
      </transition>
      <transition name="text-drop">
        <img
          class="img-main-mobile"
          :src="page.urlMainMobile"
          :alt="page.alt"
        />
      </transition>
    </div>
    <div class="main-text-content">
      <h1 class="title-main">{{ page.titleMain }}</h1>
      <p class="text-block">{{ page.textMain }}</p>
      <shop-button></shop-button>
    </div>
    <the-buttons @button-left="btnLeft" @button-right="btnRight"></the-buttons>
    <div class="img-left-container">
      <img class="imgLeft" src="../assets/images/image-about-dark.jpg" alt="" />
    </div>
    <div class="secondary-text-content">
      <h3>About our furniture</h3>
      <p class="text-block">
        Our multifunctional collection blends design and function to suit your
        individual taste. Make each room unique, or pick a cohesive theme that
        best express your interests and what inspires you. Find the furniture
        pieces you need, from traditional to contemporary styles or anything in
        between. Product specialists are available to help you create your dream
        space.
      </p>
    </div>
    <div class="img-right-container">
      <img
        class="imgRight"
        src="../assets/images/image-about-light.jpg"
        alt=""
      />
    </div>
  </section>
  <the-attribution></the-attribution>
</template>

<script>
import ShopButton from "./ShopButton.vue";
import TheNav from "./TheNav.vue";
import TheButtons from "./TheButtons.vue";
import TheAttribution from "./TheAttribution.vue";
export default {
  components: {
    ShopButton,
    TheNav,
    TheButtons,
    TheAttribution,
  },
  data() {
    return {
      pages: [
        {
          id: 1,
          urlMainDesktop: require("../assets/images/desktop-image-hero-1.jpg"),
          urlMainMobile: require("../assets/images/mobile-image-hero-1.jpg"),
          alt: "four white chairs under a table",
          titleMain: "Discover innovative ways to decorate",
          textMain:
            "We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.",
        },
        {
          id: 2,
          urlMainDesktop: require("../assets/images/desktop-image-hero-2.jpg"),
          urlMainMobile: require("../assets/images/mobile-image-hero-2.jpg"),
          alt: "three colored chairs",
          titleMain: "We are available all across the globe",
          textMain:
            "With stores all over the world, it's easy for you to find furniture for your home or place of business. Locally, we’re in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don't hesitate to contact us today.",
        },
        {
          id: 3,
          urlMainDesktop: require("../assets/images/desktop-image-hero-3.jpg"),
          urlMainMobile: require("../assets/images/mobile-image-hero-3.jpg"),
          alt: "black pliable chair",
          titleMain: "Manufactured with the best materials",
          textMain:
            "Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.",
        },
      ],
      currentCard: 0,
    };
  },
  computed() {},
  methods: {
    btnLeft() {
      if (this.currentCard <= 0) {
        this.currentCard = this.pages.length;
      }
      this.currentCard--;
    },
    btnRight() {
      if (this.pages.length - 1 <= this.currentCard) {
        this.currentCard = -1;
      }
      this.currentCard++;
    },
    firstSlide() {
      this.currentCard = 0;
    },
  },
};
</script>

<style scoped lang="scss">
@mixin tablet {
  @media only screen and(min-width: 700px) {
    @content;
  }
}
@mixin desktop {
  @media only screen and(min-width: 1100px) {
    @content;
  }
}
section {
  display: grid;
  grid-template-columns: 1fr;
  img {
    width: 100%;
    display: block;
  }
  .img-main-container {
    grid-column: 1 / 2;
    grid-row: 1 / 2;
    .img-main-desktop {
      display: none;
    }
    .img-slide-enter-from {
      transform: translateX(0);
      opacity: 1;
    }
    .img-slide-enter-active {
      transition: all 0.15s ease-in-out;
    }
    .img-slide-enter-to {
      transform: translateX(-400px);
      opacity: 0;
    }
  }
  .main-text-content {
    padding: 55px 25px 55px 25px;
    .title-main {
      font-size: 35px;
      line-height: 33px;
      font-weight: 700;
      margin-bottom: 20px;
      max-width: 380px;
    }
    .text-block {
      color: hsl(0, 0%, 63%);
      line-height: 20px;
      margin-bottom: 20px;
    }
  }
  .secondary-text-content {
    padding: 55px 25px 40px 25px;
    h3 {
      margin-bottom: 20px;
      font-size: 14px;
      letter-spacing: 7px;
      text-transform: uppercase;
    }
    .text-block {
      color: hsl(0, 0%, 63%);
      line-height: 20px;
    }
  }
  @include tablet {
    grid-template-columns: 1fr 1fr;
    .img-main-container {
      grid-column: 1 / 3;
      .img-main-mobile {
        display: none;
      }
      .img-main-desktop {
        display: block;
      }
    }
    .img-left-container {
      grid-column: 1 / 2;
      grid-row: 2 / 3;
    }
  }
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
  @include desktop {
    height: 100vh;
    grid-template-columns: 30% 1fr 120px 30%;
    grid-template-rows: 58% 60px 1fr;
    overflow: hidden;
    .img-main-container {
      overflow: hidden;
      grid-column: 1 /3;
      grid-row: 1 / 3;
      .img-main-desktop {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center 70%;
      }
    }
    .main-text-content {
      grid-column: 3 /5;
      grid-row: 1 / 3;
      place-self: center;
      padding: 4rem;
    }
    .img-left-container {
      overflow: hidden;
      grid-column: 1/ 2;
      grid-row: 3 / 4;
    }
    .secondary-text-content {
      grid-column: 2 / 4;
      grid-row: 3 / 4;
    }
    .img-right-container {
      overflow: hidden;
      grid-column: 4 / -1;
      grid-row: 3 / 4;
    }
  }
}
</style>
