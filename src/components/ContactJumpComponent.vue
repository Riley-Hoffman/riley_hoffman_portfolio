<template>
    <div class="iconContainer wrapper flexBox contactJump">
        <button
            class="styledButton"
            @="{
                click: jumpScroll,
                focus: contactJumpMoveOver,
                mouseover: contactJumpMoveOver,
            }"
        >
            Contact Me
        </button>
        <font-awesome-icon
            icon="arrow-down"
            aria-hidden="true"
            :class="
                !this.reduceMotion && {
                    animate__animated: this.hover,
                    animate__bounce: this.hover,
                }
            "
        />
    </div>
</template>
<script>
export default {
  data () {
    return {
      reduceMotion: window.matchMedia('(prefers-reduced-motion: reduce)')
        .matches,
      hover: false
    }
  },
  methods: {
    contactJumpMoveOver () {
      this.hover = true
    },
    jumpScroll () {
      const top = this.$el.offsetTop
      if (!this.reduceMotion) {
        window.scrollTo({
          behavior: 'smooth',
          top: top
        })
      } else {
        window.scrollTo({
          top: top
        })
      }
    }
  }
}
</script>
