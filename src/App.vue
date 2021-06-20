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
            <div class="card-header"  v-bind:class="formSubmittedClass">
              {{ event.eventDate }}
            </div>
            <div class="card-block">
              <h4 class="card-title" >{{ event.eventTitle }}</h4>
              <hr />
              <p class="card-text">{{ event.eventDescription }}</p>
              <p class="card-text">
                Add your name to the guest list for exclusive offers:
              </p>

              <form class="form-inline" v-on:submit.prevent="submittedForm">
                <input
                  type="text"
                  id="nameInput"
                  class="form-control mb-2 mr-sm-2 mb-sm-0"
                  placeholder="Jane Doe"
                  v-model="newNameText"
                />
                <input type="submit" class="btn btn-primary" v-bind:class="formSubmittedClass"/>
              </form>
            </div>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-sm-12">
          <div class="card">
            <div class="card-header">
              Attending ({{guestName.length}})
            </div>
            <div class="card-block">
              <div v-if="guestName.length > 0">
                <div
                  class="card-success rounded name-box"
                  v-for="(name, index) in guestName"
                  :key="index"
                >
                  {{ name }}
                </div>
              </div>
              <div v-else>
                <h4>No names added yet...</h4>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "test",
  data: () => ({
    event: {
      eventDate: "August 14th - 16th",
      eventTitle: "Summer Festival!",
      eventDescription:
        "It's back! This years summer festival will be in the beautiful countryside featuring our best line up ever!",
    },
    newNameText: "",
    guestName: [],
    formSubmittedClass:""
  }),
  methods: {
    submittedForm: function() {
      if (this.newNameText !== "") {
        this.guestName.push(this.newNameText);
        this.newNameText = "";
        this.formSubmittedClass="submitted"
      }
    },
  },
};
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
.submitted{
  background-color: #5cb85c;
}
</style>
