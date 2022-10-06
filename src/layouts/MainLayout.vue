<template>
  <q-layout view="lHh Lpr lFf">
    <q-header >
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
        <img src="..//statics/Gurtam.logo.png" alt="logo" style=" width: 70px" >
      </q-toolbar>
      <div class="q-px-lg q-pt- q-mb-md">
        <div class="text-h3">Hardware</div>
        <div class="text-subtitle1"> {{todaysDate}} </div>
      </div>
      <q-img
       src="../statics/satellite.jpg"
       class="header-image absolute-top"/>
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="230"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 144px); margin-top: 144px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item
            to="/"
            exact
            clickable
             v-ripple>
              <q-item-section avatar>
                <q-icon name="home" />
              </q-item-section>

              <q-item-section>
                Home
              </q-item-section>
            </q-item>

            <q-item
            to="/Devices"
            exact
            clickable
             v-ripple>
              <q-item-section avatar>
                <q-icon name="devices" />
              </q-item-section>

              <q-item-section>
                Devices
              </q-item-section>
            </q-item>

            <q-item
            to="/People"
            exact
            clickable
             v-ripple>
              <q-item-section avatar>
                <q-icon name="people" />
              </q-item-section>

              <q-item-section>
                People
              </q-item-section>
            </q-item>

            <q-item
            to="/Settings"
            exact
            clickable
             v-ripple>
              <q-item-section avatar>
                <q-icon name="settings" />
              </q-item-section>

              <q-item-section>
                Drafts
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="..//statics/satellite.jpg" style="height: 144px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://cdn.quasar.dev/img/boy-avatar.png">
            </q-avatar>
            <div class="text-weight-bold">Admin</div>
            <div>admin@gurtam.com</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <router-view v-slot="{ Component }">
  <keep-alive>
    <component :is="Component" />
  </keep-alive>
</router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { date } from 'quasar'


export default ({
  name: 'MainLayout',

  computed: {
    todaysDate(){
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd D MMMM')
    }

  },

  components: {
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }

  }
})
</script>

<style lang="scss">
  .header-image {
   height: 100%;
   z-index: -1;
   opacity: 0.2;
   filter: grayscale(100%);


  }

</style>
