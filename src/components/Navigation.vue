<template>
  <transition name="fade">
    <header
      :class="
        scrolled
          ? 'transition-opacity duration-500 fixed w-full py-2 px-10 z-40 mx-auto bg-black'
          : 'transition-opacity duration-500 fixed w-full py-2 px-10 z-40 mx-auto'
      "
    >
      <div class="flex container-lg container-style justify-between items-center mt-1.5 mb-1">
        <div class="flex gap-1">
          <img
            class="w-40"
            src="../assets/images/Logo_svg_majchrak.svg"
            alt="logo majchrak"
          />
        </div>
        <nav>
          <ul class="flex gap-14">
            <li
              @click="$emit('scrollToSection', item.section)"
              v-for="item in navigationItems"
              :key="item.id"
              class="text-white text-xl font-normal cursor-pointer"
            >
              {{ item.title }}
            </li>
          </ul>
        </nav>
      </div>
    </header>
  </transition>
</template>

<script>
import { onMounted, onUnmounted, ref } from "vue";
export default {
  emits: ["scrollToSection"],
  setup() {
    const navigationItems = [
      { id: 1, title: "Domov", section: "home" },
      { id: 2, title: "Prečo my?", section: "whyUs" },
      { id: 3, title: "Naše stroje", section: "ourMachines" },
      { id: 4, title: "Kontakt", section: "contact" },
    ];

    const scrolled = ref(false);

    const handleScroll = () => {
      scrolled.value = window.pageYOffset > 0;
    };

    onMounted(() => {
      window.addEventListener("scroll", handleScroll);
    });

    onUnmounted(() => {
      window.removeEventListener("scroll", handleScroll);
    });

    return { navigationItems, scrolled };
  },
};
</script>
