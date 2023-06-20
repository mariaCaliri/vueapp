<template>
    <base-card>
    <base-dialog v-if="inputIsInvalid" title="Invalid Input">
        <template #default>
            <p>Please enter valid input</p>
        </template>
        <template #actions>
            <base-button @click="confirmError">Okay</base-button>
        </template>
    </base-dialog>
        <form @submit.prevent="submitForm">
            <div>
                <label for="name">Resource Name</label>
                <input type="text" id="name" name="title" ref="nameInput">
            </div>
            <div>
                <label for="description">Description</label>
                <textarea id="description" name="description" ref="descriptionInput"></textarea>
            </div>
            <div>
                <label for="link">Link</label>
                <input type="text" id="link" ref="linkInput">
            </div>
            <div>
                <base-button type="submit">Submit</base-button>
            </div>
        </form>

    </base-card>
</template>
<script>
export default {

   inject: ['addResource'],
   data() {
       return {
          inputIsInvalid: false 
       };
    },
    methods: {
        submitForm() {
            const enteredName = this.$refs.nameInput.value;
            const enteredDescription = this.$refs.descriptionInput.value;
            const enteredLink = this.$refs.linkInput.value;

            if (
                enteredName.trim() === '' ||
                enteredDescription.trim() === '' ||
                enteredLink.trim() === ''
            ) {
                this.inputIsInvalid = true;
                return;
            }

            this.addResource(enteredName, enteredDescription, enteredLink);
            
        },
        confirmError() {
            this.inputIsInvalid = false;
        }

    },

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
}


</style>