<template>
  <section
    class="home"
    id="home"
    :style="{ backgroundImage: 'url(' + bannerImg + ')' }"
  >
    <div class="max-width">
      <div class="home-content">
        <div class="text-1">Hello, my name is</div>
        <div class="text-2">{{ displayName }}</div>
        <div class="text-3">And I'm a <span class="typing"></span></div>
        <a href="#contact">Hire me</a>
      </div>
    </div>
  </section>
</template>
<script>
import img from "../assets/images/banner.jpg";
export default {
  name: "HomeSectionStart",
  data() {
    return {
      bannerImg: img,
      displayName: "Tanesh Patel",
    };
  },
  mounted() {
    // typing text animation script
    var typed = new Typed(".typing", {
      strings: ["YouTuber", "Developer", "Blogger", "Designer", "Freelancer"],
      typeSpeed: 100,
      backSpeed: 60,
      loop: true,
    });
  },
};
</script>