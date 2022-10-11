<template>
  <header>
    <ClearNavBar />
  </header>
  <!-- Gruul Clans Page -->
  <main class="row gruul p-5">
    <!-- NOTE Guild Members & Title & Join/Remove Button -->
    <!-- GUILD MEMBERS -->
    <section class="col-md-4">
      <button v-if="isMember == true" class="btn" type="button" data-bs-toggle="offcanvas"
        data-bs-target="#chat-off-canvas" aria-controls="chat-off-canvas">
        Chat With Guild Members
      </button>
      <ChatOffcanvas />
      <h4 class="my-2 mx-3">Guild Members</h4>
      <div class="d-flex">
        <div v-for="m in members" :key="m.id">
          <Member :member="m" />
        </div>
      </div>
    </section>
    <!-- GUILD TITLE -->
    <section class="col-md-4 text-center">
      <h1>{{ activeGuild.name }}</h1>
    </section>
    <!-- GUILD JOIN/REMOVE -->
    <section class="col-md-4 text-end">
      <button v-if="isMember == false" class="btn" @click="joinGuild()">
        <i class="mdi mdi-plus fs-3"></i>
        <span class="fs-5">Join Guild</span>
      </button>
      <button v-else class="btn" @click="removeFromGuild()">
        <i class="mdi mdi-minus fs-3"></i>
        <span class="fs-5">Leave Guild</span>
      </button>
    </section>

    <!-- NOTE Background & Map Row -->
    <div class="col-md-12">
      <div class="row justify-content-evenly">
        <section class="col-md-6 azorius-deck">





          <div class="accordion mt-3" id="accordionExample">
            <div class="accordion-item">
              <h2 class="accordion-header" id="headingOne">
                <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne"
                  aria-expanded="true" aria-controls="collapseOne">
                  <h4>
                    {{ activeGuild.name }} Background
                  </h4>
                </button>
              </h2>
              <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne"
                data-bs-parent="#accordionExample">
                <div class="accordion-body">
                  <span class="d-flex ">
                    Starter Deck:
                    <!-- Giant list of router links... -->
                    <p class="ms-3">
                      <!-- Gruul -->
                    <div v-if="activeGuild.id == '633f67b879b4cee7da9c9829'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fbd9a9268b4aaceff2c3b' } }">
                        Gruul Wildling
                      </router-link>
                    </div>
                    <!-- Simic -->
                    <div v-if="activeGuild.id == '633f676979b4cee7da9c981b'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fd64f9268b4aaceff30ff' } }">
                        Simic Mutology
                      </router-link>
                    </div>
                    <!-- Boros -->
                    <div v-if="activeGuild.id == '633f670e79b4cee7da9c97f9'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fd8df9268b4aaceff31a1' } }">
                        Charge of the Boros
                      </router-link>
                    </div>
                    <!-- Golgari -->
                    <div v-if="activeGuild.id == '633f669e79b4cee7da9c97eb'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fdc9d9268b4aaceff32b4' } }">
                        Golgari Deathcreep
                      </router-link>
                    </div>
                    <!-- Izzet -->
                    <div v-if="activeGuild.id == '633f5db679b4cee7da9c97c5'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fccb39268b4aaceff2fbe' } }">
                        Izzet Gizmometry
                      </router-link>
                    </div>
                    <!-- Orzhov -->
                    <div v-if="activeGuild.id == '633f5cba79b4cee7da9c97ad'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fd25f9268b4aaceff302c' } }">
                        Code of the Orzhov
                      </router-link>
                    </div>
                    <!-- Selesnya -->
                    <div v-if="activeGuild.id == '633f5c3e79b4cee7da9c9795'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fde9a9268b4aaceff3328' } }">
                        Selesnya United
                      </router-link>
                    </div>
                    <!-- Rakdos -->
                    <div v-if="activeGuild.id == '633f5bb579b4cee7da9c9787'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fd78c9268b4aaceff3149' } }">
                        Rakdos Bloodsport
                      </router-link>
                    </div>
                    <!-- Dimir -->
                    <div v-if="activeGuild.id == '633f5ad479b4cee7da9c976f'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fdb1a9268b4aaceff323a' } }">
                        Dimir Intrigues
                      </router-link>
                    </div>
                    <!-- Azorius -->
                    <div v-if="activeGuild.id == '633f5a6579b4cee7da9c9757'">
                      <router-link :to="{ name: 'DeckDetails', params: { deckId: '633fd3eb9268b4aaceff305b' } }">
                        Azorius Ascendant
                      </router-link>
                    </div>
                    </p>
                  </span>

                  {{activeGuild.background}}
                </div>
              </div>
            </div>
            <div class="accordion-item">
              <h2 class="accordion-header" id="headingTwo">
                <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse"
                  data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                  Map results
                </button>
              </h2>
              <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo"
                data-bs-parent="#accordionExample">
                <div class="accordion-body limit-size">
                  <p v-if="locations == null">
                    Please search for locations
                  </p>
                  <ul v-else v-for="l in locations" :key="l.name">
                    <li :location="l">{{l.name}} <br> {{l.formatted_address}}</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>

        </section>
        <!-- <div class="col-md-3">
          <div class="azorius-deck rounded d-flex justify-content-end align-items-end">
            <div class="azorius-glass-card fs-5 text-center rounded-bottom p-1">

            </div>
          </div>
        </div> -->
        <!-- MAP -->
        <section class="col-md-6">
          <MainMap />
        </section>
      </div>
    </div>
    <!-- NOTE Might need this to add starter decks -->
    <!-- <div class="col-1 position-absolute cardPosition" v-if="hover">
                <img :src="oracleCard.image_uris.small" alt="">
              </div> -->
  </main>
  <!-- CHAT -->
