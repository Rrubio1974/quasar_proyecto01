<template>
  <div class="col text-center text-positive">
    <h6>"Tu pones las ganas, nosotros la calidad"</h6>
  </div>
  <div class="q-pa-md">
    <q-carousel
      animated
      arrows
      v-model="slide"
      v-model:fullscreen="fullscreen"
      navigation
      infinite
      :autoplay="autoplay"
      transition-prev="slide-right"
      transition-next="slide-left"
      @mouseenter="autoplay = false"
      @mouseleave="autoplay = true"
    >
      <q-carousel-slide :name="1" img-src="https://thefoodtech.com/wp-content/uploads/2020/09/productos-naturales.jpg" />
      <q-carousel-slide :name="2" img-src="https://lh3.googleusercontent.com/proxy/fIC98o_DNff3Kq1SxI0p4KwhigSMT4DtS-o5BrJ8Vnlzr9KK_0RYswlO0eYBsoKlFz243E3UMC1hmJtv6my8GJEJAHjugHgxcjX368e5zO61Fr_q0hkCeHQ4Le6EEcGVi6YN5CR5_A" />
      <q-carousel-slide :name="3" img-src="https://www.industriaalimentaria.org/public/uploads/images/LEGUMBRES.jpg" />
      <q-carousel-slide :name="4" img-src="https://www.vegaffinity.com/comunidad/imagenes/articles/2471504792709.jpg" />

      <template v-slot:control>
        <q-carousel-control
          position="bottom-right"
          :offset="[18, 18]"
        >
          <q-btn
            push round dense color="white" text-color="primary"
            :icon="fullscreen ? 'fullscreen_exit' : 'fullscreen'"
            @click="fullscreen = !fullscreen"
          />
        </q-carousel-control>
      </template>
    </q-carousel>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      slide: ref(1),
      autoplay: ref(true),
      fullscreen: ref(false)
    }
  }
}
</script>
