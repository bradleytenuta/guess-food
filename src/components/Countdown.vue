<template>
  <div class="row text-h2 text-center q-mt-xl countdown-container">
    <div class="col q-pa-sm">
      {{ days }}
    </div>
    <div class="col q-pa-sm">
      {{ hours }}
    </div>
    <div class="col q-pa-sm">
      {{ minutes }}
    </div>
    <div class="col q-pa-sm">
      {{ seconds }}
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import moment from "moment";

export default defineComponent({
  mounted() {
    window.setInterval(() => {
      this.now = moment().unix();
    }, 1000);
  },
  props: {
    date: {
      type: String,
    },
  },
  data() {
    return {
      now: moment().unix(),
    };
  },
  computed: {
    timeTillEvent() {
      var timeTillEvent = moment.duration(
        (moment(this.date, "YYYY-MM-DD hh:mm:ss").unix() - this.now) * 1000,
        "milliseconds"
      );
      return moment.duration(timeTillEvent - 1000, "milliseconds");
    },
    seconds() {
      return this.formatForDoubleDigits(this.timeTillEvent.seconds());
    },
    minutes() {
      return this.formatForDoubleDigits(this.timeTillEvent.minutes());
    },
    hours() {
      return this.formatForDoubleDigits(this.timeTillEvent.hours());
    },
    days() {
      return this.formatForDoubleDigits(this.timeTillEvent.days());
    },
  },
  methods: {
    formatForDoubleDigits: function (value) {
      if (value < 0) {
        return "00";
      }
      if (value.toString().length <= 1) {
        return `0${value}`;
      }
      return value;
    },
  },
});
</script>
