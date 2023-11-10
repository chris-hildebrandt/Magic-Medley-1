<template>
  <nav class="navbar navbar-expand-lg px-3 mx-0 my-0 py-0 navHeight bg-clear">
    <router-link class="navbar-brand d-flex" :to="{ name: 'Home' }">
      <div class="d-flex flex-column align-items-center" title="Home">
        <img alt="logo" src="../assets/img/FullLogo_Transparent_NoBuffer.png" height="55" />
      </div>
    </router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText"
      aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon" />
    </button>
    <div class="collapse navbar-collapse" id="navbarText">
      <ul class="navbar-nav me-auto">
        <li>
          <router-link :to="{ name: 'Collection' }"
            class="btn img-text lighten-30  text-uppercase square buttonPadding">
            Collection
          </router-link>
        </li>
        <li>
          <router-link :to="{ name: 'Search' }"
            class="btn img-text lighten-30  text-uppercase square buttonPadding">
            Search
          </router-link>
        </li>
        <li>
          <router-link :to="{ name: 'Guild' }"
            class="btn img-text lighten-30  text-uppercase square buttonPadding">
            Guild
          </router-link>
        </li>
      </ul>
      <!-- <SearchForm /> -->
      <!-- LOGIN COMPONENT HERE -->
      <div class="me-5 pe-3 fs-4 no-select">
        <Login />
      </div>
    </div>
  </nav>
</template>

<script>
import SearchForm from "./SearchForm.vue";
export default {
  setup() {
    return {};
  },
  components: { SearchForm }
};
</script>

<style scoped lang="scss">
a:hover {
  text-decoration: none;
}

.nav-link {
  text-transform: uppercase;
}

.navbar-nav .router-link-exact-active {
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
}

.buttonPadding {
  padding-top: 21px;
  padding-bottom: 21px;
  border-bottom: none;
  border-top: none;
}

.navHeight {
  height: 10VH;
}

.bg-clear {
  background-color: rgba(255, 255, 255, 0.096);
  backdrop-filter: blur(10px);
}

.img-text {
  color: whitesmoke !important;
  text-shadow: 1px 1px 3px black !important;
}

.img-text:hover {
  background-color: rgba(0, 0, 0, 0.041);
  backdrop-filter: blur(5px);
    text-shadow: 1px 1px 3px black, 1px 1px 3px black;
}
</style>
