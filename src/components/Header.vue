<template>
  <header>
    <c-box mx="8" py="4" border-bottom="1px">
      <c-flex justify="space-between" align="center">
        <c-heading>
          <g-link to="/">{{ siteName }}</g-link>
        </c-heading>
        <c-box w="48">
          <c-flex align="center" justify="space-between">
            <g-link class="nav__link" to="/">Home</g-link>
            <g-link class="nav__link" to="/about/">About</g-link>
            <c-icon-button :icon="themeIcon" @click="toggleColorMode" />
          </c-flex>
        </c-box>
      </c-flex>
    </c-box>
  </header>
</template>
<script>
import { CFlex, CBox, CIconButton, CHeading } from "@chakra-ui/vue";

export default {
  inject: ["$chakraColorMode", "$toggleColorMode"],
  name: "AppHeader",
  components: {
    CBox,
    CFlex,
    CHeading,
    CIconButton,
  },
  props: {
    siteName: {
      type: String,
      default: () => "Gridsome",
    },
  },
  computed: {
    colorMode() {
      return this.$chakraColorMode();
    },
    toggleColorMode() {
      return this.$toggleColorMode;
    },
    themeIcon() {
      return this.colorMode === "light" ? "moon" : "sun";
    },
  },
};
</script>
