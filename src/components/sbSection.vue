<template>
  <section class="elevation-2 ma-1" :class="section.title">
    <span class="heading-wrapper" @click.prevent="sectionClick($vnode.key)" :title="section.title+' section'">
      <span>
          <v-icon class="ma-1">{{section.icon}}</v-icon>
          <h2 class="heading">{{section.title}}</h2>
      </span>
      <a
        href="#"
        :class="{closed: openSection !== $vnode.key}"
        :aria-expanded="openSection===$vnode.key"
        aria-label="read more"
      >
        <v-icon>keyboard_arrow_down</v-icon>
      </a>
    </span>
    <div
      :class="{closed: openSection !== $vnode.key}"
      class="sbSection"
      :aria-hidden="openSection !== $vnode.key"
    >
      <Skillbox
        v-for="(item,i) in section.items"
        :key="i+1"
        :skill="item"
        :open="openBox===(i+1)"
        @sbOpen="handleOpening"
        @sbClose="handleClose"
      />
    </div>
  </section>
</template>

<script>
import Skillbox from "../components/skillbox";

export default {
  name: "sbSection",
  components: {
    Skillbox
  },
  data: function() {
    return {
      openBox: 0
    };
  },
  props: {
    section: Object,
    openSection: Number
  },
  methods: {
    handleOpening: function(key) {
      this.openBox = key;
    },
    handleClose: function() {
      this.openBox = 0;
    },
    sectionClick: function(key) {
      this.$emit("sectionClick", key);
      // if (this.openSection === key) { this.openSection = 0 }
      // else { this.openSection = key }
    }
  }
};
</script>
<style scoped>
span {
    display: flex;
}
span.heading-wrapper {
  justify-content: space-between;
}
.heading-wrapper a {
  justify-self: flex-end;
  margin: 10px;
  text-decoration: none;
  display: flex;
  transition: 0.3s cubic-bezier(0.25, 0.8, 0.5, 1);
  transform: rotate(180deg);
}
.heading-wrapper a.closed {
  transform: rotate(0deg);
}
h2 {
  /* text-align: center; */
  margin: 10px;
  font-weight: 500;
  font-size: 1.5rem;
  text-transform: capitalize;
}
.heading {
  font-weight: 500;
}
div.sbSection {
  display: flex;
  flex-wrap: wrap;
  min-width: 344px;
  margin-top: 10px;
  justify-content: space-evenly;
  overflow: hidden;
  transition: all 0.5s ease-in-out;
  /* transition: opacity 0.2s linear; */
  max-height: 100vh;
  opacity: 1;
}
.sbSection.closed {
  opacity: 0;
  max-height: 0px;
}
</style>
