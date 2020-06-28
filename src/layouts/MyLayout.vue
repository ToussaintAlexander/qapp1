<template>
  <q-layout view="lHh Lpr lFf">
    <q-resize-observer @resize="onResize" />
    <q-header>
      <q-toolbar>
        <q-toolbar-title>
          codeguru.io
        </q-toolbar-title>
        <div class="gt-sm">
          <q-btn
            flat
            rounded
            label="Courses"
            class="q-mr-sm"
          />
          <q-btn
            outline
            rounded
            label="Sign Up"
            class="q-mr-sm"
            :to="{ path: 'signup' }"
          />
          <q-btn
            outline
            rounded
            label="Sign In"
            :to="{ path: 'signin' }"
          />
        </div>

        <div class="lt-md">
          <q-btn
            flat
            dense
            round
            @click="leftDrawerOpen = !leftDrawerOpen"
            icon="menu"
            aria-label="Menu"
          />

        </div>
      </q-toolbar>
    </q-header>
    <q-drawer
      v-model="leftDrawerOpen"
      bordered
      content-class="bg-grey-2"
    >
      <q-list>
        <q-item-label header>Essential Links</q-item-label>
        <q-item
          clickable
          tag="a"
          target="_blank"
          href="https://quasar.dev"
        >
          <q-item-section avatar>
            <q-icon name="school" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Courses</q-item-label>
            <q-item-label caption>quasar.dev</q-item-label>
          </q-item-section>
        </q-item>
        <q-item
          clickable
          tag="a"
          target="_blank"
          href="https://github.quasar.dev"
        >
          <q-item-section avatar>
            <q-icon name="code" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Sign Up</q-item-label>
            <q-item-label caption>github.com/quasarframework</q-item-label>
          </q-item-section>
        </q-item>
        <q-item
          clickable
          tag="a"
          target="_blank"
          href="https://chat.quasar.dev"
        >
          <q-item-section avatar>
            <q-icon name="chat" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Sign In</q-item-label>
            <q-item-label caption>chat.quasar.dev</q-item-label>
          </q-item-section>
        </q-item>
        <q-item
          clickable
          tag="a"
          target="_blank"
          href="https://forum.quasar.dev"
        >

        </q-item>
      </q-list>
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MyLayout',

  data () {
    return {
      leftDrawerOpen: false
    }
  },
  methods: {
    // openURL,
    onResize (size) {
      this.report = size
    },
    async signOut () {
      await this.$Auth
        .signOut()
        .then(data => console.log(data))
        .catch(err => console.log(err))
      this.signedIn = false
      parent.signedIn = false
      this.$router.push({ name: 'signout' })
    }
  }
}
</script>
