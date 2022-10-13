<template>
  <section class="section">
    <div class="columns is-desktop is-3">
      <b-select placeholder="# of People">
        <option
          v-for="option in [
            { id: 1, label: '1 Person' },
            { id: 2, label: '2 People' },
            { id: 3, label: '3 People' },
            { id: 4, label: '4 People' },
            { id: 5, label: '5 People' },
          ]"
          :value="option.id"
          :key="option.id"
        >
          {{ option.label }}
        </option>
      </b-select>

      <b-datepicker placeholder="Dates" v-model="dates" range> </b-datepicker>
      <b-button active>Search</b-button>
    </div>
  </section>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
