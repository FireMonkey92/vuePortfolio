
<template>
  <section class="teams" id="teams">
    <div class="max-width">
      <h2 class="title">My teams</h2>
      <div class="carousel owl-carousel" v-if="team ? true : false">
        <div class="card" v-for="teamItem of team" :key="teamItem.id">
          <div class="box">
            <img v-bind:src="teamItem.image" alt="" />
            <div class="text">{{ teamItem.name }}</div>
            <p>{{ teamItem.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import img1 from "../assets/images/profile-1.jpeg";
import img2 from "../assets/images/profile-2.jpeg";
import img3 from "../assets/images/profile-3.jpeg";
import img4 from "../assets/images/profile-4.jpeg";
import img5 from "../assets/images/profile-5.jpeg";
export default {
  name: "Team",
  data() {
    return {
      team: [
        {
          id: 1,
          image: img1,
          name: "Some Name",
          desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          id: 2,
          image: img2,
          name: "Some Name",
          desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          id: 3,
          image: img3,
          name: "Some Name",
          desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          id: 4,
          image: img4,
          name: "Some Name",
          desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          id: 5,
          image: img5,
          name: "Some Name",
          desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
      ],
    };
  },
};
</script>