<template>
  <div>
    <NavBar />
    <HomeSectionStart />
    <AboutSection />
    <Services />
    <Skills />
    <Team />
    <Contact />
    <Footer />
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
};
</script>
