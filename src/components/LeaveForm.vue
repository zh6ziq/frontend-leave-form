<template>
	<div class="form">
		<div class="container">
			<b-card
				class="com-bg bfl"
				title="Please enter your details:"
				header-tag="header"
				footer-tag="footer"
			>
				<template #header>
					<h4 class="mb-0">Apply Leave</h4>
				</template>

				<b-form>
					<b-form-group label="Name:" class="text-left bfl">
						<b-form-input
							v-model="form.name"
							type="text"
							required
							placeholder="Enter name"
						/>
					</b-form-group>

					<b-form-group label="Email address:" class="text-left bfl">
						<b-form-input
							v-model="form.email"
							type="email"
							required
							placeholder="Enter email"
						/>
					</b-form-group>

					<b-form-group label="Contact No:" class="text-left bfl">
						<b-form-input
							v-model="form.contact"
							type="tel"
							required
							placeholder="Enter phone"
						/>
					</b-form-group>

					<b-form-group label="Department:" class="text-left bfl">
						<b-form-select
							v-model="form.department"
							:options="departments"
							required
						/>
					</b-form-group>

					<b-form-group label="From:" class="text-left bfl">
						<b-form-datepicker
							id="from-datepicker"
							v-model="form.fromdate"
							class="mb-2"
						/>
					</b-form-group>

					<b-form-group label="To:" class="text-left bfl">
						<b-form-datepicker
							id="to-datepicker"
							v-model="form.todate"
							class="mb-2"
						/>
					</b-form-group>

					<b-form-group label="Reason:" class="text-left bfl">
						<b-form-textarea
							id="textarea"
							v-model="form.text"
							placeholder="State your reason(s)..."
							rows="3"
							max-rows="6"
							required
						/>
					</b-form-group>

					<b-button
						variant="primary"
						@click="onHandleSubmit"
					>
						Submit
					</b-button>
				</b-form>
			</b-card>
		</div>
	</div>
</template>

<script>
export default {
	name: "LeaveForm",
	data() {
		return {
			forms: [],
			form: {
				email: '',
				name: '',
				contact: '',
				department: null,
				fromdate: '',
				todate: '',
				text: '',
			},
			departments: [{
				text: '--Select--',
				value: null
			}, 'Administration', 'Technical', 'Logistic'],

		}
	},

	mounted() {},

	methods: {
		onHandleSubmit() {
			this.$http.post(`http://localhost:3000/forms`, this.form)
				.then(() => {
					this.form = {}
				})
		},

	},
};
</script>

<style scoped>
.com-bg {
  background: linear-gradient(166deg, rgb(32, 32, 32) 22%, rgb(78, 84, 107) 93%);
}

.bfl {
  color: white;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

h4 {
  font-family: Georgia, 'Times New Roman', Times, serif;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
