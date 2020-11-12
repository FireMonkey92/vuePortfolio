
<template>
  <section class="contact" id="contact" :class="isDarkMode && ' dark-theme'">
    <div class="max-width">
      <h2 class="title">Contact me</h2>
      <div class="contact-content">
        <div class="column left">
          <div class="text">Get in Touch</div>
          <p>
            Lorem, ipsum dolor sit amet consectetur adipisicing elit.
            Dignissimos harum corporis fuga corrupti. Doloribus quis soluta
            nesciunt veritatis vitae nobis?
          </p>
          <div class="icons">
            <div class="row">
              <i class="fas fa-user"></i>
              <div class="info">
                <div class="head">Name</div>
                <div class="sub-title">Tanesh Patel</div>
              </div>
            </div>
            <div class="row">
              <i class="fas fa-map-marker-alt"></i>
              <div class="info">
                <div class="head">Address</div>
                <div class="sub-title">
                  At & post: Amalsad, Ta: Gandevi, Dist: Navsari, Pin: 396-310,
                  Gujarat
                </div>
              </div>
            </div>
            <div class="row">
              <i class="fas fa-envelope"></i>
              <div class="info">
                <div class="head">Email</div>
                <div class="sub-title">tanupatel92@gmail.com</div>
              </div>
            </div>
          </div>
        </div>
        <div class="column right">
          <div class="text">Message me</div>
          <form action="#">
            <div class="fields">
              <div class="field name">
                <input type="text" placeholder="Name" required />
              </div>
              <div class="field email">
                <input type="email" placeholder="Email" required />
              </div>
            </div>
            <div class="field">
              <input type="text" placeholder="Subject" required />
            </div>
            <div class="field textarea">
              <textarea
                cols="30"
                rows="10"
                placeholder="Message.."
                required
              ></textarea>
            </div>
            <div class="button">
              <button class="btn-primary">Send message</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  name: "Contact",
  props: ["isDarkMode"],
  data() {
    return {};
  },
};
</script>