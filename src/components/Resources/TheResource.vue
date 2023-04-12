<template>
    <base-card>
        <base-button v-on:click="() => setSelectedTab('StoredResource')">Stored Resource</base-button>
        <base-button @click="() => setSelectedTab('AddResourece')" > Add Resource</base-button>

       
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
            storedResources:[
                {
                    id: 1,
                    title: 'Vue js',
                    description: 'This is the content of Vue js',
                    url: 'www.google.com'
                },
                {
                    id: 2,
                    title: 'React js',
                    description: 'This is the content of React js',
                    url: 'www.google.com'
                },
                {
                    id: 3,
                    title: 'Angular js',
                    description: 'This is the content of Angular',
                    url: 'www.google.com'
                },
            ]
             
    
            }
         },
         provide(){
            return {
                resources: this.storedResources,
                addNewResource: this.addResource,
                deleteResource: this.removeResource,
            }
         },
        methods:
        {
            setSelectedTab(tab){
                this.selectedTab = tab
            },

           addResource(title, description, link){
                const newResoure={
                    id: new Date().toISOString(),
                    title: title,
                    description: description,
                    url: link
                };
                this.storedResources.push(newResoure);
                this.selectedTab = 'StoredResource';
           },
           removeResource(resId){
            const resIndex = this.storedResources.findIndex(res => resId === res.id );
            this.storedResources.splice(resIndex, 1);
           },
         

        }
    }
</script>