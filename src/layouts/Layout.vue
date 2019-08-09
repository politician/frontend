<template>
  <q-layout view="hHh lpr fff">
    <q-header
      reveal
      class="bg-grey-2 text-grey-9"
    >
      <q-toolbar>
        <q-btn
          dense
          flat
          round
          icon="
      menu"
          @click="left = !left"
        />

        <q-toolbar-title>
          My SaaS
          <q-badge
            v-if="dev"
            color="deep-orange"
            align="top"
          >
            DEV
          </q-badge>
        </q-toolbar-title>

        <q-avatar
          class="cursor-pointer"
          @click="right = !right"
        >
          <img src="data:image/png;base64,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">
        </q-avatar>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="left"
      side="left"
      bordered
    >
      <Nav />
    </q-drawer>

    <q-drawer
      v-model="right"
      side="right"
      overlay
      bordered
    >
      <ProfileNav />
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer
      v-if="!($q.platform.is.electron || $q.platform.is.cordova)"
      elevated
      class="bg-grey-8 text-white"
    >
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
export default {
  name: 'Layout',
  components: {
    Nav: () => import('components/Nav/Nav.vue'),
    ProfileNav: () => import('components/Nav/ProfileNav.vue')
  },
  data () {
    return {
      left: true,
      right: true,
      dev: process.env.DEV
    }
  }
}
</script>
