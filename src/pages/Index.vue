<template>
  <q-page>
    <!-- Timer -->
    <div class="row flex flex-center">
      <Countdown date="2021-05-28 15:00:00"></Countdown>
    </div>

    <!-- Messgae -->
    <div class="row flex flex-center">
      <h5 class="text-h5 text-center">Where are we going for food?</h5>
    </div>

    <!-- Image -->
    <div class="row flex flex-center">
      <img alt="Quasar logo" src="~assets/clue1.png" />
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import Countdown from "components/Countdown.vue";

export default defineComponent({
  name: "PageIndex",
  components: {
    Countdown,
  },
});
</script>
