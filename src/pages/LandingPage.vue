<template>
  <div>
    <NavBar @handleThemeChange="handleThemeChange" />
    <HomeSectionStart :isDarkMode="isDarkMode ? isDarkMode : false" />
    <AboutSection :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Services />
    <Skills :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Team />
    <a id="download">Download</a>
<button id="stop">Stop</button>

    <Contact :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Footer :isDarkMode="isDarkMode ? isDarkMode : false" />
  </div>
</template>

<script>
import vue from "vue";
import NavBar from "../components/NavBar";
import HomeSectionStart from "../components/HomeSectionStart";
import AboutSection from "../components/AboutSection";
import Services from "../components/Services";
import Skills from "../components/Skills";
import Team from "../components/Team";
import Contact from "../components/Contact";
import Footer from "../components/Footer";
export default {
  name: "LandingPage",
  components: {
    NavBar,
    HomeSectionStart,
    AboutSection,
    Services,
    Skills,
    Team,
    Contact,
    Footer,
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
  methods: {
    handleThemeChange(valueFromChild) {
      console.log("valueFromChild", valueFromChild);
      this.isDarkMode = valueFromChild;
    },
  },
  mounted() {
    // navbar animation
    $(window).scroll(function () {
      // sticky navbar on scroll script
      if (this.scrollY > 20) {
        if (localStorage.getItem("THEME") === "dark-theme")
          $("#navbar").addClass("dark-sticky");
        else $("#navbar").addClass("sticky");
      } else {
        $("#navbar").removeClass();
      }
      // scroll-up button show/hide script
      if (this.scrollY > 500) {
        $(".scroll-up-btn").addClass("show");
      } else {
        $(".scroll-up-btn").removeClass("show");
      }
    });
    // slide-up script
    $(".scroll-up-btn").click(function () {
      $("html").animate({ scrollTop: 0 });
      // removing smooth scroll on slide-up button click
      $("html").css("scrollBehavior", "auto");
    });
    $("#navbar .menu li a").click(function () {
      // applying again smooth scroll on menu items click
      $("html").css("scrollBehavior", "smooth");
    });
    
    let shouldStop = false;
  let stopped = false;
  const downloadLink = document.getElementById('download');
  const stopButton = document.getElementById('stop');

  stopButton.addEventListener('click', function() {
    shouldStop = true;
  });

  const handleSuccess = function(stream) {
    const options = {mimeType: 'audio/webm'};
    const recordedChunks = [];
    const mediaRecorder = new MediaRecorder(stream, options);

    mediaRecorder.addEventListener('dataavailable', function(e) {
      if (e.data.size > 0) {
        recordedChunks.push(e.data);
      }

      if(shouldStop === true && stopped === false) {
        mediaRecorder.stop();
        stopped = true;
      }
    });

    mediaRecorder.addEventListener('stop', function() {
      downloadLink.href = URL.createObjectURL(new Blob(recordedChunks));
      downloadLink.download = 'acetest.wav';
    });

    mediaRecorder.start();
  };

  navigator.mediaDevices.getUserMedia({ audio: true, video: false })
      .then(handleSuccess);

    
  },
};
</script>
