<template>
  <v-container fluid>
    <v-row class="mx-auto d-flex justify-center" style="max-width: 90%">
      <v-col
        v-for="(plan, ix) in teDhenat"
        :key="`plan-${ix}`"
        cols="12"
        md="6"
        lg="6"
      >
        <v-hover v-slot="{ hover }" class="card-container">
          <v-card
            style="
              align-items: center;
              justify-content: center;
              position: relative;
            "
            :elevation="hover ? 24 : plan.elevation"
            max-width="600"
            :class="hover ? 'zoom' : 'notzoom'"
            class="mx-auto transition-swing"
            height="600"
            theme="dark"
          >
            <!-- Your video and overlay styles -->
            <video
              autoplay
              muted
              loop
              style="width: 100%; height: 100%; object-fit: cover; z-index: -1"
            >
              <source :src="plan.src" type="video/mp4" />
            </video>
            <div
              style="
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background-color: rgba(0, 0, 0, 0.5);
              "
            ></div>

            <v-row
              class="d-flex justify-center align-center"
              style="height: 100%"
            >
              <v-card-title class="title-style">
                {{ plan.title }}
              </v-card-title>

              <v-card-subtitle class="description-style">
                {{ plan.description }}
              </v-card-subtitle>

              <v-row class="d-flex justify-center button-style">
                <v-btn> Zbulo me teper </v-btn>
              </v-row>
            </v-row>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      teDhenat: [
        {
          title: 'ANNA PHOTOGRAPHERS',
          description:
            'Ne jemi destinacioni juaj i duhur për sesione fotografike magjike. ',
          elevation: 16,
          button: 'me kliko per me teper informacjone',
          src: 'photographyVideo.mp4',
        },
        {
          title: 'ANNA DECOR',
          description:
            'Perjeto magjine e shnderrimit te imagjinates ne realitet',
          elevation: 16,
          button: 'me kliko per me teper informacjone',
          src: 'decorVideo.mp4',
        },
      ],
    }
  },
}
</script>

<style scoped>
.title-style {
  position: absolute;
  background-color: transparent;
  color: rgba(255, 255, 255, 0.9);
  font-family: 'Raleway', sans-serif;
  font-size: 35px;
  font-weight: 800;
  line-height: 72px;
  margin: 0 0 24px;
  text-align: center;
  top: 180px;
  text-transform: uppercase;
}
.description-style {
  position: absolute;
  background-color: transparent;
  color: rgba(255, 255, 255, 0.9); /* Red color with 50% opacity */
  font-family: 'Raleway', sans-serif;
  font-size: 13px;
  font-weight: 400;
  margin: 0 0 24px;
  text-align: center;
  top: 260px;
  text-transform: uppercase;
}

.button-style {
  position: absolute;
  top: 360px; /* Adjust the top position based on your layout */
  background-color: transparent;
  text-align: center;
  transition: transform 0.3s ease-in-out; /* Add a smooth transition effect */
}

.button-style:hover {
  transform: scale(1.1);
}
.card-container:hover {
  transform: scale(1.05);
}
</style>
