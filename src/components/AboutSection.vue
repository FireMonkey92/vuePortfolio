<template>
  <section class="about" id="about" :class="isDarkMode && ' dark-theme'">
    <div class="max-width">
      <h2 class="title">About me</h2>
      <div class="about-content">
        <div class="column left">
          <img :src="prof1" alt="" />
        </div>
        <div class="column right">
          <div class="text">
            I'm Tanesh and I'm a <span class="typing-2"></span>
          </div>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Quasi ut
            voluptatum eveniet doloremque autem excepturi eaque, sit laboriosam
            voluptatem nisi delectus. Facere explicabo hic minus accusamus alias
            fuga nihil dolorum quae. Explicabo illo unde, odio consequatur ipsam
            possimus veritatis, placeat, ab molestiae velit inventore
            exercitationem consequuntur blanditiis omnis beatae. Dolor iste
            excepturi ratione soluta quas culpa voluptatum repudiandae harum
            non.
          </p>
          <a href="#">Download CV</a>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import prof1 from "../assets/images/profile-1.jpeg";
export default {
  name: "AboutSection",
  props: ["isDarkMode"],
  data() {
    return {
      prof1: prof1,
    };
  },
  mounted() {
    var typed = new Typed(".typing-2", {
      strings: ["YouTuber", "Developer", "Blogger", "Designer", "Freelancer"],
      typeSpeed: 100,
      backSpeed: 60,
      loop: true,
    });
  },
};
</script>