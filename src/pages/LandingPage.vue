<template>
  <div>
    <NavBar @handleThemeChange="handleThemeChange" />
    <HomeSectionStart :isDarkMode="isDarkMode ? isDarkMode : false" />
    <AboutSection :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Services />
    <Skills :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Team />
    <Contact :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Footer :isDarkMode="isDarkMode ? isDarkMode : false" />
  </div>
  <div id="chatmonday-container">
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
    
    
       chatImportHandler = () => {
    (function (t, a, s, k, p) {
      k = t.Promise; s = a.createElement("script"); s.src = `https://helenzystech.com/utm/talk_init.js`; s.async = true; a.head.appendChild(s);
      t.Talk = { v: 1, ready: { then: async function (f) { p = new k((res, rej) => { s.onload = res; s.onerror = rej; }); await k.all([p]); if (typeof f == "function") f(); } } };
    })(window, document);
    if (window.Talk)
      return window.Talk;
  }
  
   const Talk = chatImportHandler();
   Talk.ready.then(function () {
      _this.popup = null
      var user = new Talk.User({
        userid: `${currantUser.userid}`,
        imageURL: imageURL !== "" && imageURL !== null ? `${imageURL}` : getDefaultProfPic()
        // welcomeMessage: "Hey there! How are you? :-)"
      });
      var other = new Talk.User({
        userid: `${provider.userid}`,
        imageURL: provider.imageURL !== "" && provider.imageURL !== null ? `${provider.imageURL}` : getDefaultProfPic()
        // welcomeMessage: "Hey there! How are you? :-)"
      });
      var session = new Talk.Session({
        appid: CHATM_APPID,
        user: user
      })
      var conversation = session.getOrCreateConversation([user, other])
      var popup = new session.createPopup(conversation)
      popup.mount({show : true})    
  }  
  },
};
</script>
