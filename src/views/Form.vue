<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-5 mb-3">
        <LeaveForm />
      </div>

      <div class="col-6 mb-3">
        <CheckForm />
      </div>
    </div>
  </div>
</template>

<script>
import LeaveForm from "@/components/LeaveForm.vue";
import CheckForm from "@/components/CheckForm.vue";

export default {
  name: "Form",
  components: {
    LeaveForm,
    CheckForm,
  },
};
</script>

<style>
body {
  background: black;
}
</style>
