<template>
    
    <ul>
        <ResourceItem
            v-for="res in resources" :key="res.id"
            :id="res.key"
            :title="res.title"
            :description="res.description"
            :url="res.url"
            
        ></ResourceItem>
    </ul>
</template>
<script>
     import ResourceItem from './ResourceItem.vue';

    export default{
        inject:['resources'],
        components:{ResourceItem},
        data(){
            return{
                resources: this.resources,
            }
        }
    }
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>