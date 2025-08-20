<template>
  <main class="project-main">
    <ContentSlot :use="$slots.default" />
  </main>
</template>

<style lang="scss">
  .project-main {
    width: 100%;
    padding-top: 10rem;

    @media (max-width: 768px) {
      padding-top: 0;
    }
  }
</style>
