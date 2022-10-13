<template>
  <form action="">
    <div class="modal-card" style="width: auto">
      <header class="modal-card-head">
        <p class="modal-card-title">Login</p>
        <button type="button" class="delete" @click="$emit('close')" />
      </header>
      <section class="modal-card-body">
        <b-field label="House Name">
          <b-input
            type="text"
            :value="house_name"
            placeholder="House Name"
            required
          >
          </b-input>
        </b-field>

        <table>
        
        </table>
        <b-field label="Appartment Name">
          <b-input
            type="password"
            :value="appartment_name"
            password-reveal
            placeholder="Appartment Name"
            required
          >
          </b-input>
        </b-field>
      </section>
      <footer class="modal-card-foot">
        <b-button label="Close" @click="$emit('close')" />
        <b-button label="Create" type="is-primary" />
      </footer>
    </div>
  </form>
</template>

<script>
export default {
  name: "PropertyForm",
  props: {
    house_name: {
      type: String,
      default: "",
    },
    appartment_name: {
      type: String,
      default: "",
    },
  },
};
</script>
<style>
</style>
