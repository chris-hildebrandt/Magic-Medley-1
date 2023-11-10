<template>
  <header class="">
    <!-- <Navbar /> -->
  </header>

  <main class="container-fluid">
    <router-view />
  </main>

  <Modal>
    <CardModal id="card-modal" />
  </Modal>
</template>

<script>
import { computed, onMounted } from "vue";
import { AppState } from "./AppState";
import { cardsService } from "./services/CardsService.js";
import Modal from "./components/Modals/Modal.vue";
import CardModal from "./components/Modals/CardModal.vue";

export default {
    name: "App",
    setup() {
        async function alphaSearch() {
            const search = "set:lea";
            await cardsService.getAlphaSearch(search);
        }
        onMounted(() => {
            alphaSearch();
        });
        return {
            appState: computed(() => AppState),
        };
    },
    components: { Modal, CardModal }
};
</script>
<style lang="scss">
*::-webkit-scrollbar {
  display: none;
}

@import "./assets/scss/main.scss";
</style>
