<template>
  <div>
    <AddressBookHeader />
    <div id="main">
      <AddButtonDetails />
      <AddressBookContact />
    </div>
  </div>
</template>
<script>
import AddressBookHeader from "../components/AddressBookHeader.vue";
import AddButtonDetails from "../components/AddButtonDetails.vue";
import AddressBookContact from "../components/AddressBookContacts.vue";
export default {
  name: "AddressBookMain",
  components: {
    AddressBookHeader,
    AddButtonDetails,
    AddressBookContact,
  },
};
</script>
<style>
#main {
  background-color: #f7f7f7;
}
</style>