<template>
  <BaseDialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Unfortunately, at least one imput value is invalid.</p>
      <p>
        Please check all inputs and make sure you enter at least a few
        characters into each input field.
      </p>
    </template>
    <template #actions>
      <BaseButton @click="confirmError">Okay</BaseButton>
    </template>
  </BaseDialog>
  <BaseCard>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" v-model.trim="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Descirpition</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          v-model.trim="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" v-model.trim="linkInput" />
      </div>
      <div>
        <BaseButton type="submit">Add Resource</BaseButton>
      </div>
    </form>
  </BaseCard>
</template>

<script setup>
import { ref, inject } from 'vue';

const addResource = inject('addResource');
const inputIsInvalid = ref(false);
const titleInput = ref('');
const descInput = ref('');
const linkInput = ref('');

function submitData() {
  const enteredTitle = titleInput.value;
  const enteredDescription = descInput.value;
  const enteredLink = linkInput.value;

  if (enteredTitle === '' || enteredDescription === '' || enteredLink === '') {
    inputIsInvalid.value = true;
    return;
  }
  addResource(enteredTitle, enteredDescription, enteredLink);
}
function confirmError() {
  inputIsInvalid.value = false;
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
