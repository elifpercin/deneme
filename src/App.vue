<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipped flating temporary>
      <v-list dense>
        <v-row class="ma-2 mb-3">
          <v-icon class="mx-4 fab fa-battle-net" large> </v-icon>
          <v-toolbar-title class="align-center">
            <span class="title font-weight-bold-italic" style="color:dimgrey"
              >Elif Perçin</span
            >
          </v-toolbar-title>
        </v-row>
        <v-list-item v-for="item in items" :key="item.icon" link>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>
              {{ item.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click="drawer = !drawer"> </v-app-bar-nav-icon>
      <v-icon class="mx-4 fab fa-battle-net" large> </v-icon>
      <v-toolbar-title class="align-center">
        <span class="title font-weight-bold-italic" style="color:dimgrey"
          >Elif Perçin</span
        >
      </v-toolbar-title>
      <v-spacer> </v-spacer>

      <v-text-field
        placeholder="Araa"
        single-line
        append-icon="mdi-magnify"
        color="white"
        class="mt-2"
      />
      <v-spacer> </v-spacer>
      <v-btn class="ml-0" icon><v-icon>mdi-apps</v-icon></v-btn>
      <v-btn class="ma-2" icon><v-icon>mdi-bell</v-icon></v-btn>
      <div>
        <v-menu
          v-model="menu"
          :close-on-content-click="false"
          :nudge-width="250"
          offset-x
        >
          <template v-slot:activator="{ on }">
            <v-avatar size="50">
              <img
                v-on="on"
                src="https://api.adorable.io/avatars/285/abott@adorable.png"
              />
            </v-avatar>
          </template>
          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar></v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title>ELİF PERÇİN</v-list-item-title>
                  <v-list-item-subtitle>açıklama</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider></v-divider>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-action>
                <v-list-item-title>Ayarlar</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-divider></v-divider>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-switch v-model="theme" color="blue" />
                </v-list-item-action>
                <v-list-item-title>Tema Seçimi</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer />
              <v-btn color="primary" text @click="menu = false">Çıkış"</v-btn>
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <v-content>
      <v-container>
        <v-row class="mb-4">
          <v-col
            sm="6"
            md="4"
            lg="3"
            xl="2"
            v-for="(item, index) in 200"
            :key="index"
          >
            <v-card>
              <v-img
                height="200px"
                :src="`https://picsum.photos/500/300?image=${index + 1}`"
                :lazy-src="`https://picsum.photos/10/6?image=${index + 1}`"
              ></v-img>
              <v-list>
                <v-list-item>
                  <v-list-item-avatar> </v-list-item-avatar>
                  <v-list-item-content>
                    <v-list-item-title
                      class="ml-15 mb-0 mt-0"
                      style="text-align:right"
                      >{{ index + 1 }}.resim</v-list-item-title
                    >
                    <v-btn
                      color="primary"
                      class="ml-15 mb-0 mt-6"
                      height="5px"
                      text
                      >Çıkış</v-btn
                    >
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    items: [
      { icon: "mdi-trending-up", text: "içerik" },
      { icon: "mdi-youtube-subscription", text: "takip" },
      { icon: "mdi-playlist-play", text: "geçmiş" },
    ],
    menu: false,
    theme: false,
    drawer: false,

    //
  }),
  watch: {
    theme: function(next) {
      this.$vuetify.theme.dark = next;
    },
  },
};
</script>
