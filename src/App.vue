<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar class="custom-toolbar">
        <p class="toolbar-logo">Rindu Sakinah</p>
        <div class="toolbar-spacer"></div>
        <q-btn-dropdown class="custom-dropdown" label="Daftar Tugas" dropdown-icon="-">
          <q-list class="nav-list">
            <q-item clickable v-close-popup>
              <router-link to="/">
                <q-item-section>
                  <q-item-label class="custom-label">Weather</q-item-label>
                </q-item-section>
              </router-link>
            </q-item>
          </q-list>
        </q-btn-dropdown>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view></router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  setup() {}
};
</script>

<style scoped>
@import './assets/index.css';

.custom-toolbar {
  background: linear-gradient(to right, #ff758c, #ff7eb3);
  color: #ffffff;
  text-decoration: none;
  padding: 15px;
  display: flex;
  align-items: center;
}

.toolbar-logo {
  font-size: 16px;
  margin-right: 20px;
  border: 1px solid pink;
  border-radius: 10px;
  padding: 7px 7px;
}

.toolbar-spacer {
  flex-grow: 1;
}

.custom-dropdown {
  background: linear-gradient(to right, #ff758c, #ff7eb3);
  color: #ffffff;
  border: 1px solid pink;
  border-radius: 10px;
}

.nav-list {
  background: linear-gradient(to right, #ff758c, #ff7eb3);
  color: #ffffff;
}

.custom-label {
  color: #ffffff;
}

.nav-list .q-item-link {
  text-decoration: none;
}

.q-item-section {
  color: #ffffff !important;
}
</style>
