<template>
  <div class="overlay" v-if="overlay" @click="closeMobileMenu"></div>
  <nav>
    <img
      class="icon-hamburger-menu"
      src="../assets/images/icon-hamburger.svg"
      alt="icon hamburger menu"
      @click="openMobileMenu"
    />
    <img
      @click="home"
      class="logo"
      src="../assets/images/logo.svg"
      alt="room logo"
    />
    <div class="menu-mobile" v-if="showMobileMenu">
      <img
        class="icon-close"
        src="../assets/images/icon-close.svg"
        alt="icon close menu"
        @click="closeMobileMenu"
      />
      <div class="nav-links-mobile">
        <a href="#">home</a>
        <a href="#">shop</a>
        <a href="#">about</a>
        <a href="#">contact</a>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  emits: ["back-home"],
  data() {
    return {
      showMobileMenu: false,
      overlay: false,
    };
  },
  mounted() {
    this.resizeWindow();
    window.addEventListener("resize", this.resizeWindow);
  },
  methods: {
    home() {
      this.$emit("back-home");
    },
    openMobileMenu() {
      this.showMobileMenu = true;
      this.overlay = true;
      document.body.style.overflow = "hidden";
      // this.resizeWindow();
    },
    closeMobileMenu() {
      this.showMobileMenu = false;
      this.overlay = false;
      document.body.style.overflow = "unset";
    },
    resizeWindow() {
      const windowWidth = window.innerWidth;
      if (windowWidth >= 700) {
        this.overlay = false;
        this.showMobileMenu = true;
      } else {
        this.overlay = false;
        this.showMobileMenu = false;
      }
      // if (windowWidth <= 700) {
      //   return
      // } else {
      //   this.overlay = false;
      //   this.showMobileMenu = true;
      // }
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
.overlay {
  position: absolute;
  width: 100%;
  min-height: 100vh;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(44, 44, 44, 0.507);
  z-index: 15;
  cursor: pointer;
}
nav {
  position: absolute;
  padding: 3rem 0 0 1.5rem;
  width: 100%;
  z-index: 20;
  .logo {
    position: absolute;
    left: 50%;
    top: 87%;
    transform: translate(-50%, -50%);
    cursor: pointer;
  }
  .icon-close,
  .icon-hamburger-menu {
    cursor: pointer;
  }
  .menu-mobile {
    position: absolute;
    background-color: rgb(255, 255, 255);
    top: 0;
    left: 0;
    right: 0;
    width: 100%;
    padding: 2.9rem 1.6rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    .nav-links-mobile {
      a {
        position: relative;
        font-weight: 600;
        text-decoration: none;
        color: #000;
        margin-left: 25px;
        &::after {
          position: absolute;
          content: "";
          bottom: -10px;
          left: 50%;
          transform: translateX(-50%);
          width: 0%;
          height: 2px;
          background-color: #000;
          border-radius: 10px;
          transition: width 0.15s linear;
        }
        &:hover {
          &::after {
            width: 70%;
          }
        }
      }
    }
  }
  @include tablet {
    display: flex;
    align-items: center;
    padding: 3rem 0 0 4rem;
    width: fit-content;
    .logo {
      position: relative;
      top: unset;
      left: unset;
      right: unset;
      transform: unset;
    }
    .icon-close,
    .icon-hamburger-menu {
      display: none;
    }
    .menu-mobile {
      width: unset;
      padding: unset;
      background-color: unset;
      position: relative;
      .nav-links-mobile {
        margin-left: 35px;
        a {
          color: #fff;
          &::after {
            background-color: #fff;
          }
        }
      }
    }
  }
}
</style>
