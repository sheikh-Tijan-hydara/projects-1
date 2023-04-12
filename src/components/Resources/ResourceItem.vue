<template>
    <li>
        <base-card>
                <header>
                    <h3>{{ title }}</h3>
                    <base-button mode="flat" @click="deleteResource(id)" >Delete</base-button>
                </header>
            
            <p>{{ description }}</p>
            <nav>
                <a :href="url">View Resource</a>
            </nav>
        </base-card>
    </li>
</template>
<script>
    export default {
        inject:['deleteResource'],
        props: ['id', 'title', 'description', 'link']
    }

</script>
<style scoped>
    header{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
    li{
        list-style-type: none;
        padding: 5px;
        margin: 5px;
    }
    a{
        text-decoration: none;
    }
    button{
        padding-top: 0;
    }
</style>