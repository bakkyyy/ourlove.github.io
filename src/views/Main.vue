<template>
  <div class="main" id="main">
    <img class="image" src="@/assets/space.jpg" />
    <template v-for="(phrase, index) in phrases">
      <div
        class="item"
        :key="index"
        v-bind:style="{fontFamily:fonts[index % fonts.length], color:colors[index % colors.length]}"
      >{{phrase}}</div>
    </template>
    <div
      class="time"
      id="time"
    >{{years}} year {{days}} days {{hours}} hours {{minutes}} minutes {{seconds}} seconds</div>
  </div>
</template>

<script>
import moment from "moment";
import anime from "animejs/lib/anime.es.js";
import "@/styles/style.css";
export default {
  data() {
    return {
      firstdate: moment("2019-04-02 21"),
      seconds: 0,
      minutes: 0,
      hours: 0,
      days: 0,
      years: 0,
      time: 0,
      mainDate: setInterval(() => {
        this.seconds = moment(new Date()).diff(this.firstdate, "seconds") % 60;
        this.minutes = moment(new Date()).diff(this.firstdate, "minutes") % 60;
        this.hours = moment(new Date()).diff(this.firstdate, "hours") % 24;
        this.days = moment(new Date()).diff(this.firstdate, "days") % 365;
        this.years = moment(new Date()).diff(this.firstdate, "years");
      }),
      fonts: [
        "'Balsamiq Sans', cursive",
        "'Caveat', cursive",
        "'Pacifico', cursive",
        "'Balsamiq Sans', cursive",
        "'Didact Gothic', sans-serif",
        "'El Messiri', sans-serif",
        "'Lobster', cursive",
        "'Marck Script', cursive",
        "'Russo One', sans-serif"
      ],
      colors: [
        "#28262c",
        "#c44900",
        "#ef476f",
        "#ca7df9",
        "#724cf9",
        "#f7567c",
        "#1b9aaa",
        "#f8333c",
        "#44af69"
      ],
      phrases: [
        "Я тебя люблю",
        "Заюха",
        "Я тебя сильней люблю",
        "2 апреля",
        "Балбеска",
        "Зая",
        "Балбес",
        "9 мая",
        "Можно?",
        "Цеуууууй",
        "♥",
        "♂",
        "♀",
        "♫",
        "☼",
        "☺",
        "♥",
        "♥",
        ":*",
        "Заюха дурочка"
      ]
    };
  },
  methods: {
    animate: function randomValues() {
      anime({
        targets: ".item",
        translateX: function() {
          return anime.random(0, window.innerWidth);
        },
        translateY: function() {
          return anime.random(0, window.innerHeight);
        },
        rotate: function() {
          return anime.random(0, 360);
        },
        easing: "easeInOutQuad",
        duration: 10000,
        complete: randomValues
      });
      anime({
        targets: ".image",
        translateX: 100,
        duration: 60000,
        direction: "alternate",
        loop: true
      });
    }
  },
  mounted() {
    this.animate();
  }
};
</script>
