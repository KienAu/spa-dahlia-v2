<script setup> 
const route = useRoute()
/**
 * Create correct slug and handle language parameter
 */
// Here we are getting the path as a URL parameter
let slug = []
if (route.query.path) {
  slug = route.query.path?.split('/')
} else {
  // fallback if no path parameter found (e.g. in template space)
  slug = route.params.slug.slice()
}
// In your project you would typically want to do the following:
// let slug = route.params.slug.slice()
let language = 'default'
if (slug) {
  language = await getLanguage(slug)
  // remove first slug entry if it matches query language
  if (language !== 'default') slug = slug.slice(1)
  slug = slug.join('/')
} else {
  slug = 'home'
}

const story = ref(null)
const storyblokApi = useStoryblokApi()
const { data } = await storyblokApi.get('cdn/stories/' + slug, {
  version: 'draft',
  language: language,
  fallback_lang: 'default',
  resolve_links: 'url',
})

story.value = data.story

</script>
 
<template>
  <StoryblokComponent v-if="story" :blok="story.content" />
</template>