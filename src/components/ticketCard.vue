<template>
  <ul class="ticket-list">
    <li class="ticket-element" v-for="ticket of tickets" :key="ticket.id">
      <div class="ticket__image-container">
        <div :class="ticket.labelColor" class="ticket__label">{{ ticket.label }}</div>
        <img class="ticket__image" :src="ticket.image" :alt="ticket.title">
      </div>
      <div class="ticket__content-container">
        <div class="ticket__time-container">
          <img class="ticket__time-image" :src="ticket.timeImage" :alt="ticket.title">
          <div class="ticket__time">{{ ticket.time }}</div>
        </div>
        <div class="ticket__title">{{ ticket.title }}</div>
        <div>
          <div class="ticket__details-list">
            <div class="ticket__details-element" v-for="detail in ticket.details" :key="detail.name">
              <img class="ticket__details-image" :src="ticket.checkImage" :alt="ticket.title">
              {{ detail }}
            </div>
          </div>
          <div class="ticket__flex-container">
            <div class="ticket__today">Ближайший рейс сегодня</div>
            <div class="ticket__times-container">
              <ul class="ticket__times-list">
                <li class="ticket__times-element" v-for="openTime in ticket.openTimes.slice(0,2)" :key="openTime.id">
                  {{ openTime.time }}
                </li>
              </ul>
              <ul v-show="this.showTimes"  class="ticket__times-list">
                <li class="ticket__times-element" v-for="openTime in ticket.openTimes.slice(2,100)" :key="openTime.id">
                  {{ openTime.time }}
                </li>
              </ul>
            </div>
            <div @click.prevent="remakeClass()" class="ticket__else-button">eще</div>
          </div>
        </div>
        <div class="ticket__price-and-button">
          <div class="ticket__price-container">
            <div class="ticket__price">{{ ticket.price }}<span>&#x20bd;</span></div>
            <div class="ticket__discount">{{ ticket.discount }}</div>
          </div>
          <button class="ticket__button">Подробнее</button>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>

import tickets from "@/data/tickets";

export default {
  data() {
    return {
      tickets,
      showTimes: false,
    }
  },
  methods: {
    remakeClass() {
      this.showTimes = !this.showTimes;
    },
  },
  computed: {}
}
</script>


