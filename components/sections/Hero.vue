<template>
  <section id="hero">
    <v-carousel
      height="800"
      dark
      cycle
      show-arrows-on-hover
      draggable="true"
      hide-delimiter-background
    >
      <v-carousel-item
        v-for="(carousel, carindex) in carouselsData"
        :key="carindex"
        :src="carousel.src"
      >
        <v-container fill-height>
          <div style="max-width: 100%" class="text-center">
            <div class="text-md-h2 mb-3 text-sm-h3 text-h5 font-weight-black">
              {{ carousel.heading }}
            </div>
            <p class="mb-5">{{ carousel.subHeading }}</p>
            <v-btn :x-large="$vuetify.breakpoint.smAndUp" class="my-3 primary"
              >Get Started</v-btn
            >
            <span class="mx-2 my-4"></span>
            <v-btn
              :x-large="$vuetify.breakpoint.smAndUp"
              text
              class="my-3"
              outlined
              ><v-icon left large color="primary">mdi-play</v-icon>Learn
              More</v-btn
            >
          </div>
        </v-container>
      </v-carousel-item>
    </v-carousel>
  </section>
</template>

<script>
export default {
  data() {
    return {
      carouselsData: [
        {
          src: 'slider/SLIDER-1.jpg',
          heading: 'Agradecemos tu precensia estos 15 años de trayectoria',
          subHeading: ' ',
        },
        {
          src: 'slider/SLIDER-2.jpg',
          heading: 'Ofreciendote las mejores opciones en Protección',
          subHeading: ' ',
        },
        {
          src: 'slider/SLIDER-3.jpg',
          heading: 'Asegurando lo que más quieres',
          subHeading: ' ',
        },
        {
          src: 'slider/SLIDER-4.jpg',
          heading: 'Y cuidando de tu patrimonio',
          subHeading: '',
        },
      ],
    }
  },
}
</script>

<style>
.gradient-fill .v-responsive__content {
  background: rgb(0, 0, 0);
  background: linear-gradient(
    to right,
    rgba(3, 12, 41, 0.75),
    rgba(5, 11, 31, 0.65)
  );
}
</style>
