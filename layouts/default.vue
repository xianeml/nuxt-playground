<template>
  <v-app id="inspire">
    <!-- 메뉴 바 -->
    <v-navigation-drawer v-model="drawer" app permanent>
      <v-list>
        <!-- 프로필이미지 -->
        <v-list-item>
          <v-list-item-avatar>
            <v-img
              src="https://github.com/xianeml/mini-portfolio/blob/master/Img/pic.jpg?raw=true"
            ></v-img>
          </v-list-item-avatar>
        </v-list-item>
        <!-- 사용자 정보 -->
        <v-list-item link>
          <v-list-item-content>
            <v-list-item-title class="title"> Mihyun </v-list-item-title>
            <v-list-item-subtitle>@xianeml</v-list-item-subtitle>
          </v-list-item-content>
          <!-- 드롭다운 가능 -->
          <v-list-item-action>
            <v-icon>mdi-menu-down</v-icon>
          </v-list-item-action>
        </v-list-item>
      </v-list>

      <v-divider></v-divider>

      <!-- 메뉴 리스트 -->
      <v-list nav dense>
        <v-list-item-group color="primary">
          <v-list-item v-for="menu in menus" :key="menu.id">
            <!-- 메뉴 아이콘 -->
            <v-list-item-icon v-if="!menu.submenus"
              ><v-icon v-text="menu.icon"></v-icon
            ></v-list-item-icon>
            <!-- 메뉴명-->
            <v-list-item-content v-if="!menu.submenus">
              <v-list-item-title v-text="menu.title"></v-list-item-title>
            </v-list-item-content>

            <!-- 서브메뉴 테스트-->
            <v-list-group v-if="menu.submenus" :value="true" sub-group>
              <template #activator>
                <v-list-item-content>
                  <v-list-item-title>{{ menu.title }}</v-list-item-title>
                </v-list-item-content>
              </template>
              <v-list-item
                v-for="[id, title, icon] in menu.submenus"
                :key="id"
                link
              >
                <v-list-item-icon>
                  <v-icon v-text="icon"></v-icon>
                </v-list-item-icon>
                <v-list-item-title v-text="title"></v-list-item-title>
              </v-list-item>
            </v-list-group>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <!-- 상단바 -->
    <v-app-bar app>
      <!-- 아이콘 -->
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <!-- 타이틀 -->
      <v-toolbar-title>Vuetify 연습</v-toolbar-title>
    </v-app-bar>

    <!-- 메인 영역 -->
    <v-main> </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: null,
      menus: [
        { id: 1, title: 'Dashboard', icon: 'mdi-view-dashboard' },
        { id: 2, title: '사용자 관리', icon: 'mdi-image' },
        { id: 3, title: '메뉴관리', icon: 'mdi-help-box' },
        {
          id: 4,
          title: 'parent',
          icon: 'mdi-help-box',
          submenus: [
            ['5', 'Management', 'mdi-account-multiple-outline'],
            ['6', 'Settings', 'mdi-cog-outline'],
          ],
        },
      ],
      right: null,
    }
  },
}
</script>
