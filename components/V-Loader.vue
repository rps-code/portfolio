<template>
  <div
    ref="loader"
    class="bg-black w-full h-full z-10 absolute top-0 left-0"
  >
    <div class="loader">
      <div class="loader__dots"><span /><span /><span /></div>
    </div>
  </div>
</template>

<script setup>
  const loader = ref(null)

  const { gsap } = useGsap()
  const emitter = useEmitter()

  emitter.on('shader:running', () => {
    gsap.to(loader.value, {
      autoAlpha: 0,
      pointerEvents: 'none',
      onComplete: () => emitter.emit('loader:end')
    })
  })
</script>

<style lang="scss">
  .loader {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 10;
    pointer-events: all;

    &__dots {
      display: flex;
      gap: 16px;

      span {
        width: 20px;
        height: 20px;
        background: white;
        border-radius: 50%;
        animation: bouncePulse 1.4s infinite ease-in-out both;
        opacity: 0.7;
        transform-origin: center;

        &:nth-child(1) {
          animation-delay: -0.32s;
        }

        &:nth-child(2) {
          animation-delay: -0.16s;
        }

        &:nth-child(3) {
          animation-delay: 0;
        }
      }
    }
  }

  @keyframes bouncePulse {
    0%,
    80%,
    100% {
      transform: scale(0.7);
      opacity: 0.5;
    }
    40% {
      transform: scale(1.3);
      opacity: 1;
    }
  }
</style>
