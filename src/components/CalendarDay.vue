<template>
  <div class="calendar-day">
    <div class="date">{{ number }}</div>
    <div class="name">{{ name }}</div>
  </div>
</template>

<script>
export default {
  name: 'CalendarDay',
  props: {
    number: {
      type: Number,
      required: true
    },
    name: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles/config.scss';

.calendar-day {
  background-color: #fff;
  border: 1px solid #999;
  font-size: 11px;
  margin: 1px;
  padding: 0.5rem;
  box-sizing: border-box;
  @include breakpoint($mobile) {
    & > div {
      display: inline;
    }
  }
  @include breakpoint($medium) {
    display: inline-block;
    width: 100px;
  }
  .date {
    font-weight: bold;
    @include breakpoint($mobile) {
      margin-right: 0.5rem;
    }
  }
}
</style>