</template>

<script>
import { computed } from '@vue/reactivity';
import { onMounted } from 'vue';
import { useRoute, useRouter } from 'vue-router';
import { AppState } from '../AppState';
import { guildsService } from '../services/GuildsService';
import { membersService } from '../services/MembersService';
import { logger } from '../utils/Logger';
import Pop from '../utils/Pop';
import Member from '../components/Member.vue';
import GuildChat from '../components/GuildChat.vue';
import ClearNavBar from '../components/ClearNavBar.vue';
import Navbar from '../components/Navbar.vue';
import MainMap from '../components/MainMap.vue';

export default {
  setup() {
    const route = useRoute();
    const router = useRouter()
    async function getGuildById() {
      try {
        await guildsService.getGuildById(route.params.guildId);
        logger.log(AppState.activeGuild);
      }
      catch (error) {
        logger.error("[getting guild by id]", error);
        Pop.error(error);
      }
    }
    async function getGuildMembers() {
      try {
        await membersService.getGuildMembers(route.params.guildId);
      }
      catch (error) {
        logger.error("[getting guild members]", error);
        Pop.error(error);
      }
    }
    onMounted(() => {
      getGuildById();
      getGuildMembers()
    });
    return {
      locations: computed(() => AppState.locations),
      message: computed(() => AppState.messages),
      activeGuild: computed(() => AppState.activeGuild),
      members: computed(() => AppState.members),
      guilds: computed(() => AppState.guilds),
      cover: computed(() => `url(${AppState.activeGuild?.coverImg})`),
      cardImg: computed(() => `url(${AppState.activeGuild?.cardImg})`),
      userAddress: computed(() => AppState.account.location),
      isMember: computed(() => {
        if (AppState.members.find(m => m.accountId == AppState.account.id)) {
          return true
        }
        return false
      }),

      async joinGuild() {
        try {
          let newMember = {
            guildId: AppState.activeGuild.id,
            accountId: AppState.account.id
          };
          await membersService.joinGuild(newMember);
          Pop.success(`You've joined the ${AppState.activeGuild.name} Guild`);
          logger.log(AppState.members);
        }
        catch (error) {
          logger.error("[joining guild]", error);
          (error);
        }
      },

      async removeFromGuild() {
        try {
          const yes = await Pop.confirm(`Are you sure you want to leave the ${AppState.activeGuild.name} Guild?`)
          if (!yes) {
            return
          }
          const removedMember = AppState.members.find(m => m.accountId == AppState.account.id)
          await membersService.removeFromGuild(removedMember.id)
          router.push({
            name: "Guild",
          });
        } catch (error) {
          logger.error('[removing from guild]', error);
          Pop.error(error)
        }
      },

      scrollLeft() {
        let content = document.querySelector(".guild-cards-container");
        if (scrollPosition.value > 100) {
          scrollPosition.value -= 500;
        }
        content.scrollTo({
          left: scrollPosition.value,
          behavior: "smooth",
        });
      },

      scrollRight() {
        let content = document.querySelector(".guild-cards-container");
        if (scrollPosition.value < 1501) {
          scrollPosition.value += 500;
        }
        content.scrollTo({
          left: scrollPosition.value,
          behavior: "smooth",
        });
      },

    };
  },
  components: { Member, GuildChat, ClearNavBar, Navbar, MainMap }
};
</script>



