<template>
  <BaseCard>
    <!-- '@click' FALLS THROUGH here -->
    <BaseButton
      @click="setSelectedTab('StoredResources')"
      :mode="storedResourceButtonMode"
    >
      Stored Resources</BaseButton
    >
    <BaseButton
      @click="setSelectedTab('AddResource')"
      :mode="addResourceButtonMode"
      >Add Resource</BaseButton
    >
  </BaseCard>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'StoredResources',
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
  provide() {
    return {
      resources: this.storedResources,
    };
  },
  computed: {
    storedResourceButtonMode() {
      return this.selectedTab === 'StoredResources' ? null : 'flat';
    },
    addResourceButtonMode() {
      return this.selectedTab === 'AddResource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>
