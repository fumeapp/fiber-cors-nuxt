<script lang="ts" setup>

const headers = ref(undefined)

const cors = () => $fetch('https://d245hvitoez60u.cloudfront.net/', {
  method: 'OPTIONS',
  onResponse({ response }) {
    console.log(request, response, options)
  },
})

const { data, refresh, status, error } = useFetch('https://d245hvitoez60u.cloudfront.net/')

</script>

<template>
  <div class="flex flex-col items-center justify-center gap-4 h-screen max-w-xl w-full mx-auto">
    <h1 class="font-bold text-2xl text-(--ui-primary)">
      fiber CORS test
    </h1>

    <div class="flex items-center gap-2">
      <UButton
        label="Refresh CORS"
        @click="cors"
      />

      <UButton
        label="Refresh GET"
        @click="refresh"
      />


      <UButton
        label="GitHub"
        color="neutral"
        variant="outline"
        icon="i-simple-icons-github"
        to="https://github.com/nuxt/ui"
        target="_blank"
      />
    </div>

    <UCard class="w-full">
      <template #header>
        <div class="flex justify-between">

        <UBadge color="neutral"> OPTIONS https://d245hvitoez60u.cloudfront.net/ </UBadge>
        <UButtonGroup>
          <UBadge>status</UBadge>
          <UBadge>{{  status }}</UBadge>
        </UButtonGroup>
        </div>
      </template>
      <pre> {{ headers }}</pre>
    </UCard>
 

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
      <pre> {{ data }}</pre>
      <template #footer> {{ headers }}</template>
    </UCard>
    <UAlert v-if="error" color="error" variant="subtle">
      <template #description>
        {{  error  }}
      </template>
      </UAlert>
  </div>
</template>