<style scoped lang="scss">
.profile-pic {
  border-radius: 50%;
}

.gruul {
  color: whitesmoke;
  background-image: v-bind(cover);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  min-height: 100vh;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.gruul-bg {
  background: rgba(49, 49, 49, 0.5);
  text-shadow: 1px 1px 3px black;
  backdrop-filter: blur(5px);
  color: #f0f0f0 !important;
  border: none;
}

.azorius-bg {
  background: rgba(248, 231, 185, 0.8);
  text-shadow: 1px 1px 3px black;
  backdrop-filter: blur(5px);
  color: #f0f0f0 !important;
  border: none;
  width: 90%;
}

.limit-size {
  max-height: 50vh !important;
  overflow-y: scroll;
}

.btn:hover {
  border: none !important;
}

.azorius-glass-card {
  background: rgba(248, 231, 185, 0.8);
  backdrop-filter: blur(5px);
  width: 100%;
  height: 15%;
}

.azorius-deck {
  background-image: v-bind(cardImg);
  background-size: cover;
  background-position: center;
  // min-height: 20em;
  max-height: 75vh;
  // width: 75%;
  color: #0f0f0f !important;
  border-radius: 13px;
}

.buttonHeight {
  height: 100VH;
  height: 95VH;
  position: fixed;
  right: 0;
}

.btn {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
}

.simic {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Simic-Guildgate.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.boros {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Boros-Guildgate.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.golgari {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Golgari-Longlegs.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.izzet {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/izzet-guildgate.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.orzhov {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Guild-Orzhov.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.selesnya {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Selesnya-Guildgate.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.rakdos {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Rakdos-Guildgate.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.dimir {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Dimir-Guildgate.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

.azorius {
  text-shadow: 1px 1px 3px black;
  color: whitesmoke;
  background-image: url(../assets/img/mtg-guilds/Azorius-Guildgate.jpg);
  background-position: 50% 70%;
  background-size: cover;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  /* backdrop-filter: blur(4px); */
  /* border: solid #8d8b8b1f; */
  /* border-radius: 8px; */
}

// .columnHeight {

//   height: 10Vh;
// }
.guild-container-bg {
  background: rgb(54 52 75 / 38%);
  backdrop-filter: blur(4px);
  border: solid #8d8b8b1f;
  border-radius: 8px;
  padding: 1em;
}

.guild-cards-container {
  flex-wrap: nowrap;
  scroll-snap-type: x mandatory;
  max-width: 100vw;
  overflow-x: scroll;

  >div {
    scroll-snap-align: start;
    scroll-snap-stop: always;
  }
}

.button-style {
  color: #bd4362;
  font-size: 4em;
  padding: 0%;
}
</style>