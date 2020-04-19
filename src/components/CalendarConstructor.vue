<template>
  <div class="calendar-constructor">
    <h1>Your 2020 calendar is...</h1>
    <div
      class="calendar-month"
      v-for="(month, index) in daysInMonth"
      :key="'month-' + index"
    >
      <h2>
        {{ randomMonth() }} <small>({{ index + 1 }})</small>
      </h2>
      <div class="days" :class="'prefix-' + month.prefix">
        <CalendarDay
          v-for="n in month.days"
          :number="n"
          :name="randomDay()"
          :key="'day-' + n"
        />
      </div>
    </div>
    <footer>
      A goofy ass thing by <a href="https://mraichelson.rocks/">@MRaichelson</a>
    </footer>
  </div>
</template>

<script>
import CalendarDay from '@/components/CalendarDay.vue'

export default {
  components: { CalendarDay },
  data() {
    return {
      daysInMonth: [
        { days: 31, prefix: 3 },
        { days: 28, prefix: 6 },
        { days: 31, prefix: 1 },
        { days: 30, prefix: 3 },
        { days: 31, prefix: 5 },
        { days: 30, prefix: 1 },
        { days: 31, prefix: 3 },
        { days: 31, prefix: 6 },
        { days: 30, prefix: 2 },
        { days: 31, prefix: 4 },
        { days: 30, prefix: 0 },
        { days: 31, prefix: 2 }
      ],
      months: {
        init: [
          'Ja',
          'Fe',
          'Mar',
          'Ap',
          'Ma',
          'Ju',
          'Aug',
          'Sep',
          'Oc',
          'Nov',
          'Dec'
        ],
        mid: ['nu', 'bru', 'ril', 'us', 'tem', 'b', 'tob', 'emb'],
        end: ['ary', 'y', 'ne', 'ch', 'ust', 'er']
      },
      days: {
        init: ['Mon', 'Tu', 'Wed', 'Thu', 'Fr', 'Sa', 'Su'],
        mid: ['es', 'nes', 'rs', 'id', 'tur', 'en']
      }
    }
  },
  methods: {
    randomDay() {
      const dayParts = this.days
      const parts = []
      parts.push(
        dayParts.init[Math.floor(Math.random() * dayParts.init.length)]
      )
      let dayLength = Math.floor(Math.random() * 2)
      for (let i = 0; i <= dayLength; i++) {
        parts.push(
          dayParts.mid[Math.floor(Math.random() * dayParts.mid.length)]
        )
      }
      parts.push('day')
      return parts.join('')
    },
    randomMonth() {
      const monthParts = this.months
      const parts = []
      parts.push(
        monthParts.init[Math.floor(Math.random() * monthParts.init.length)]
      )
      let nameLength = Math.floor(Math.random() * 2)
      for (let i = 0; i <= nameLength; i++) {
        parts.push(
          monthParts.mid[Math.floor(Math.random() * monthParts.mid.length)]
        )
      }
      parts.push(
        monthParts.end[Math.floor(Math.random() * monthParts.end.length)]
      )
      return parts.join('')
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles/config.scss';
h1 {
  font-size: 24px;
  text-align: center;
}
.calendar-month {
  background-color: #ddd;
  border: 1px solid #999;
  padding: 1px;
  @include breakpoint($mobile) {
    margin-bottom: 15px;
  }
  @include breakpoint($medium) {
    margin: 0 auto 1.5rem;
    width: 714px;
  }
  h2 {
    font-size: 16px;
    margin: 0.5rem 0;
    text-align: center;
    small {
      font-size: 12px;
      vertical-align: top;
    }
  }
  .days {
    @include breakpoint($medium) {
      &.prefix-1 > div:first-child {
        margin-left: 103px;
      }
      &.prefix-2 > div:first-child {
        margin-left: 205px;
      }
      &.prefix-3 > div:first-child {
        margin-left: 307px;
      }
      &.prefix-4 > div:first-child {
        margin-left: 409px;
      }
      &.prefix-5 > div:first-child {
        margin-left: 511px;
      }
      &.prefix-6 > div:first-child {
        margin-left: 613px;
      }
    }
  }
}
footer {
  font-size: 10px;
  padding: 0.5rem 0.5rem 1rem;
  text-align: center;
}
</style>
