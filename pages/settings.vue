<template>
  <section class="section">
    <b-button
      label="Create Property"
      type="is-primary"
      size="is-medium"
      @click="isComponentModalActive = true"
    />
    <b-modal
      v-model="isComponentModalActive"
      has-modal-card
      trap-focus
      :destroy-on-hide="false"
      aria-role="dialog"
      aria-label="Create Property"
      close-button-aria-label="Close"
      aria-modal
    >
      <template #default="props">
        <property-form v-bind="formProps" @close="props.close"></property-form>
      </template>
    </b-modal>
    <card
      :title="property.house_name"
      v-for="property in properties"
      key="property.house_name"
    >
      <template #content>
        <p>Permissions</p>
        <ul>
          <li v-for="permission in permissions.filter((p) => p.house_id == property.id)" :key="permission">
            {{ (users.find((user) => user.id === permission.user_id)).name }} {{ permission.permission }} 
          </li>
        </ul>
      </template>
      <b-table
        :data="property.appartments"
        :striped="true"
        :mobile-cards="false"
      >
        <b-table-column
          field="appartment_name"
          label="name"
          centered
          v-slot="props"
        >
          <b-input
            type="text"
            :value="props.row.appartment_name"
            placeholder="Appartment Name"
            required
          >
          </b-input>
        </b-table-column>

        <b-table-column
          field="people"
          label="# of People"
          centered
          v-slot="props"
        >
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
        </b-table-column>

        <b-table-column
          field="status"
          label="Current Status"
          centered
          v-slot="props"
        >
          <b-select placeholder="Current Status">
            <option
              v-for="option in [
                { id: 'availeble', label: 'Available for rent' },
                { id: 'reserved', label: 'Reserved for Special use' },
                { id: 'longterm', label: 'Reserved for Long Term' },
              ]"
              :value="option.id"
              :key="option.id"
            >
              {{ option.label }}
            </option>
          </b-select>
        </b-table-column>

        <template #empty>
          <div class="has-text-centered">No Appartments set for this house</div>
        </template>
      </b-table>
    </card>
  </section>
</template>

<script>
import PropertyForm from "~/components/PropertyForm";

export default {
  name: "SettingsPage",
  components: {
    PropertyForm,
  },
  data() {
    return {
      isComponentModalActive: false,
      formProps: {
        email: "evan@you.com",
        password: "testing",
      },
      properties: [
        {
          id: 1,
          house_name: "House 1",
          appartments: [
            {
              id: 1,
              appartment_name: "Appartment 1",
            },
            {
              id: 2,
              appartment_name: "Appartment 2",
            },
          ],
        },
        {
          id: 2,
          house_name: "House 2",
          appartments: [
            {
              id: 3,
              appartment_name: "Apt 1",
            },
            {
              id: 4,
              appartment_name: "Apt 2",
            },
          ],
        },
      ],

      permissions: [
        {
          user_id: 1,
          house_id: 1,
          permission: "admin",
        },
        {
          user_id: 2,
          house_id: 1,
          permission: "read",
        },
        {
          user_id: 3,
          house_id: 1,
          permission: "write",
        },
      ],

      users: [
        {
          id: 1,
          name: "Evan You",
          email: ""
        },
        {
          id: 2,
          name: "Adam Jahr",
          email: ""
        },
        {
          id: 3,
          name: "Chris Fritz",
          email: ""
        },
        {
          id: 4,
          name: "Steve Schoger",
          email: ""
        },
        {
          id: 5,
          name: "Alex Kyriakidis",
          email: ""
        },
        {
          id: 6,
          name: "Sean Larkin",
          email: ""
        },
        {
          id: 7,
          name: "Natalia Tepluhina",
          email: ""
        }
      ]
    };
  },
};
</script>
