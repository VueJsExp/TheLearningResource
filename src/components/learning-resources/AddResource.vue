<template>
    <base-dialog 
      title = "Invalid Input"
      v-if = "inputIsInvalid"
      v-on:close = "confirmError"
    >
      <template v-slot:header>
        <h2>Header</h2>
      </template>
      <template v-slot:default>
        <p>Unfortunately, at least one input value is empty.</p>
        <p>Please check all inputs and make sure that you enter at least a few characters into each input fields.</p>
      </template>
      <template v-slot:actions>
        <base-button v-on:click = "confirmError">Okay</base-button>
      </template>
    </base-dialog>
    <base-card>
        <h2>Add Resource</h2>
        <form v-on:submit.prevent = "submitData">
            <div class="form-control">
                <label for="title">Title</label>
                <input id="title" name="title" type = "text" ref = "titleInput" />
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea id="description" name="description" rows="3" ref = "descriptionInput"></textarea>
            </div>
            <div class="form-control">
                <label for="link">Link</label>
                <input id="link" name="link" type = "url" ref = "linkInput" />
            </div>
            <div>
                <base-button type="submit">Add Resource</base-button>
            </div>
        </form>
    </base-card>
</template>

<script>
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog },
  inject: ["addNewResource"],
  data()
  {
    return {
      inputIsInvalid: false
    };
  },
  methods: {
    submitData()
    {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descriptionInput.value;
      const enteredLink = this.$refs.linkInput.value;
      if (enteredTitle.trim() === "" || enteredDescription.trim() === "" || enteredLink.trim() === "") {
        //input is invalid
        this.inputIsInvalid = true;
        return;
      }
      //clearing
      this.$refs.titleInput.value = "";
      this.$refs.descriptionInput.value = "";
      this.$refs.linkInput.value = "";

      this.addNewResource(enteredTitle, enteredDescription, enteredLink);
    },
    confirmError()
    {
      this.inputIsInvalid = false;
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
}
</style>