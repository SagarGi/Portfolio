<template>
  <div class="main-body" :class="modeType">
    <div class="main-body-wrapper">
      <div class="content">
        <div class="my-information">
          <div class="heading">
            <h2>Hello World !!</h2>
            <img
              v-if="modeType === 'light'"
              class="hand-wave"
              src="./assets/images/wave-black.png"
              alt="wave-hand"
            />
            <img
              v-else
              class="hand-wave"
              src="./assets/images/wve-white.png"
              alt="wave-hand"
            />
          </div>
          <div class="information">
            <p>I am sagar gurung,</p>
            <p>programmer | test automation engineer</p>
            <div class="heading-with-image">
              <p>working from</p>
              <img src="./assets/images/nepal.png" alt="nepal" />
              <img src="./assets/images/baoudha.png" alt="boudha" />
            </div>
          </div>
        </div>
        <div class="robot-image">
          <img class="robot" src="./assets/images/robot.gif" alt="robot-head" />
        </div>
      </div>
      <div class="thumps-up">
        <p>{{ this.likes }}</p>
        <span class="give-like" @click="giveALike"
          ><i class="fas fa-thumbs-up"></i
        ></span>
      </div>
      <div class="follow-down">
        <span class="follow-down-icon"
          ><i class="fas fa-angle-double-down"></i
        ></span>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  props: ["modeType"],
  name: "ContentComponent",
  data() {
    return {
      likes: 0,
      baseServerUrl: "https://dark-jade-horse-belt.cyclic.app/",
    };
  },
  async created() {
    this.likes = await this.getLikes();
  },
  methods: {
    async getLikes() {
      try {
        const result = await axios.get(this.baseServerUrl + "/like/get-likes");
        return result.data.likes;
      } catch (e) {
        console.error(e);
      }
    },
    async giveALike() {
      try {
        const response = await axios.put(this.baseServerUrl + "/like/add-like", {
          likes: this.likes,
        });
        if(response.status === 201) {
          this.likes++;
        }
      } catch (e) {
        console.error(e);
      }
    },
  },
};
</script>
<style scoped>
.main-body {
  height: 65vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-body-wrapper {
  width: 100%;
}
.content {
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  column-gap: 60px;
  flex-wrap: wrap;
  height: auto;
}

.heading {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 210px;
}

.information {
  padding: 10px 0;
}

.information,
p {
  color: #7e7e7e;
  padding: 10px 0;
}

.heading-with-image {
  display: flex;
  justify-content: start;
  align-items: self-start;
}

.heading-with-image img {
  width: 22px;
  height: 22px;
  padding-left: 4px;
  padding-top: 5px;
}

.robot-image {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-bottom: 70px;
}

.robot {
  width: 250px;
}

.hand-wave {
  width: 45px;
  height: 40px;
  animation-name: wave-animation;
  animation-duration: 2.5s;
  animation-iteration-count: infinite;
  transform-origin: 70% 70%;
  display: inline-block;
}

.thumps-up {
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  column-gap: 10px;
  height: 10vh;
}

.thumps-up,
img:hover {
  cursor: pointer;
}

.give-like {
  height: 50px;
  width: 50px;
  background-color: #ff4539;
  border-radius: 35px;
  text-align: center;
  line-height: 45px;
  color: white;
  font-size: 18px;
}
.give-like i {
  transition: all 0.3s linear;
}

.give-like:hover i {
  transform: scale(1.5);
}

.follow-down {
  display: flex;
  justify-content: center;
  align-items: end;
  height: 10vh;
}

.follow-down i {
  font-size: 15px;
}

.follow-down-icon {
  display: inline-block;
  position: relative;
  -moz-animation: bounce 0.5s infinite linear;
  -o-animation: bounce 0.5s infinite linear;
  -webkit-animation: bounce 0.5s infinite linear;
  animation: bounce 0.5s infinite linear;
}

.dark p {
  color: white;
}

/* Responsive layout - makes a one column-layout instead of two-column layout */
@media (max-width: 800px) {
  .main-body {
    height: auto;
  }
}

@keyframes wave-animation {
  0% {
    transform: rotate(0deg);
  }
  10% {
    transform: rotate(14deg);
  }
  20% {
    transform: rotate(-8deg);
  }
  30% {
    transform: rotate(14deg);
  }
  40% {
    transform: rotate(-4deg);
  }
  50% {
    transform: rotate(10deg);
  }
  60% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(0deg);
  }
}

@-webkit-keyframes bounce {
  0% {
    top: 0;
  }
  50% {
    top: -0.2em;
  }
  70% {
    top: -0.3em;
  }
  100% {
    top: 0;
  }
}
@-moz-keyframes bounce {
  0% {
    top: 0;
  }
  50% {
    top: -0.2em;
  }
  70% {
    top: -0.3em;
  }
  100% {
    top: 0;
  }
}
@-o-keyframes bounce {
  0% {
    top: 0;
  }
  50% {
    top: -0.2em;
  }
  70% {
    top: -0.3em;
  }
  100% {
    top: 0;
  }
}
@-ms-keyframes bounce {
  0% {
    top: 0;
  }
  50% {
    top: -0.2em;
  }
  70% {
    top: -0.3em;
  }
  100% {
    top: 0;
  }
}
@keyframes bounce {
  0% {
    top: 0;
  }
  50% {
    top: -0.2em;
  }
  70% {
    top: -0.3em;
  }
  100% {
    top: 0;
  }
}
</style>
