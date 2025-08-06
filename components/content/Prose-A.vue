<template>
  <NuxtLink
    v-hoverable.action
    :href="href"
    class="project-link"
    target="_blank"
  >
    <ContentSlot
      :use="$slots.default"
      :unwrap="true"
    />
    <ArrowLink class="project-link__arrow-svg" />
  </NuxtLink>
</template>

<script setup>
  import ArrowLink from '~/assets/img/arrow-outer-link.svg'

  defineProps({
    href: { type: String, required: true }
  })
</script>

<style lang="scss">
  .project-link {
    --size: var(--step--1);

    display: inline-block;
    font: inherit;
    font-size: var(--size);
    color: var(--ff-color);
    text-decoration: none;
    opacity: 0.7;
    cursor: none;
    display: inline-flex;
    font-size: inherit;
    height: min-content;

    .project-link__arrow-svg {
      transform: scale(1.125);
    }

    &__arrow-svg {
      width: var(--size);
      height: auto;
      margin-left: 0.5rem;
      transform: translateY(15%);
    }
  }
</style>
