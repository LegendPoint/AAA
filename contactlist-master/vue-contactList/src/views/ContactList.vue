<template>
  <main>
    <div class="container">
      <div>
        <h1 style="text-align: center;">Contact List<br></h1>

        <div class="form-group row">
          <label for="name" class="col-sm-2 col-form-label">Name:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="name" v-model="newContact.name" placeholder="Enter name">
          </div>
        </div>

        <div class="form-group row">
          <label for="telephone" class="col-sm-2 col-form-label">Mobile:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="telephone" v-model="newContact.telephone" placeholder="Enter telephone number">
          </div>
        </div>

        <div class="form-group row">
          <label for="email" class="col-sm-2 col-form-label">Email:</label>
          <div class="col-sm-10">
            <input type="email" class="form-control" id="email" v-model="newContact.email" placeholder="Enter email address">
          </div>
        </div>

        <button type="submit" class="btn btn-primary" @click="addContact">Add</button>

        <hr>

        <div class="row">
          <div class="col-sm-4" v-for="(newContact, index) in contacts" :key="index">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">{{ newContact.name }}</h5>
                <h6 class="card-subtitle mb-2 text-muted">{{ newContact.telephone }}</h6>
                <p class="card-text">{{ newContact.email }}</p>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      newContact: {
        name: '',
        telephone: '',
        email: ''
      },
      contacts: []
    };
  },
  methods: {
    addContact() {
      this.contacts.push({...this.newContact});
      this.newContact.name = '';
      this.newContact.telephone = '';
      this.newContact.email = '';
    }
  }
};
</script>

<style>
.card {
  margin-bottom: 20px;
}
</style>



