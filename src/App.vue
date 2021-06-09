<template>
<div id="app">
    <div class="container">

      <div class="row">
        <div class="col-sm-12 text-center">
          <h1>Guest List</h1>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="card">
            <div class="card-header">
    {{event.eventDate}}
            </div>
            <div class="card-block">
              <h4 class="card-title">{{ event.eventTitle }}</h4><hr>
              <p class="card-text">{{event.eventDescription}}</p>
              <p class="card-text">Add your name to the guest list for exclusive offers:</p>

              <form class="form-inline" v-on:submit.prevent="submittedForm">
                <input type="text" id="nameInput" class="form-control mb-2 mr-sm-2 mb-sm-0" placeholder="Jane Doe" v-model="newNameText">
                <input type="submit" class="btn btn-primary"/>
              </form>
              {{newNameText}}
            </div>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="card">
            <div class="card-header">
              Attending ()
            </div>
            <div class="card-block">
              <div>
                <div class="card-success rounded name-box">

                </div>
              </div>
              <div>
                <h4>No names added yet...</h4>
                {{guestName}}
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default{
name:"test",
data: ()=>({
    event: {
      eventDate: "August 14th - 16th",
      eventTitle: "Summer Festival!",
      eventDescription:
        "It's back! This years summer festival will be in the beautiful countryside featuring our best line up ever!",
    },
    newNameText: "",
    guestName: [],
  }
  )
  ,
  methods:
  {

    submittedForm:  function(){

      this.guestName.push(this.newNameText)

    }
  }
}
</script>

<style>
.row {
  margin-top: 25px;
}

.name-box {
  padding: 10px;
  margin: 10px;
  display: inline-block;
}

</style>
