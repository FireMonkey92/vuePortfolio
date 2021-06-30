<template>
  <div>
    <NavBar @handleThemeChange="handleThemeChange" />
    <HomeSectionStart :isDarkMode="isDarkMode ? isDarkMode : false" />
    <AboutSection :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Services />
    <Skills :isDarkMode="isDarkMode ? isDarkMode : false" />
    <Team />
      
    <section id="contact" class="contact">
    <div class="max-width">
    <h2 class="title">MediaRecorder API example</h2> 
    <p> For now it is supported only in Firefox(v25+) and Chrome(v47+)</p>
    <div class="contact-content">
       <div id='btns'>
       <button className="btn btn-primary mr-3" id='start'>Start</button>
       <button className="btn btn-primary" id='stop'>Stop</button>
       </div>
       <div>
       <ul className="list-unstyled" id='ul'></ul>
       </div>
    </div>
    </section>
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
  
  //VOICE RECORDING API
  
  // DOM and Variables
        let log = console.log.bind(console),
            id = val => document.getElementById(val),
            ul = id('ul'),
            start = id('start'),
            stop = id('stop'),
            stream,
            recorder,
            counter = 1,
            chunks,
            media;

        // Initialize RecordApi
        let mediaOptions = {
            audio: {
                tag: 'audio',
                type: 'audio/ogg',
                ext: '.ogg',
                gUM: { audio: true }
            }
        };
        media = mediaOptions.audio;
        navigator.mediaDevices.getUserMedia(media.gUM).then(_stream => {
            stream = _stream;
            id('btns').style.display = 'inherit';
            start.removeAttribute('disabled');
            recorder = new MediaRecorder(stream);
            recorder.ondataavailable = e => {
                chunks.push(e.data);
                if (recorder.state == 'inactive') makeLink();
            };
            log('got media successfully');
        }).catch(log);

        // Initiate Char Recording
        start.onclick = e => {
            start.disabled = true;
            stop.removeAttribute('disabled');
            chunks = [];
            recorder.start();
        }
        //  Stopped Chat Recording
        stop.onclick = e => {
            stop.disabled = true;
            recorder.stop();
            start.removeAttribute('disabled');
        }

        // append Download Link to the dom
        function makeLink() {
            let blob = new Blob(chunks, { type: media.type })
                , url = URL.createObjectURL(blob)
                , li = document.createElement('li')
                , mt = document.createElement(media.tag)
                , hf = document.createElement('a')
                ;
            mt.controls = true;
            mt.src = url;
            hf.href = url;
            hf.download = `${counter++}${media.ext}`;
            hf.innerHTML = `donwload ${hf.download}`;
            li.appendChild(mt);
            li.appendChild(hf);
            ul.appendChild(li);
        }
  
      
  },
};
</script>
