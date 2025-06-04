<script lang="ts" setup>
const data = ref(undefined)
const error = ref(undefined)
const get = async () => {
  const response = await $fetch('https://d245hvitoez60u.cloudfront.net/').catch(err => {
    error.value = err
  })
  data.value = response
}
onMounted(get)
</script>

<template>
  <div class="flex flex-col items-center justify-center gap-4 h-screen max-w-4xl w-full mx-auto">
    <h1 class="font-bold text-2xl text-(--ui-primary)">
      fiber CORS test
    </h1>

    <UCard class="w-full">
      <template #header>
        <div class="flex justify-between">
        <UBadge color="neutral"> GET https://d245hvitoez60u.cloudfront.net/ </UBadge>
        <UButton
          icon="i-mdi-refresh"
          @click="get"
        />
       </div>
      </template>
      <pre class="text-xs overflow-scroll"> {{ data }}</pre>
    </UCard>
    <UAlert v-if="error" color="error" variant="subtle">
      <template #description>
        {{  error  }}
      </template>
    </UAlert>
  </div>
</template>
