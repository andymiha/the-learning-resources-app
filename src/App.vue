<template>
  <ul>
    <ResourceItem
      v-for="resource in storedResources"
      :key="resource.id"
      :resource="resource"
    ></ResourceItem>
  </ul>
</template>

<script>
import ResourceItem from './components/learning-resources/ResourceItem.vue';

export default {
  components: {
    ResourceItem,
  },
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official Vue.js dodumentation.',
          link: 'https://cli.vuejs.org/#getting-started',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://www.google.com/',
        },
      ],
    };
  },
};
</script>
