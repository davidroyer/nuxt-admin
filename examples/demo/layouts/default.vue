<template>
  <div>
    <b-navbar toggleable="md" variant="light">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
      <b-navbar-brand to="/">Firebase Auth - Nuxt Auth Module</b-navbar-brand>

      <b-collapse is-nav id="nav_collapse">
        <b-navbar-nav>
          <b-nav-item to="/" exact>Home</b-nav-item>
          <b-nav-item to="/public">Public</b-nav-item>
          <b-nav-item to="/secure">Secure</b-nav-item>
        </b-navbar-nav>
        <b-navbar-nav class="ml-auto">
          <template v-if="$auth.state.loggedIn">
            <b-nav-item-dropdown :text="$auth.state.user.name" right>
              <b-dropdown-item @click="$auth.logout()">Logout</b-dropdown-item>
            </b-nav-item-dropdown>
            <b-img :src="$auth.state.user.picture" class="mt-1" rounded="circle" width="30px" height="30px" />
          </template>
          <template v-else>
            <b-dropdown-item to="/login">Login</b-dropdown-item>
          </template>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <b-container class="mt-4">
      <nuxt />
    </b-container>
  </div>
</template>

<style>
.page-enter-active, .page-leave-active {
  transition: opacity .5s
}
.page-enter, .page-leave-active {
  opacity: 0
}
</style>
