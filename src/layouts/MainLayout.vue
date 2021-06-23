<template>
  <q-layout view="lHh Lpr lff">
      <q-header elevated class="bg-cyan-8">
        <q-toolbar class="text-center">
          <q-toolbar-title>Nowen</q-toolbar-title>
          <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        show-if-above
        :width="200"
        :breakpoint="400"
      >
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>

            <q-item clickable v-ripple to="/" active-class="my-menu-link" exact>
              <q-item-section avatar>
                <q-icon name="home" />
              </q-item-section>

              <q-item-section>
                Inicio
              </q-item-section>
            </q-item>

            <q-item active clickable v-ripple to="/productos" active-class="my-menu-link">
              <q-item-section avatar>
                <q-icon name="store_mall_directory" />
              </q-item-section>

              <q-item-section>
                Nuestros Productos
              </q-item-section>
            </q-item>

            <q-item active clickable v-ripple to="/form" active-class="my-menu-link">
              <q-item-section avatar>
                <q-icon name="add_shopping_cart" />
              </q-item-section>

              <q-item-section>
                Agregar Productos
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple to="/empresa" active-class="my-menu-link">
              <q-item-section avatar>
                <q-icon name="family_restroom"/>
              </q-item-section>

              <q-item-section>
                Nuestra Empresa
              </q-item-section>
            </q-item>

          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://cdn.quasar.dev/img/boy-avatar.png">
            </q-avatar>
            <div class="text-weight-bold">Nowen</div>
            <div>Productos Naturales</div>
          </div>
        </q-img>
      </q-drawer>

      <q-page-container>
        <router-view></router-view>
      </q-page-container>

      <q-footer class="bg-info text-white">
        <q-toolbar>
          <q-toolbar-title class="q-gutter-xs text-left">
            Derechos Reservados: Jacqueline Parra, Alexander Marcano, Rodrigo Rubio 
            <q-ico class="far fa-copyright"/>
            2021
          </q-toolbar-title>
          <div class="q-pa-md q-gutter-sm">
            <q-btn round color="primary" icon="fab fa-facebook-square" />
            <q-btn round color="secondary" icon="fab fa-twitter-square" />
            <q-btn round color="amber" icon="fab fa-whatsapp-square" />
            <q-btn round color="deep-orange" icon="fab fa-instagram-square" />
            <q-btn round color="secondary" icon="navigation" />
          </div>
        </q-toolbar>
      </q-footer>
    </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const drawer = ref(false)

    return {
      drawer
      
    }
  }
}
</script>

<style lang="sass">
.my-menu-link
  color: white
  background: #F2C037
</style>
