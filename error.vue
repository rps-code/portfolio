<template>
  <main>
    <div class="flex justify-center items-center flex-col min-h-screen overflow-hidden">
      <div class="text-center space-y-8">
        <h1
          class="text-[clamp(4rem,20vw,16rem)] font-black !mt-0 bg-gradient-to-r from-purple-400 via-pink-400 to-cyan-400 bg-clip-text text-transparent leading-none tracking-tighter animate-fade-in"
        >
          {{ error.statusCode }}
        </h1>

        <div class="space-y-4 max-w-2xl mx-auto px-6">
          <h2 class="text-2xl md:text-3xl font-bold text-white/90 animate-slide-up">
            {{ error.statusCode === 404 ? 'Page Not Found' : 'Generic Error' }}
          </h2>

          <p
            class="text-lg text-white/60 leading-relaxed animate-slide-up"
            style="animation-delay: 0.2s"
          >
            <template v-if="error.statusCode === 404">
              The page you're looking for seems to have vanished into the digital void. But don't worry, we'll help you find your way back.
            </template>
            <template v-else>Something unexpected happened, and I'm sorry I let you down like this ::: {{ error.message || 'An error occurred' }}</template>
          </p>
        </div>

        <div
          class="animate-slide-up"
          style="animation-delay: 0.4s"
        >
          <NuxtLink
            to="/"
            class="text-3xl text-center no-underline leading-relaxed bg-gradient-to-t from-white to-white bg-no-repeat bg-[length:100%_1px] bg-[position:100%_100%] transition-all duration-300 hover:text-black hover:bg-[length:100%_100%] focus-visible:text-black focus-visible:bg-[length:100%_100%] text-white"
          >
            Go Home
          </NuxtLink>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
  const props = defineProps({ error: { type: Object, required: true } })

  useHead({
    title: () => props.error.statusCode
  })
</script>

<style scoped>
  @keyframes fade-in {
    from {
      opacity: 0;
      transform: scale(0.8);
    }
    to {
      opacity: 1;
      transform: scale(1);
    }
  }

  @keyframes slide-up {
    from {
      opacity: 0;
      transform: translateY(30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .animate-fade-in {
    animation: fade-in 1s ease-out;
  }

  .animate-slide-up {
    animation: slide-up 0.8s ease-out forwards;
    opacity: 0;
  }
</style>
