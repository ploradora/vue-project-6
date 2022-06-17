<template>
  <div class="nav-buttons">
    <div class="left" @click="$emit('button-left')">
      <img src="../assets/images/icon-angle-left.svg" alt="icon arrow left" />
    </div>
    <div class="right" @click="$emit('button-right')">
      <img src="../assets/images/icon-angle-right.svg" alt="icon arrow right" />
    </div>
  </div>
</template>

<script>
export default {
  emits: ['button-left', 'button-right'],
  data() {
    return {
    }
  },

}
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
.nav-buttons {
  display: flex;
  align-items: center;
  grid-column: 1 / 2;
  grid-row: 1/ 2;
  justify-self: end;
  align-self: end;
  z-index: 10;
  .left,
  .right {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #000;
    height: 50px;
    width: 50px;
    &:hover {
        cursor: pointer;
        background-color: hsl(0, 0%, 27%);
        
    }
    img {
        width: 9px;
    }
  }
  @include tablet {
    grid-column: 2 / 3;
    .left,
    .right {
      height: 60px;
      width: 60px;
      img {
          width: unset;
      }
    }
  }
  @include desktop {
    grid-column: 3 / 4;
    grid-row: 2 / 3;
  }
}
</style>
