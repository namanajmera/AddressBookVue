<template>
  <div class="main-content">
    <div class="header-contain">
      <div class="address-text-details">
        Person Details
        <div class="address-count">{{ totalContact }}</div>
      </div>
      <div class="search">
        <!-- <img
          src="../assets/person_search_black_24dp.svg"
          alt=""
          id="search-icon"
        /> -->
        <input
          type="search"
          id="searchBox"
          placeholder="search content"
          @input="searchName"
          v-model="searchNameKeyword"
        />
        <button id="reload" @click="reload">
          <img src="../assets/reload.png" alt="" />
        </button>
      </div>
      <router-link to="/addContact"
        ><a class="add-button">
          <img
            src="../assets/person_add_black_24dp.svg"
            class="plus-button"
            alt=""
          />Add User</a
        ></router-link
      >
    </div>
    <div class="table-main">
      <table class="table" id="display">
        <tr>
          <th>Full Name</th>
          <th>Address</th>
          <th>City</th>
          <th>State</th>
          <th>Zip Code</th>
          <th>Phone Number</th>
          <th>Actions</th>
        </tr>
        <tr v-for="contact in Contacts" :key="contact.contactId">
          <td>{{ contact.fullName }}</td>
          <td>{{ contact.address }}</td>
          <td>{{ contact.city }}</td>
          <td>{{ contact.state }}</td>
          <td>{{ contact.zip }}</td>
          <td>{{ contact.phoneNumber }}</td>
          <td>
            <img
              :id="contact.contactId"
              src="../assets/delete_black_24dp.svg"
              alt="delete"
              class="actions"
              @click="remove(contact.contactId)"
            />
            <img
              :id="contact.contactId"
              src="../assets/edit_black_24dp.svg"
              alt="edit"
              class="actions"
              @click="update(contact)"
            />
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
import { HTTP } from "../service/service.js";
export default {
  name: "AddressBookContact",
  data() {
    return {
      Contacts: [],
      searchNameKeyword: undefined,
      totalContact: "0",
    };
  },
  mounted() {
    // this.count();
    if (this.searchNameKeyword == undefined) {
      this.getContacts();
    } else {
      this.searchName();
    }
  },
  methods: {
    reload() {
      this.getContacts();
    },
    searchName() {
      HTTP.get("/addressbook/get/search/" + this.searchNameKeyword)
        .then((result) => {
          this.Contacts = result.data.data;
          console.log(result.data.data);
          console.log(this.searchNameKeyword);
          this.totalContact = this.Contacts.length;
        })
        .catch((err) => {
          console.log(err);
        });
      console.log("Length", this.Contacts.length);
    },
    getContacts() {
      HTTP.get("/addressbook")
        .then((result) => {
          this.Contacts = result.data.data;
          console.log(result.data.data);
          this.totalContact = this.Contacts.length;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    remove(id) {
      HTTP.delete("/addressbook/delete/" + id)
        .then((result) => {
          console.log(result);
          this.getContacts();
          this.count();
        })
        .catch((err) => {
          console.log(err);
        });
    },
    update(data) {
      this.$router.push({
        name: "MainForm",
        params: {
          data: {
            result: data,
            type: "update",
          },
        },
      });
    },
  },
};
</script>
<style>
a {
  text-decoration: none;
}
.main-content {
  display: flex;
  flex-direction: column;
  margin-top: 10px;
  min-height: calc(100vh-80px);
  background-color: #f7f7f7;
  padding: 30px 0 10px;
  box-sizing: border-box;
}

.header-contain {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 83%;
  margin: 0 auto;
  padding-bottom: 25px;
}

.address-text-details {
  font: normal normal bold 28px/25px Roboto;
  letter-spacing: 0px;
  color: #42515f;
  opacity: 1;
}

.address-count {
  background-color: #008cff;
  color: #ffffff;
  border-radius: 42%;
  font-size: 16px;
  width: 26px;
  text-align: center;
  display: inline-block;
}
#searchBox {
  background-image: url("../assets/person_search_black_24dp.svg");
  background-position: right;
  outline: none;
  border-radius: 28px;
  border: 0px;
  width: 170px;
  height: 50px;
  /* opacity: 0.8; */
  margin-left: -0.5px;
  transition: width 2s;
}
/* #searchBox:hover {
  width: 170px;
  height: 55px;
  background-image: none;
} */
.search {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  /* background: #ffffff 0% 0% no-repeat padding-box; */
  padding: 20px;
  /* box-shadow: 0px 1px 3px #00000029; */
  /* border-radius: 28px; */
  opacity: 1;
  /* width: 250px; */
  height: 55px;
  margin-left: 750px;
}

#search-icon {
  width: 27px;
  height: 27px;
}

#reload {
  border: none;
  background-color: #f7f7f7;
  /* margin-left: 10px; */
}
#reload img {
  width: 30px;
  height: 30px;
}

.plus-button {
  margin-right: 5px;
}

.add-button {
  text-align: center;
  font: normal normal normal 22px/29px Roboto;
  letter-spacing: 0px;
  color: #ffffff;
  opacity: 1;
  background: #008cff 0% 0% no-repeat padding-box;
  border-radius: 5px;
  opacity: 1;
  width: 150px;
  height: 50px;
  border-radius: 5px;
  padding: 10px 18px;
  outline: none;
  cursor: pointer;
  text-decoration: none;
}
/* Table Content */

.table-main {
  width: 80%;
  margin: 0 auto;
  overflow: auto;
}

.table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0 15px;
  min-width: 800px;
}

td,
th {
  text-align: left;
  padding: 5px 8px;
}

th {
  background: #2c81d1 0% 0% no-repeat padding-box;
  border-radius: 3px 3px 0px 0px;
  text-align: left;
  font: normal normal medium 18px/24px Roboto;
  letter-spacing: 0px;
  color: #ffffff;
  text-transform: uppercase;
  /* border: 0px solid #dddddd; */
  padding: 20px;
  opacity: 1;
}

tr:not(:first-child) {
  font: normal normal normal 14px/21px Roboto;
  letter-spacing: 0px;
  color: #3d3d3d;
  opacity: 1;
}

tr {
  border: 2px solid #000000;
  background-color: white;
  padding: 12px 12px 12px 12px;
  height: 20px;
  border-radius: 3px;
  box-shadow: 1px 1px black;
}

td {
  text-align: left;
  font: normal normal 600 16px/19px Lato;
  letter-spacing: 0px;
  color: #3d3d3d;
  opacity: 1;
}

td:first-child {
  display: flex;
  align-items: center;
}

td img {
  margin-left: 10px;
}

.actions {
  margin-left: 20px;
  cursor: pointer;
}
</style>