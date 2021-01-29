<template>
  <div class="form">
    <div>
      <b-card bg-variant="light">
        <b-form-group label-cols-xs="3" label="Check Application" label-size="lg" label-class="font-weight-bold pt-0" class="mb-0 text-left">
          <b-form-group label-cols-sm="2" label="Email:" label-align-sm="right" label-for="nested-street" class="pt-5">
            <b-form-input v-model="form.email" id="nested-street"></b-form-input>
          </b-form-group>

          <b-button
            variant="primary"
            class="float-right"
            @click="getForms"
          >
            Check
          </b-button>

        </b-form-group>
      </b-card>
    </div>

    <h4 class="text-light mt-4">Application Details</h4>

    <table class="table table-hover bg-light mt-4">
    <thead>
      <tr>
        <th scope="col">Name</th>
        <th scope="col">Email</th>
        <th scope="col">Contact</th>
        <th scope="col">Reason</th>
        <th scope="col">From Date</th>
        <th scope="col">To Date</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(check) in forms" :key="check.id">
        <td>{{ check.name }}</td>
        <td>{{ check.email }}</td>
        <td>{{ check.contact }}</td>
        <td>{{ check.text }}</td>
        <td>{{ check.fromdate }}</td>
        <td>{{ check.todate }}</td>
      </tr>
    </tbody>
  </table>
  </div>
</template>

<script>
export default {
  name: 'CheckForm',
  data() {
    return {
      forms: [],
      form: {
        email: '',
      },
    }
  },

  methods: {
    getForms() {
      const email = this.form.email
      this.$http.get(`http://localhost:3000/forms/${email}`)
        .then(res => {
          this.form.email = ''
          this.forms = res.data
          console.log(res.data)
        })
        .catch((err) => {
          console.log(err)
        })
    },
  },
}
</script>

<style scoped>
.bc {
  background: whitesmoke;
}
</style>
