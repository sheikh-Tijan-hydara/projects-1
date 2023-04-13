<template>
    <base-card>
        <base-button v-on:click="() => setSelectedTab('StoredResource')">Stored Resource</base-button>
        <base-button @click="() => setSelectedTab('AddResourece')" > Add Resource</base-button>
        <h1 v-if="isloading">Loading</h1>
    </base-card>
    <KeepAlive>
         <component :is="selectedTab"></component>
    </KeepAlive>
</template>

<script>
import StoredResource from './StoredResource.vue';
import AddResourece from './AddResourece.vue';


    export default{
       
       
        components: {
            AddResourece,
            StoredResource
        },  
        data(){
            return {
            selectedTab: 'StoredResource',
            storedResources:[],
            isloading: false,
            }
         },
         provide(){
            return {
                resources: this.storedResources,
                addNewResource: this.addResource,
                deleteResource: this.removeResource,
                isloading: this.isloading
            }
         },
        methods:
        {
            setSelectedTab(tab){
                this.selectedTab = tab
            },

           addResource(title, description, link){
                const newResource={
                    id: new Date().toISOString(),
                    title: title,
                    description: description,
                    url: link
                };
                fetch('https://vue-project-1-b0a50-default-rtdb.firebaseio.com/resources.json', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(newResource)
                })
                this.storedResources.push(newResource);
                this.selectedTab = 'StoredResource';
           },
           async removeResource(resId){
            const resIndex = this.storedResources.findIndex(res => resId === res.id );
            this.storedResources.splice(resIndex, 1);
         },

           
          
           
           async loadResources(){
            this.isloading = true;
            const response = await fetch('https://vue-project-1-b0a50-default-rtdb.firebaseio.com/resources.json');
            const data = await response.json();
            this.isloading = false;
            for (const key of Object.keys(data)){
                this.storedResources.push(data[key]);
            }
            },

        },
        created(){
            this.loadResources();
        }
       
    }
</script>