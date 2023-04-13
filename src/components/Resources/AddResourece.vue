<template>
  <base-dialogue v-if="inputIsValid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Unfortunately, at least one input is invalid.</p>
      <p>Please check all inputs</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialogue>

    <base-card>
        <form @submit.prevent="submitData">
            <div class="form-control">
                <label for="title">Title</label>
                <input type="text" id="title" name="title" ref="titleInput">
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea type="text" id="description" name="description" ref="descInput"></textarea>
            </div>
            <div class="form-control">
                <label for="url">Link</label>
                <input type="url" id="url" name="url" ref="linkInput">
            </div>
            <div>
                <base-button type="submit"> Add Resource</base-button>
            </div>
        </form>
    </base-card>

</template>
 <script>
  export default{
    inject:['addNewResource'],
    data(){
      return{
        inputIsValid: false

      }
    },
    methods:{
      submitData(){
        const enteredTitle = this.$refs.titleInput.value;
        const enteredDescription = this.$refs.descInput.value;
        const enteredLink = this.$refs.linkInput.value;

        if( enteredTitle.trim() === '' || enteredDescription.trim() === '' || enteredLink.trim() === ''){
          this.inputIsValid = true;
          return;
        }
        this.addNewResource(enteredTitle, enteredDescription, enteredLink);
        this.$refs.titleInput.value = '';
        this.$refs.descInput.value = '';
        this.$refs.linkInput.value = '';
      },
      confirmError(){
        this.inputIsValid = false;
      }
    }
  }
</script>
<style scoped>

label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}</style>