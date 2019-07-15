<template>
  <aside class="vuestic-sidebar">
    <vuestic-scrollbar>
      <ul class="sidebar-menu">
        <slot name="menu"></slot>
      </ul>
    </vuestic-scrollbar>
  </aside>
</template>

<script>
export default {
  name: 'vuestic-sidebar',
  props: {
    hidden: {
      type: Boolean,
      required: true,
    },
  },
}
</script>

<style lang="scss">
.vuestic-sidebar {
  @include media-breakpoint-down(md) {
    background-color: transparent;
    height: $sidebar-viewport-height-mobile;
    top: $sidebar-mobile-top;
    left: $sidebar-mobile-left;
    width: $sidebar-mobile-width;
    z-index: $sidebar-mobile-z-index;
    box-shadow: none;
  }

  background-color: $sidebar-bg;
  height: $sidebar-viewport-height;
  position: absolute;
  width: $sidebar-width;
  top: $sidebar-top;
  left: 0;
  transition: all 0.2s ease;
  opacity: 1;
  box-shadow: $sidebar-box-shadow;

  .vuestic-scrollbar {
    height: 100%;

    .sidebar-menu {
      max-height: 100%;
      margin-bottom: 0;
      list-style: none;
      padding-left: 0;
      li {
        display: block;
        padding-left: 0;
      }
    }

    .scrollbar-content {
      background: $sidebar-bg;
    }

  }

  &.sidebar-hidden {
    @include media-breakpoint-down(md) {
      top: $sidebar-hidden-top-mobile;
      opacity: 0;
      z-index: $sidebar-mobile-z-index;
      height: $sidebar-hidden-height-mobile;
    }
    top: $sidebar-hidden-top;
    opacity: 0;
    z-index: $min-z-index;
  }
  &.sidebar-hidden + .content-wrap {
    @include media-breakpoint-down(md) {
      margin-left: 0;
    }
    margin-left: $sidebar-left;
  }
}
</style>
