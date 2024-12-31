<template>
  <div class="flex flex-col justify-center max-w-7xl mx-auto p-16 px-8 sm:px-16 2xl:px-0">
  <div class="relative grid justify-center text-center items-center gap-16">
  <div class="relative mx-auto">
  <div class="circle-animation absolute -left-28 top-4">
  <div class="-z-10 w-[200px] h-[200px] rounded-full circle"></div></div></div>  
  <div class="relative outline-dashed smooth-transition outline-4 outline-offset-4 outline-[#D3C8FF] rounded-3xl mx-auto">
  <img src="/avatar.jpg" class="rounded-3xl w-32 h-32 "></div>
  <div class="grid gap-8 items-center">  
  <h1 class="font-[Onest] text-neutral-100 text-4xl font-semibold">hi , i'm <span class="text-white">Murchikov</span></h1>
  <p class="font-[Overpass] text-neutral-500 max-w-3xl font-medium text-lg">
  Hii!  I'm <code v-html="formattedAge"></code> years
  old. programmer, frontend & more! I go by he/him, and I like to make things on the internet :] I enjoy messing around with hardware too! I also play several video games, some of my favorites include Minecraft, Death Stranding, Valheim, webfishing & More :D
</p>
    </div>
       </div>
       </div>
                    
</template>
<script>
import Infobox from "~/components/Infobox.vue";
export default {
  components: { Infobox },
  data() {
    return {
      age: 0,
      birthTimestamp: 1226320320 * 1000,
      birthTimestamp: 1226320320 * 1000,
      increment: 0,
    };
  },
  computed: {
    formattedAge() {
      return this.age.toFixed(8);
    },
  },
  mounted() {
    this.calculateInitialAge();
    this.calculateIncrement();
    this.interval = setInterval(this.updateAge, 50);
  },
  beforeDestroy() {
    clearInterval(this.interval);
  },
  methods: {
    calculateInitialAge() {
      const now = Date.now();
      const ageInSeconds = (now - this.birthTimestamp) / 1000;
      this.age = ageInSeconds / (365.25 * 24 * 60 * 60);
    },
    calculateIncrement() {
      const secondsInYear = 365.25 * 24 * 60 * 60;
      const incrementPerUpdate = 50 / 1000;
      this.increment = incrementPerUpdate / secondsInYear;
    },
    updateAge() {
      this.age += this.increment;
    },
  },
};
</script>
