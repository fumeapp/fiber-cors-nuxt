<script lang="ts" setup>
const { data, refresh, status, error } = useFetch('https://d245hvitoez60u.cloudfront.net/')
</script>

<template>
  <div class="flex flex-col items-center justify-center gap-4 h-screen max-w-4xl w-full mx-auto">
    <h1 class="font-bold text-2xl text-(--ui-primary)">
      fiber CORS test
    </h1>

    <div class="flex items-center gap-2">
      <UButton
        label="Refresh GET"
        @click="refresh"
      />
   </div>

    <UCard class="w-full">
      <template #header>
        <div class="flex justify-between">

        <UBadge color="neutral"> GET https://d245hvitoez60u.cloudfront.net/ </UBadge>
        <UButtonGroup>
          <UBadge>status</UBadge>
          <UBadge>{{  status }}</UBadge>
        </UButtonGroup>
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
