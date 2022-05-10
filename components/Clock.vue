<template>
  <div class="clock">
    <div class="clock__time">
      <span class="clock__time__hour">
        {{ time.getHours() }}</span>
      <span class="clock__time__colon">:</span>
      <span class="clock__time__minutes">
        {{ time.getMinutes().toString().length == 1 ? '0' : ''}}{{ time.getMinutes() }}</span>
      <span class="clock__time__seconds">{{ time.getSeconds().toString().length == 1 ? '0' : ''}}{{ time.getSeconds() }}</span>
    </div>
    <div class="clock__date">
      <span class="clock__date__dayname"> {{ getDayName() }}, </span>
      <span class="clock__date__datename">{{ time.getDate()}}. {{ getMonthName() }} {{time.getUTCFullYear()}} </span>
    </div>
  </div>
</template>

<script>
export default {
    name: "ClockComponent",
    data() {
        return {
            time: new Date(),
        }
    },
    methods: {
        clock: function() {
            setInterval(() => {
                this.time = new Date();
            }, 100);
        },
        getDayName: function() {
          const locale = "en-US";
          const weekday = this.time.toLocaleDateString(locale, {weekday: 'long'});
          return weekday;
        },
        getMonthName: function() {
          const locale = "en-US";
          const month = this.time.toLocaleDateString(locale, {month: 'long'});
          return month;
        }
    },
    created() {
        this.clock();
    }
}
</script>

<style>
</style>