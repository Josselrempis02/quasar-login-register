<template>
  <div class="">
    <q-layout
      view="hHh Lpr lff"
      container
      style="height: 1000px"
      class="shadow-2 rounded-borders"
    >
      <q-header
        elevated
        :class="$q.dark.isActive ? 'bg-secondary' : 'bg-black'"
      >
        <q-toolbar>
          <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
          <q-toolbar-title>Header</q-toolbar-title>
          <q-space />
          <!-- Avatar Dropdown -->
          <q-avatar
            style="font-size: 40px"
            @click="menu = !menu"
            ref="avatarRef"
          >
            <img src="https://cdn.quasar.dev/img/avatar.png" />
          </q-avatar>
          <q-menu
            v-model="menu"
            :anchor="anchor"
            :self="self"
            fit
            cover
            no-caps
            ref="menuRef"
            class="menu"
          >
            <q-list style="min-width: 10px">
              <q-item clickable v-ripple>
                <q-item-section style="width: 30px">Settings</q-item-section>
              </q-item>
              <q-item clickable v-ripple>
                <q-item-section>Logout</q-item-section>
              </q-item>
            </q-list>
          </q-menu>
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        show-if-above
        :width="200"
        :breakpoint="500"
        bordered
        :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
      >
        <q-scroll-area class="fit">
          <q-list>
            <template v-for="(menuItem, index) in menuList" :key="index">
              <q-item
                clickable
                :active="menuItem.label === selectedMenuItem"
                v-ripple
                @click="selectMenuItem(menuItem.label)"
              >
                <q-item-section avatar>
                  <q-icon :name="menuItem.icon" />
                </q-item-section>
                <q-item-section>
                  {{ menuItem.label }}
                </q-item-section>
              </q-item>
              <q-separator :key="'sep' + index" v-if="menuItem.separator" />
            </template>
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <q-page padding>
          <div v-if="selectedMenuItem === 'Home'">
            <h1>Welcome to the Home Page!</h1>
            <p>
              This is the home page content that shows when you click "Home" in
              the menu.
            </p>
          </div>
          <div v-else-if="selectedMenuItem === 'Send Feedback'">
            <h1>Send Feedback</h1>
            <p>This is the feedback page content.</p>
          </div>
          <div v-else-if="selectedMenuItem === 'Help'">
            <h1>Help Page</h1>
            <p>This is the help page content.</p>
          </div>
        </q-page>
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>
import { ref } from "vue";

const menuList = [
  {
    icon: "inbox",
    label: "Home",
    separator: true,
  },
  {
    icon: "feedback",
    label: "Send Feedback",
    separator: false,
  },
  {
    icon: "help",
    iconColor: "primary",
    label: "Help",
    separator: false,
  },
];

export default {
  name: "UserIndex",
  setup() {
    const drawer = ref(false);
    const miniState = ref(true);
    const selectedMenuItem = ref("Home");
    const menu = ref(false);
    const anchor = ref("bottom right");
    const self = ref("top right");

    const selectMenuItem = (item) => {
      selectedMenuItem.value = item;
    };

    return {
      drawer,
      miniState,
      menuList,
      selectedMenuItem,
      selectMenuItem,
      menu,
      anchor,
      self,
    };
  },
};
</script>
<style>
.menu {
  width: 100%;
  max-width: 100px;
}
</style>
