<template>
<main>
  <BaseCard>
    <BaseButton
      @click="setSelectedTab('StoredResources')"
      :mode="storedResButtonMode"
      >Stored Resources</BaseButton
    >
    <BaseButton @click="setSelectedTab('AddResource')" :mode="addResButtonMode"
      >Add Resource</BaseButton
    >
  </BaseCard>
  <keep-alive>
    <component :is="selecetedTab"></component>
  </keep-alive>
</main>
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
      selecetedTab: 'StoredResources',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'Official Vue.js documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selecetedTab === 'StoredResources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selecetedTab === 'AddResource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selecetedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResources.unshift(newResource);
      this.selecetedTab = 'StoredResources';
    },
    removeResource(resId) {
      const resIndex=this.storedResources.findIndex(res=>res.id===resId);
      this.storedResources.splice(resIndex,1);
    },
  },
};
</script>

<style scoped>
main {
  padding: 1rem;
}
</style>