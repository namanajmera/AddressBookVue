<template>
  <div>
    <AddressBookHeader />
    <div id="main">
      <AddressBookContact />
    </div>
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
#main {
  background-color: #f7f7f7;
}
</style>