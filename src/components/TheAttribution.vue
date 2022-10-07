<template>
  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io/challenges/room-homepage-BtdBY_ENq" target="_blank"
      >Frontend Mentor</a
    >. Coded by <a href="https://sebastiansuciu.netlify.app/">Sebastian Suciu</a>.
  </div>
</template>

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

.attribution {
  color: rgb(65, 65, 65);
  background-color: rgb(201, 201, 201);
  font-family: 'Times New Roman', Times, serif;
  font-size: 12px;
  text-align: center;
  padding: 13px 0 7px 0;
  a {
    color: hsl(0, 0%, 0%);
  }
}
</style>
