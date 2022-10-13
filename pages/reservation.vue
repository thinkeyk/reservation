<template>
  <section class="section">
    <b-table
      :data="isEmpty ? [] : reservations"
      :striped="true"
      :mobile-cards="false"
    >
      <b-table-column
        field="from"
        label="From"
        :th-attrs="dateThAttrs"
        :td-attrs="columnTdAttrs"
        centered
        v-slot="props"
      >
        <span class="tag is-success">
          {{ new Date(props.row.from).toLocaleDateString() }}
        </span>
      </b-table-column>

      <b-table-column
        field="to"
        label="To"
        :th-attrs="dateThAttrs"
        :td-attrs="columnTdAttrs"
        centered
        v-slot="props"
      >
        <span class="tag is-success">
          {{ new Date(props.row.to).toLocaleDateString() }}
        </span>
      </b-table-column>

      <b-table-column
        field="name"
        label="Name"
        :td-attrs="columnTdAttrs"
        v-slot="props"
      >
        {{ props.row.name }}
      </b-table-column>

      <b-table-column
        field="status"
        label="Status"
        :td-attrs="columnTdAttrs"
        v-slot="props"
      >
        {{ props.row.status }}
      </b-table-column>

      <template #empty>
        <div class="has-text-centered">No Reservations</div>
      </template>
    </b-table>
  </section>
</template>

<script>
import Card from "~/components/Card";

export default {
  name: "IndexPage",
  components: {
    Card,
  },
  data() {
    return {
      reservations: [
        { from: '2020-01-01', to: '2020-01-02', name: 'John Doe', status: 'pending' },
        { from: '2020-01-02', to: '2020-01-03', name: 'Jane Doe', status: 'pending' },
        { from: '2020-01-03', to: '2020-01-04', name: 'Crystal Dwaine', status: 'confirmed' },
        { from: '2020-01-04', to: '2020-01-05', name: 'Allyson Black', status: 'pending' },
        { from: '2020-01-05', to: '2020-01-06', name: 'Simon Red', status: 'confirmed' },

      ],
    };
  }
};
</script>
