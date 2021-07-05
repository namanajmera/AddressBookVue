<template>
  <div class="main-content">
    <div class="header-contain">
      <div class="address-text-details">Person Details</div>
      <div class="search">
        <img
          src="../assets/person_search_black_24dp.svg"
          alt=""
          id="search-icon"
        />
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
  </div>
</template>
<script>
export default {};
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
  width: 80%;
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

.search {
  display: flex;
  align-items: center;
  justify-content: center;
  background: #ffffff 0% 0% no-repeat padding-box;
  box-shadow: 0px 1px 3px #00000029;
  border-radius: 28px;
  opacity: 1;
  width: 77px;
  height: 55px;
  margin-left: 750px;
}

#search-icon {
  width: 27px;
  height: 27px;
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
</style>