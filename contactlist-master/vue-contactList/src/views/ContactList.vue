<template>
  <main>
    <div class="container">
      <div>
        <h1 style="text-align: center;">Contact List<br></h1>
        <div class="list">
          <table>
            <tbody>
              <tr v-for="(acontact, index) in filterContacts" :key="acontact.id">
                <td>
                  <img :src="acontact.imageUrl" style="max-width: 150px; max-height: 300px;">
                  <div>
                    <div>{{acontact.firstname}} {{acontact.lastname}}</div>
                    <div>Mobile: {{acontact.mobileNo}}</div>
                    <div>Email: {{acontact.email}}</div>
                    <div>Facebook: {{acontact.facebook}}</div>
                    <div>
                      <router-link :to="{path:'/contactupdate' , name: 'contactupdate', params: {contactId: acontact._id}}">
                        <button type="button" class="btn btn-warning">Update User</button>
                      </router-link >
                      <button @click="deleteContact(acontact._id)" class="btn btn-danger">Delete User</button>
                    </div>
                  </div>
                </td>
                <td v-if="index % 2 === 0"></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Contacts',
  data() {
    return {
      search: '',
      Contacts : [],
      uid: ''
    }
  },
  mounted() {
    axios.get('http://127.0.0.1:5001/contacts')
    .then((response)=>{
      console.log(response.data)
      this.Contacts = response.data
    })
    .catch((error)=>{
      console.log(error)
    })
  },
  computed :{
    filterContacts: function(){
      return this.Contacts.filter((contact)=>{
        return contact.firstname.match(this.search)
      })
    }
  },
  methods:{
    deleteContact(contactId) {
      axios.delete("http://127.0.0.1:5001/contacts/"+contactId)
      .then((response)=>{
        console.log('Delete Contact Id: ' + contactId)
      })
      .catch((error)=>{
        console.log(error)
      })
      window.location.reload()
    }
  }
}
</script>

<style>
.container {
  display: flex;
  font-family: "Tilt Warp";
  color: black;
  background-color: aliceblue;
  border-radius: 16px;
  padding: 50px;
  overflow-x: auto; /* allow horizontal scrolling if content overflows */
  max-width: 100%; /* set a maximum width to prevent the container from becoming too wide */
}

.list table {
  display: inline-block; /* allow tables to fill the available space next to each other */
}

.list table tr {
  max-width: 500px; /* set a maximum width for the table rows */
  overflow: hidden; /* hide any overflowing content */
  text-overflow: ellipsis; /* add ellipsis (...) to indicate truncated content */
  white-space: nowrap; /* prevent line breaks within cells */
  margin-right: 50px; /* add some margin to separate tables */
}
</style>