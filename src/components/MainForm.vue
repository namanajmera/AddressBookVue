<template>
  <div>
    <AddressBookHeader />
    <ContactForm :data="this.data" />
  </div>
</template>
<script>
import AddressBookHeader from "../components/AddressBookHeader.vue";
import ContactForm from "../components/ContactForm.vue";
export default {
  name: "MainForm",
  props: ["data"],
  components: {
    AddressBookHeader,
    ContactForm,
  },
};
</script>
<style>
</style>