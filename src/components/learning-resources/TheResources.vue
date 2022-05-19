<template>
  <main>
    <BaseCard>
      <BaseButton
        @click="setSelectedTab('StoredResources')"
        :mode="storedResButtonMode"
        >Stored Resources</BaseButton
      >
      <BaseButton
        @click="setSelectedTab('AddResource')"
        :mode="addResButtonMode"
        >Add Resource</BaseButton
      >
    </BaseCard>
    <keep-alive>
      <component
        v-if="selecetedTab === 'StoredResources'"
        :is="StoredResources"
      />
      <component v-else :is="AddResource" />
    </keep-alive>
  </main>
</template>

<script setup>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';
import { ref, reactive, computed, provide } from 'vue';

const selecetedTab = ref('StoredResources');

function setSelectedTab(tab) {
  selecetedTab.value = tab;
}

const storedResButtonMode = computed(() => {
  return selecetedTab.value === 'StoredResources' ? null : 'flat';
});
const addResButtonMode = computed(() => {
  return selecetedTab.value === 'AddResource' ? null : 'flat';
});

const storedResources = reactive([
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
]);

function addResource(title, description, url) {
  const newResource = {
    id: new Date().toISOString(),
    title: title,
    description: description,
    link: url,
  };
  storedResources.unshift(newResource);
  selecetedTab.value = 'StoredResources';
}
function removeResource(resId) {
  const resIndex = storedResources.findIndex((res) => res.id === resId);
  storedResources.splice(resIndex, 1);
}

provide('resources', storedResources);
provide('addResource', addResource);
provide('removeResource', removeResource);
</script>

<style scoped>
main {
  padding: 1rem;
}
</style>
