<template>
  <section
    id="testimonials"
    :class="$vuetify.theme.dark ? 'black' : 'white'"
    class="py-16"
  >
    <h2 class="text-h4 text-md-h3 text-center font-weight-black mb-8 my-8">
      Vlersime nga klientet
    </h2>
    <v-col style="padding-top: 5px">
      <v-row>
        <div class="sk-ww-google-reviews" data-embed-id="25347530"></div>
        <script
          src="https://widgets.sociablekit.com/google-reviews/widget.js"
          async
          defer
        ></script></v-row
    ></v-col>
  </section>
</template>

<script>
export default {
  data() {
    return {
      testimonials: [
        {
          avtar: 'person-4.jpg',
          name: 'Mario Speedwagon',
          post: 'Creative Editor of ABC LTD',
        },
        {
          avtar: 'person-8.jpg',
          name: 'Petey Cruiser',
          post: 'CEO of Json LLC',
        },
        {
          avtar: 'person-7.jpg',
          name: 'Anna Sthesia',
          post: 'Director of Cleaner LTD',
        },
        {
          avtar: 'person-10.jpg',
          name: 'Paul Molive',
          post: 'Manager of Torson LTD',
        },
        {
          avtar: 'person-9.jpg',
          name: 'Gail Forcewind',
          post: 'Human Resource Manager of Humibed LLC',
        },
      ],
    }
  },
}
</script>
