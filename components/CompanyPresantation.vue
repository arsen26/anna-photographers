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
        <v-hover v-slot="{ hover }">
          <v-card
            :elevation="hover ? 24 : plan.elevation"
            max-width="600"
            :class="hover ? 'zoom' : 'notzoom'"
            class="mx-auto transition-swing"
            height="600"
            theme="dark"
          >
            <!-- Check if the index is 0 before rendering the video -->
            <video
              v-if="ix === 0"
              autoplay
              muted
              loop
              style="width: 100%; height: 100%; object-fit: cover; z-index: -1"
            >
              <source src="photographyVideo.mp4" type="video/mp4" />
            </video>
            <!-- <v-card-title style="background-color: transparent">{{
              plan.title
            }}</v-card-title>
            <v-card-subtitle>{{ plan.description }}</v-card-subtitle> -->

            <video
              v-if="ix === 1"
              autoplay
              muted
              loop
              style="width: 100%; height: 100%; object-fit: cover"
            >
              <source src="decorVideo.mp4" type="video/mp4" />
            </video>
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
          description: 'test test test',
          elevation: 16,
          button: 'me kliko per me teper informacjone',
          src: 'photographyVideo.mp4',
        },
        {
          title: 'ANNA DECOR',
          description: 'test test test',
          elevation: 16,
          button: 'me kliko per me teper informacjone',
        },
      ],
    }
  },
}
</script>

<style scoped>
.video-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}
</style>
