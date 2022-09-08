<template>
  <v-app id="app">
    <v-app-bar app color="white" flat>
      <v-img max-width="150" src="http://app.baseplayground.com/img/logo-color.030d3d9e.png"></v-img>

      <v-spacer></v-spacer>

      <v-btn outlined>Locum Directory</v-btn>
      <v-avatar class="mr-1 ml-4" color="grey darken-1" size="32"></v-avatar>
      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on" text> user@user.com </v-btn>
        </template>

        <v-list>
          <v-list-item v-for="n in 5" :key="n" @click="() => {}">
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main class="grey lighten-4">
      <v-container fluid>
        <v-row>
          <v-col cols="2">
            <v-sheet rounded="lg" color="transparent">
              <v-list shaped two-line color="transparent">
                <v-list-item v-for="item in sideMenu" :key="n" link class="my-2 list-card">
                  <v-list-item-content>
                    <v-list-item-title class="mb-2"> {{ item.label }} </v-list-item-title>
                    <v-list-item-subtitle v-if="item.stats1">
                      <v-chip small class="mr-2">{{ item.stats1 }}</v-chip>
                      <v-chip small>{{ item.stats2 }}</v-chip>
                    </v-list-item-subtitle>
                  </v-list-item-content>
                  <v-list-item-action>
                    <v-icon v-if="!active" color="grey lighten-3"> mdi-star-outline </v-icon>

                    <v-icon v-else color="yellow darken-3"> mdi-star </v-icon>
                  </v-list-item-action>
                </v-list-item>

                <v-divider class="my-2"></v-divider>

                <v-list-item link class="list-card">
                  <v-list-item-content>
                    <v-list-item-title> Refresh </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-sheet>
          </v-col>

          <v-col>
            <v-sheet v-if="view === 'calender'" min-height="100vh" rounded="lg">
              <!--  -->
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import { defineComponent } from '@vue/composition-api'
import HelloWorld from './components/HelloWorld.vue'

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
  },
  data() {
    return {
      sideMenu: [
        {
          label: 'Upcoming Bookings',
          stats1: '2 - Oct 22',
          stats2: '4 - Nov 22',
        },
        {
          label: 'Requests Sent',
          stats1: '2 - Oct 22',
          stats2: '3 - Nov 22',
        },
        {
          label: 'Applications',
          stats1: '6 - Oct 22',
          stats2: '1 - Nov 22',
        },
        {
          label: 'Offers Posted',
          stats1: '2 - Oct 22',
          stats2: '4 - Oct 22',
        },
        {
          label: 'Booking History',
        },
      ],
    }
  },
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}

.list-card {
  background-color: white;
}
</style>
