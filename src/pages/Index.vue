<template>
  <q-page>
    <!-- Timer -->
    <div class="row flex flex-center">
      <Countdown :date="dateOfDinner"></Countdown>
    </div>

    <!-- Messgae -->
    <div class="row flex flex-center">
      <h5 class="text-h5 text-center">Where are we going for food?</h5>
    </div>

    <!-- Image -->
    <div class="row flex flex-center" v-if="daysLeft > 2">
      <img src="~assets/clue1.png" />
    </div>
    <div class="row flex flex-center" v-if="daysLeft <= 2 && daysLeft > 1">
      <img src="~assets/clue2.png" />
    </div>
    <div class="row flex flex-center" v-if="daysLeft <= 1">
      <img src="~assets/clue3.png" />
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import Countdown from "components/Countdown.vue";
import moment from "moment";

export default defineComponent({
  name: "PageIndex",
  components: {
    Countdown,
  },
  data() {
    return {
      dateOfDinner: "2021-05-28 15:00:00",
      now: moment().unix(),
    };
  },
  mounted() {
    window.setInterval(() => {
      this.now = moment();
    }, 1000);
  },
  computed: {
    daysLeft() {
      return moment(this.dateOfDinner).diff(this.now, "days", true);
    },
  },
});
</script>
