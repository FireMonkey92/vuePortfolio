<template>
  <div>
    <div class="scroll-up-btn">
      <i class="fas fa-angle-up"></i>
    </div>
    <nav id="navbar">
      <div class="max-width">
        <div class="logo">
          <a href="#">Portfo<span>lio.</span></a>
        </div>
        <ul class="menu">
          <li><a href="#home" class="menu-btn">Home</a></li>
          <li><a href="#about" class="menu-btn">About</a></li>
          <li><a href="#services" class="menu-btn">Services</a></li>
          <li><a href="#skills" class="menu-btn">Skills</a></li>
          <li><a href="#teams" class="menu-btn">Teams</a></li>
          <li><a href="#contact" class="menu-btn">Contact</a></li>
          <li class="switch">
            <label class="switch">
              <input
                type="checkbox"
                v-bind:checked="isDarkMode"
                v-on:change="handhleChange"
              />
              <span class="slider round">
                <i class="fas" :class="isDarkMode ? ' fa-moon' : ' fa-sun'"></i>
              </span>
            </label>
          </li>
        </ul>
        <div class="menu-btn">
          <i class="fas fa-bars"></i>
        </div>
      </div>
    </nav>
  </div>
</template>
<script>
export default {
  name: "NavBar",
  props: {
    method: { type: Function },
  },
  data() {
    return {
      isDarkMode:
        localStorage.getItem("THEME") !== null
          ? localStorage.getItem("THEME") === "dark-theme"
            ? true
            : false
          : false,
    };
  },
  mounted() {
    // toggle menu/navbar script
    $(".menu-btn").click(function () {
      $("#navbar .menu").toggleClass("active");
      $(".menu-btn i").toggleClass("active");
      if (localStorage.getItem("THEME") !== "dark-theme")
        $("#navbar .menu").addClass("bgLite");
    });
  },
  methods: {
    handhleChange(e) {
      this.isDarkMode = e.target.checked;
      localStorage.setItem(
        "THEME",
        e.target.checked ? "dark-theme" : "light-theme"
      );
      if (window.scrollY > 20) {
        $("#navbar").removeClass();
        if (e.target.checked) {
          $("#navbar").addClass("dark-sticky");
          $("#navbar .menu").removeClass("bgLite");
        } else {
          $("#navbar").addClass("sticky");
          $("#navbar .menu").addClass("bgLite");
        }
      } else {
        if (e.target.checked) $("#navbar .menu").removeClass("bgLite");
        else $("#navbar .menu").addClass("bgLite");
      }
      this.$emit("handleThemeChange", e.target.checked);
    },
  },
};
</script>