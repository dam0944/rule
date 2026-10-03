<script setup>
import { ref, inject, onMounted, onBeforeUnmount } from "vue";
const changeLanguage = inject("changeLanguage");
const menuOpen = ref(false);
const closeOnEscape = (event) => {
  if (event.key === "Escape") menuOpen.value = false;
};
onMounted(() => document.addEventListener("keydown", closeOnEscape));
onBeforeUnmount(() => document.removeEventListener("keydown", closeOnEscape));
</script>
<template>
  <header class="top">
    <div class="in">
      <RouterLink class="brand" to="/"
        ><i>D</i
        ><span
          ><b><span class="en">DHARMASASTRA</span><span class="km">ធម្មសាស្ត្រ</span></b
          ><small
            ><span class="en">NOTARY PUBLIC</span
            ><span class="km">សារការីសាធារណៈ</span></small
          ></span
        ></RouterLink
      >
      <nav
        :class="{ 'is-open': menuOpen }"
        @click="menuOpen = false"
        id="main-navigation"
        aria-label="Main navigation"
      >
        <RouterLink to="/about"
          ><span class="en">Our Firm</span
          ><span class="km">អំពីការិយាល័យ</span></RouterLink
        >
        <RouterLink to="/#services"
          ><span class="en">Services</span><span class="km">សេវាកម្ម</span></RouterLink
        >
        <RouterLink to="/#notary"
          ><span class="en">Our Notary</span
          ><span class="km">សារការីរបស់យើង</span></RouterLink
        >
        <RouterLink to="/#prepare"
          ><span class="en">Before Your Visit</span
          ><span class="km">មុនពេលមក</span></RouterLink
        >
        <RouterLink to="/contact"
          ><span class="en">Contact</span><span class="km">ទំនាក់ទំនង</span></RouterLink
        >
      </nav>
      <button
        class="menu-toggle"
        type="button"
        aria-controls="main-navigation"
        :aria-expanded="menuOpen"
        @click="menuOpen = !menuOpen"
      >
        <span class="en">{{ menuOpen ? "Close" : "Menu" }}</span>
        <span class="km">{{ menuOpen ? "បិទ" : "ម៉ឺនុយ" }}</span>
        <span class="menu-icon" aria-hidden="true">
          <span></span>
          <span></span>
          <span></span>
        </span>
      </button>
      <div class="tools">
        <div class="switch">
          <label for="l-en" @click.prevent="changeLanguage('en')">EN</label
          ><span class="sep">|</span
          ><label for="l-km" @click.prevent="changeLanguage('km')">ខ្មែរ</label>
        </div>
        <RouterLink class="reqbtn" to="/contact"
          ><span class="en">Request an Appointment</span
          ><span class="km">ស្នើសុំការណាត់ជួប</span></RouterLink
        >
      </div>
    </div>
  </header>
</template>

<style scoped>
.menu-toggle {
  align-items: center;
  justify-content: center;
  gap: 10px;
  cursor: pointer;
}

.menu-icon {
  position: relative;
  display: inline-block;
  flex: 0 0 22px;
  width: 22px;
  height: 18px;
}

.menu-icon > span {
  position: absolute;
  left: 0;
  top: 8px;
  width: 100%;
  height: 2px;
  border-radius: 2px;
  background: currentColor;
  transform-origin: center;
  transition: transform 300ms cubic-bezier(0.4, 0, 0.2, 1), opacity 180ms ease;
}

.menu-icon > span:first-child {
  transform: translateY(-7px);
}

.menu-icon > span:last-child {
  transform: translateY(7px);
}

.menu-toggle[aria-expanded="true"] .menu-icon > span:first-child {
  transform: rotate(45deg);
}

.menu-toggle[aria-expanded="true"] .menu-icon > span:nth-child(2) {
  opacity: 0;
  transform: scaleX(0);
}

.menu-toggle[aria-expanded="true"] .menu-icon > span:last-child {
  transform: rotate(-45deg);
}

@media (max-width: 1100px) {
  .menu-toggle {
    display: inline-flex;
  }
}

@media (prefers-reduced-motion: reduce) {
  .menu-icon > span {
    transition: none;
  }
}
</style>
