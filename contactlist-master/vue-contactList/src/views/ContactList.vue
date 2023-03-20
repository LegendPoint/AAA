<template>
  <main>
    <div class="container">
      <div>
        <h1 style="text-align: center;">Contact List<br></h1>
       
        <div class="form-group row">
          <label for="name" class="col-sm-2 col-form-label">Name:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="name" placeholder="Enter name">
          </div>
        </div>

        <div class="form-group row">
          <label for="telephone" class="col-sm-2 col-form-label">Mobile:</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="telephone" placeholder="Enter telephone number">
          </div>
        </div>

        <div class="form-group row">
          <label for="email" class="col-sm-2 col-form-label">Email:</label>
          <div class="col-sm-10">
            <input type="email" class="form-control" id="email" placeholder="Enter email address">
          </div>
        </div>

        <button type="submit" class="btn btn-primary">Add</button>

      </div>
    </div>
  </main>
</template>

<script>

export default {
  data() {
    return{
      name:'',
      email:'',
      telephone:''
    }


  },
  methods:{

  }
}
</script>

<style>

</style>



