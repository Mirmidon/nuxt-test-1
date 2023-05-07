<script setup lang="ts">
useHead({
  script: [
    {
      id: 'chart-script',
      src: 'https://cdn.jsdelivr.net/npm/chart.js',
      defer: true,
    },
    {
      id: 'cesium-script',
      src: 'https://cesium.com/downloads/cesiumjs/releases/1.105/Build/Cesium/Cesium.js',
      defer: true,
    },
    {
      id: 'virtual-scroller',
      src: 'https://cdn.jsdelivr.net/npm/vue-virtual-scroller@1.1.2/dist/vue-virtual-scroller.umd.min.js',
      defer: true,
    },
  ],
  link: [
    {
      id: 'cesium-style',
      rel: 'stylesheet',
      href: 'https://cesium.com/downloads/cesiumjs/releases/1.105/Build/Cesium/Widgets/widgets.css',
    },
    {
      id: 'cesium-style',
      rel: 'stylesheet',
      href: 'https://cdn.jsdelivr.net/npm/vue-virtual-scroller@1.1.2/dist/vue-virtual-scroller.min.css',
    },
  ],
})

onMounted(() => {
})

const route = useRoute()
</script>

<template>
  <NuxtExampleLayout example="routing/pages">
    <NuxtLoadingIndicator />
    <NuxtPage />

    <template #nav>
      <nav class="flex align-center gap-4 p-4">
        <NuxtLink to="/" class="n-link-base">Home</NuxtLink>
        <NuxtLink to="/chart" class="n-link-base">Chart</NuxtLink>
        <NuxtLink to="/map" class="n-link-base">Map</NuxtLink>
        <NuxtLink to="/table" class="n-link-base">Table</NuxtLink>
        <NuxtLink to="/three-fiber" class="n-link-base">3D Scene</NuxtLink>
        <!-- <NuxtLink to="/about" class="n-link-base">About</NuxtLink> -->
        <!-- <NuxtLink to="/parent" class="n-link-base">Parent (index)</NuxtLink> -->
        <!-- <NuxtLink to="/parent/b" class="n-link-base">Parent (b)</NuxtLink> -->
        <!-- <NuxtLink to="/404" class="n-link-base">404</NuxtLink> -->
        <!-- <NuxtLink to="/?middleware" class="n-link-base">Middleware</NuxtLink> -->
        <!-- <button class="n-link-base" @click="$router.push(`/parent/reload-${(Math.random() * 100).toFixed()}`)">
          Keyed child
        </button>
        <button class="n-link-base" @click="$router.push(`/parent/static-${(Math.random() * 100).toFixed()}`)">
          Non-keyed child
        </button> -->
      </nav>
    </template>
    <template #footer>
      <div class="text-center p-4 op-50">
        Current route: <code>{{ route.path }}</code>
      </div>
    </template>
  </NuxtExampleLayout>
</template>
