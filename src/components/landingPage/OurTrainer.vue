<!-- this component is for displaying the trainer information and social media contacts -->
<template>
  <div>
    <h2 class="font-weight-bold mb-2 text-center">Our Expert Trainers</h2>
    <p class="font-italic text-muted mb-4"></p>

    <div class="row pb-5 mb-4 d-flex justify-content-center">
      <div
        class="col-lg-3 col-md-6 mb-4 mb-lg-0"
        v-for="(trainer, index) in trainers"
        :key="index"
      >
        <!-- Card-->
        <div class="card shadow-sm border-1 rounded image-hover-effect">
          <div class="card-body p-0">
            <!-- trainer images -->
            <img :src="trainer.image" alt="" class="w-100 card-img-top" />
            <!-- trainer information -->
            <div class="p-4">
              <h5 class="mb-0">{{ trainer.name }}</h5>
              <p class="small text-muted">{{ trainer.position }}</p>
              <ul class="list-inline mb-0">
                <li class="list-inline-item">
                  <a
                    :href="facebookLink"
                    class="social-link"
                    aria-label="Facebook"
                  >
                    <font-awesome-icon :icon="icons.faFacebookF" />
                  </a>
                </li>
                <li class="list-inline-item">
                  <a
                    :href="twitterLink"
                    class="social-link"
                    aria-label="Twitter"
                  >
                    <font-awesome-icon :icon="icons.faTwitter" />
                  </a>
                </li>
                <li class="list-inline-item">
                  <a
                    :href="instagramLink"
                    class="social-link"
                    aria-label="Instagram"
                  >
                    <font-awesome-icon :icon="icons.faInstagram" />
                  </a>
                </li>
                <li class="list-inline-item">
                  <a
                    :href="linkedinLink"
                    class="social-link"
                    aria-label="LinkedIn"
                  >
                    <font-awesome-icon :icon="icons.faLinkedin" />
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {
  faFacebookF,
  faTwitter,
  faInstagram,
  faLinkedin,
} from "@fortawesome/free-brands-svg-icons";
import { library } from "@fortawesome/fontawesome-svg-core";

export default {
  created() {
    library.add(faFacebookF, faTwitter, faInstagram, faLinkedin);
  },
  components: {},
  data() {
    return {
      // card content
      icons: {
        faFacebookF: ["fab", "facebook-f"],
        faTwitter: ["fab", "twitter"],
        faInstagram: ["fab", "instagram"],
        faLinkedin: ["fab", "linkedin"],
      },
      facebookLink: "https://www.facebook.com",
      twitterLink: "https://twitter.com",
      instagramLink: "https://www.instagram.com",
      linkedinLink: "https://www.linkedin.com",
      trainers: [
        {
          image: "../assets/trainer/team1.png",
          name: "Mark Rockwell",
          position: "CEO - Consultant",
        },
        {
          image: "../assets/trainer/team2.png",
          name: "John Doe",
          position: "Fitness Trainer",
        },
        {
          image: "../assets/trainer/team3.png",
          name: "Jane Smith",
          position: "Yoga Instructor",
        },
      ],
    };
  },
};
</script>

<style scoped>
.social-link {
  width: 30px;
  height: 30px;
  border: 1px solid #ddd;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
  border-radius: 50%;
  transition: all 0.3s;
  font-size: 0.9rem;
}

.image-hover-effect:hover {
  transform: scale(1.1);
  transition: transform 0.3s ease-in-out;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
}

.social-link:hover,
.social-link:focus {
  background: #ddd;
  text-decoration: none;
  color: #555;
}

.social-link {
  width: 30px;
  height: 30px;
  margin: 8px;
  border: 1px solid #ddd;
  display: flex;
  align-items: center;
  justify-content: center;
  color: blue;
  border-radius: 50%;
  transition: all 0.3s;
  font-size: 0.9rem;
}

.social-link:hover,
.social-link:focus {
  background: red;
  text-decoration: none;
  color: white;
}

.progress {
  height: 10px;
}
</style>
