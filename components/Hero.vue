<template>
  <div class="container-fluid p-0 h-100">
    <div class="row no-gutters h-100 justify-content-center align-items-center">
      <div class="col p-5">
        <img src="~assets/images/logo.png" alt="logo" />

        <h1>Create, share and <span>earn</span></h1>
        <h3>...all from your phone</h3>

        <ul>
          <li>Turn iPhone videos into a subscription business</li>
          <li>Engage with your community</li>
          <li>Your terms, your content, your brand</li>
        </ul>

        <button type="button" class="btn btn-primary">Become a creator</button>
      </div>
      <div class="col">
        <img src="~assets/images/hero.png" class="hero__background-image" />

        <transition name="fade">
          <div class="hero__images">
            <div
              class="hero__images--container"
              v-for="(slide, index) in slides"
              v-if="activeSlide === index"
              :class="{ 'slide-left': slideDirection == 0 }"
              :key="index"
            >
              <img :src="require(`~/assets/images/${slide.photo}`)" alt="" />
            </div>
            <div class="hero__button-right" @click="slideRight">></div>
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      changeInterval: null,
      activeSlide: 0,
      slideDirection: 0,
      slides: [
        {
          photo: "phone1.png"
        },
        {
          photo: "phone1.png"
        },
        {
          photo: "phone1.png"
        }
      ]
    };
  },
  mounted() {
    this.changeInterval = setInterval(() => this.nextSlide(), 10000);
  },
  methods: {
    clearIntervalSlider() {
      clearInterval(this.changeInterval);
    },
    slideRight() {
      this.nextSlide();
      this.clearIntervalSlider();
    },
    previousSlide() {
      this.activeSlide =
        this.activeSlide <= 0 ? this.slides.length - 1 : this.activeSlide - 1;
      this.slideDirection = 0;
    },
    nextSlide() {
      this.activeSlide =
        this.activeSlide < this.slides.length - 1 ? this.activeSlide + 1 : 0;
      this.slideDirection = 1;
    }
  }
};
</script>

<style lang="scss" scoped>
.hero {
  &__background-image {
    width: 100%;
  }

  &__images {
    &--container {
      position: absolute;
      bottom: 0;
    }
  }

  &__button-right {
    background: #171d33;
    color: #fff;
    font-size: 36px;
    cursor: pointer;
    border-radius: 300px;
    padding: 30px 45px;
    position: absolute;
    top: 50%;
    right: 5%;
  }
}

.container--thoughts {
  height: 100%;
  position: relative;
}

.row--thoughts {
  height: 100%;
}

h3 {
  position: static;
  left: 0px;
  margin-right: 0px;
  margin-bottom: 10px;
  padding-left: 0px;
  clear: none;
  color: #28dc8e;
  font-size: 18px;
  font-weight: 700;
}

p {
  font-family: "Markpro light", sans-serif;
  color: #3e83ff;
  font-size: 33px;
  line-height: 51px;
  letter-spacing: -0.6px;
}

.slider-content {
  padding-top: 100px;
  height: 560px;
}

.slider-container,
.team-image-slider {
  position: relative;
}

.slider-container .slider,
.team-image-slider .slide {
  position: absolute;
}

// QUOTE TRANSITIONS

.fade-enter,
.fade-enter p,
.fade-enter-active p,
.fade-enter-to p,
.fade-leave-active p,
.fade-leave-active,
.fade-enter.slide-left,
.fade-enter.slide-left p,
.fade-enter-active.slide-left p,
.fade-enter-to.slide-left p,
.fade-leave-active.slide-left p,
.fade-leave-active.slide-left {
  transition: all 0.35s ease;
}

.fade-enter-active,
.fade-leave-active,
.fade-enter-active.slide-left,
.fade-leave-active.slide-left {
  transition: all 0.4s ease;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}

.fade-enter-active.slide-left p {
  transform: translateX(31px);
}

.fade-enter-active p {
  transform: translateX(-31px);
}

.fade-enter-to.slide-left p {
  transform: translateX(0);
}

.fade-enter-to p {
  transform: translateX(0);
}

.fade-enter-active,
.fade-enter-active.slide-left {
  transition-delay: 100ms;
}

.fade-enter-active.slide-left h3 {
  transform: all 0.35s ease;
  transition: translateX(-62px);
  opacity: 0;
}

.fade-enter-active h3 {
  transform: all 0.35s ease;
  transition: translateX(62px);
  opacity: 0;
}

.fade-enter-to.slide-left h3 {
  transition: all 0.35s ease;
  transform: translateX(0px);
  opacity: 1;
}

.fade-enter-to h3 {
  transition: all 0.35s ease;
  transform: translateX(0px);
  opacity: 1;
}

.fade-enter-active.slide-left p {
  transform: 31px;
}

.fade-enter-active p {
  transform: -31px;
}

.fade-enter-to.slide-left p {
  transform: translateX(0);
}

.fade-enter-to p {
  transform: translateX(0);
}

.fade-enter.slide-left {
  transform: translateX(17px);
}

.fade-enter {
  transform: translateX(-17px);
}

.fade-enter.slide-left h3 {
  transform: translateX(0);
}

.fade-enter h3 {
  transform: translateX(0);
}

.slider {
  position: relative;
  display: block;
  left: 0;
  right: 0;
  height: 100%;
}

.the-team-slider {
  position: relative;
  margin-top: 169px;
  margin-bottom: 258px;
  padding-top: 0px;
  padding-bottom: 0px;
}

.the-team-slider__overlay {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100vw;
  margin-left: 80px;
  background-color: #f8fbff;
}

.container-full {
  position: relative;
  margin-right: auto;
  margin-left: auto;
  padding: 0px 56px;
}

.staff-slider {
  padding-left: 0;
}

.thoughts-from-the-team {
  position: relative;
  top: 0px;
}

.team-slider-profile-pic {
  position: absolute;
  width: 266px;
  height: 266px;
  margin-top: 145px;
}

.button-container {
  position: absolute;
  display: flex;
  margin-top: 0;
  right: 10px;
  bottom: -25px;
  margin-left: 0px;
  padding-top: 0px;
  padding-left: 0px;
  flex-direction: row;
  justify-content: flex-end;
  align-items: center;
}

.team-slider-button {
  position: relative;
  display: flex;
  width: 60px;
  height: 60px;
  float: none;
  flex-direction: row;
  justify-content: center;
  border-radius: 300px;
  background-image: linear-gradient(180deg, #fff, #fff);
  box-shadow: 0 3px 8px 0 rgba(62, 131, 255, 0.15);
  transition: transform 1s ease;
  cursor: pointer;

  &:hover {
    background-image: linear-gradient(180deg, #f8faff, #f8faff);
  }
}

.team-slider-button__left {
  margin-right: 10px;
  transform: translate(0px, 0px);

  .arrow-image-left {
    transform: rotateX(0deg) rotateY(-180deg) rotateZ(0deg);
  }
}

.team-author {
  font-family: "Markpro book", sans-serif;
  color: rgba(33, 14, 74, 0.75);
  font-size: 18px;
  font-weight: 300;
  letter-spacing: 0;
  margin: 0;
}

.job-title {
  font-family: "Markpro book", sans-serif;
  color: rgba(33, 14, 74, 0.5);
  font-weight: 300;
  letter-spacing: 0;
}

.slider p {
  margin: 0 0 25px 0;
}
</style>
