<template>
  <div class="back-color">
    <section id="intro" class="py-16">
      <v-container>
        <v-responsive class="max-auto mx-auto text-center" max-width="600">
          <!--<v-avatar color="primary" size="70" class="mb-8">
          <v-icon x-large dark>mdi-web</v-icon>
        </v-avatar>-->
          <div class="text-h5 text-md-h6 text-center mb-7">
            Las mejores opciones <span class="subtitle"><b>para ti</b></span>
          </div>
          <!--<p class="title font-weight-light">
          ModeVue — is a carefully crafted multi-purpose, responsive, and
          gorgeous theme. Built with
          <strong>Vue.js</strong>
          and
          <strong>Nuxt.js</strong>, it comes with the features you need to
          quickly start developing your application.
        </p>-->
        </v-responsive>

        <v-row class="pt-12">
          <v-col v-for="card in cards" :key="card.title" cols="12" md="4">
            <v-row no-gutters>
              <v-col :cols="card.callout ? 9 : 12">
                <div class="pr-2">
                  <div class="text--disabled" v-text="card.subtitle"></div>
                  <h4
                    class="text-uppercase mt-1 mb-4"
                    style="letter-spacing: 0.15em"
                    v-text="card.title"
                  ></h4>
                  <p v-text="card.text"></p>
                </div>
              </v-col>
              <v-col v-if="card.callout" cols="2">
                <span
                  class="text-h3 grey--text font-weight-bold pr-8"
                  style="opacity: 0.1"
                  >{{ card.callout }}</span
                >
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: [
        {
          title: 'Seguros Personales',
          subtitle: '',
          text:
            'Especializados en el mercado de productos individuales y familiares',
          callout: '01',
        },
        {
          title: 'Seguros Comerciales',
          subtitle: '',
          text: 'Productos enfocados para Negocios, Empresas e Industrias',
          callout: '02',
        },
        {
          title: 'Fianzas',
          subtitle: '',
          text: 'Asesoría y apoyo para el cumplimiento de garantías',
          callout: '03',
        },
      ],
    }
  },
}
</script>

<style scoped>
.back-color {
  background-color: #e6e7e8;
  height: 360px;
}

.subtitle {
  color: #5687b7;
}
</style>
