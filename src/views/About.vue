<template>
  <div class="about">
    <!-- name="fade" -->
    <!-- @after-enter="afterEnter"
    @before-leave="beforeLeave"
    @leave="leave"
    -->
    <transition @after-leave="afterLeave" appear @before-enter="beforeEnter" @enter="enter">
      <h1 v-if="showTitle">About</h1>
    </transition>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
  </div>
</template>

<script>
import { ref } from "vue";
import gsap from "gsap";
export default {
  setup() {
    const showTitle = ref(true);
    const beforeEnter = (el) => {
      console.log("before enter", el);
      console.log("befefore enter - set intitial state");
      el.style.transform = "translateY(-60px)";
      el.style.opacity = 0;
    };
    const enter = (el, done) => {
      console.log("starting to enter - make transitions");
      console.log(" enter", el);

      gsap.to(el, {
        y: 0,
        opacity: 1,
        duration: 1,
        ease: "bounce.out",
        onComplete: done,
      });
    };

    const afterEnter = (el) => {
      // el.style.color = "green";
      console.log("after enter", el);
      // setTimeout(() => {
      //   showTitle.value = false;
      // }, 2000);
    };

    // const beforeLeave = (el) => {
    //   el.style.color = "pink";
    //   console.log("before leave", el);
    // };

    // const leave = (el) => {
    //   console.log(" leave", el);
    // };

    // const afterLeave = (el) => {
    //   console.log("after leave", el);
    // };
    return {
      showTitle,
      beforeEnter,
      enter,
      afterEnter,
      // beforeLeave,
      // leave,
      // afterLeave,
    };
  },
};
</script>

<style>
.about {
  max-width: 600px;
  margin: 20px auto;
}

/* switch transitions */

/* .fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active {
  transition: all 3s ease;
}
.fade-leave-active {
  transition: all 3s ease;
} */
</style>