<template>
  <div id="app">
    <div class="container-fluid">
      <div>
        <img alt="Vue logo" src="../assets/mongodb-image.png" height="200" width="320"/>
        <h1>{{ msg }}</h1>
      </div>
      <form class="row g-3">
        <div class="col-md-12">
          <label for="requester" class="form-label">Requester</label>
          <input type="email" class="form-control" id="requester" placeholder="Requester" v-model="requester">
        </div>
        <div class="col-md-4">
          <label for="project" class="form-label">Project</label>
          <input type="text" class="form-control" id="project" placeholder="Project" v-model="project">
        </div>
        <div class="col-md-4">
          <label for="cluster" class="form-label">Cluster</label>
          <input type="password" class="form-control" id="cluster" placeholder="Cluster" v-model="cluster">
        </div>
        <div class="col-md-4">
          <label for="database" class="form-label">Database</label>
          <input type="text" class="form-control" id="database" placeholder="Database" v-model="database">
        </div>
        <div class="col-md-4">
          <label for="requestType" class="form-label">Request Type</label>
          <select id="requestType" class="form-select" v-model="requestType" @change="displayInputFields">
            <option selected value="USER-ACCESS">USER-ACCESS</option>
            <option value="NETWORK-ACCESS">NETWORK-ACCESS</option>
            <option value="NEW-INFRA">NEW-INFRA</option>
          </select>
        </div>

        <div class="form-row" v-for="(inputField, index) in inputFields" :key="index">
          <div class="col-md-4">
            <label>{{ inputField.label }}</label>
            <input v-model="inputField.label" :name="`inputFields[${index}][label]`" type="text" class="form-control" :placeholder="`inputFields[${index}][label]`">
          </div>
        </div>

        <div class="col-12">
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MongoAdminRequest',
  props: {
    msg: String,
  },
  data: () => ({
    inputFields: [
    ],
  }),
  methods: {
    displayInputFields () {
      if (requestType.value === 'USER-ACCESS') {
        this.inputFields = [];
        this.inputFields.push({
          label: 'Role',
          id: 'role'
        })
      } else if (requestType.value === 'NETWORK-ACCESS') {
        this.inputFields = [];
        this.inputFields.push({
          label: 'CIDR/IP',
          id: 'cidr'
        })
      }
    }
  }
}
</script>
