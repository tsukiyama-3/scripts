<script lang="ts" setup>
import { useScriptGoogleTagManager } from '#nuxt-scripts/registry/google-tag-manager'
import { useHead } from '#imports'

useHead({
  title: 'Google Analytics',
})

// composables return the underlying api as a proxy object and the script state
const { proxy, onLoaded, status } = useScriptGoogleTagManager({
  id: 'GTM-MWW974PF',
}) // id is set via runtime config
proxy.dataLayer.push({
  event: 'page_view',
  page_title: 'Google Analytics',
  page_location: 'https://harlanzw.com/third-parties/google-analytics',
  page_path: '/third-parties/google-analytics',
})
onLoaded(({ google_tag_manager, dataLayer }) => {
  // eslint-disable-next-line no-console
  console.log('google_tag_manager is ready', google_tag_manager)
  // eslint-disable-next-line no-console
  console.log('google_tag_manager is ready', window.google_tag_manager)

  // eslint-disable-next-line no-console
  console.log('dataLayer', dataLayer)
  // eslint-disable-next-line no-console
  console.log(google_tag_manager['GTM-MNJD4B'].dataLayer.reset)
  // eslint-disable-next-line no-console
  console.log(google_tag_manager.dataLayer.gtmDom)

  dataLayer.push({
    event: 'pageview',
    page_path: '/google-tag-manager',
  })
})
</script>

<template>
  <div>
    <ClientOnly>
      <div>
        status: {{ status }}
      </div>
    </ClientOnly>
  </div>
</template>
