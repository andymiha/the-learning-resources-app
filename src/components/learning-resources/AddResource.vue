<template>
  <BaseDialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>At least one input value is invalid</p>
      <p>No Input fields should be empty</p>
    </template>
    <template #actions>
      <BaseButton @click="confirmError">OK</BaseButton>
    </template>
  </BaseDialog>
  <BaseCard>
    <!-- to collect data here, we could either use v-model or refs -->
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Title</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <div class="form-control">
        <BaseButton type="submit">Add Resource</BaseButton>
      </div>
    </form>
  </BaseCard>
</template>

<script>
export default {
  inject: ['addResource'],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descInput.value;
      const enteredUrl = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredUrl.trim() === ''
      ) {
        /* injecting our custom alert */
        this.inputIsInvalid = true;
        return;
      }

      /* we could emit a custom event here and have the AddRersource comp listen to it */
      /* but this is hard bc comp is injected dynamically */
      /* we will use provide/inject */
      this.addResource(enteredTitle, enteredDescription, enteredUrl);
    },
    confirmError() {
      this.inputIsInvalid = false;
    },
  },
};
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
