<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
    </q-toolbar>
    <div class="q-px-lg q-pt-xl q-mb-nd">
      <div class="text-h3">
        <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>

    </div>
    <q-img 
      src="statics/mountains.jpg"
      class="header-image absolute-top" />
      
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item
             to="/"
             exact
            clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>


            <q-item 
            to="/help"
            exact
            clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help page
              </q-item-section>
            </q-item>

           
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="static/mountain.jpg" style="height: 192px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://pbs.twimg.com/profile_images/1298034463180558336/9uf6mO1W_400x400.jpg">
            </q-avatar>
            <div class="text-weight-bold">Stelso Mphiri</div>
            <div>@StelsoMphiri</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <Keep-alive>
        <router-view />
      </Keep-alive>
        
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    };
    computed: {
      todaysDate(); { 
        let timeStamp = Date.now()
        return date.formatDate(timeStamp, 'dddd D MMMM')
 

      }
    }
  }
  
})
</script>

<style img="scss">
  .header-image{
    height: 100%;
    z-index: -1;
    opacity: 0,2;
    filter: grayscale(100%);
  }
</style>
