<template>
  <div>
    <AddressBookHeader />
    <AddressBookContact />
  </div>
</template>
<script>
import AddressBookHeader from "../components/AddressBookHeader.vue";
import AddressBookContact from "../components/AddressBookContacts.vue";
export default {
  name: "AddressBookMain",
  components: {
    AddressBookHeader,
    AddressBookContact,
  },
};
</script>
<style>
</style>