<template>
  <div>
    <AddressBookHeader />
    <ContactForm />
  </div>
</template>
<script>
import AddressBookHeader from "../components/AddressBookHeader.vue";
import ContactForm from "../components/ContactForm.vue";
export default {
  name: "MainForm",
  components: {
    AddressBookHeader,
    ContactForm,
  },
};
</script>
<style>
</style>