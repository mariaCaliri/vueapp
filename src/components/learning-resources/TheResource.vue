<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resource')" :mode="storedResButton">Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resource')" :mode="addResButton">Add Resource</base-button>
    </base-card>
    <KeepAlive>
    <component :is="selectedTab"></component>
</KeepAlive>
</template>

<script>
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
    components: {
        StoredResource,
        AddResource
    },
   
    data() {
        return {
            selectedTab: 'stored-resource',
            storedResources: [
              {
                  id: 1,
                  name: 'Resource 1',
                  description: 'Vue documentation',
                  link: 'https://www.vuejs.org'
              },
              {
                  id: 2,
                  name: 'Resource 2',
                  description: 'This is the description for google',
                  link: 'https://www.google.com'
              },
              {
                  id: 3,
                  name: 'Resource 3',
                  description: 'This is the description for resource 3',
                  link: 'https://www.google.com'
              }

          ],
        }
    },
    provide() {
        return {
            storedResources: this.storedResources,
            addResource: this.addResorce,
            deleteResource: this.removeResource
        }
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        },
        addResorce(title, description, url){
            const newResource = {
                id: new Date().toISOString(),
                name: title,
                description: description,
                link: url
            };
            this.storedResources.unshift(newResource);
            this.selectedTab = 'stored-resource';
        },
        removeResource(id) {
           const resourceIndex = this.storedResources.findIndex(
               (resource) => resource.id === id);
               this.storedResources.splice(resourceIndex, 1
           );
        }

    },
    computed: {
        storedResButton() {
            return this.selectedTab === 'stored-resource' ? 'raised' : 'flat';
        },
        addResButton() {
            return this.selectedTab === 'add-resource' ? 'raised' : 'flat';
        }
    },

}
</script>