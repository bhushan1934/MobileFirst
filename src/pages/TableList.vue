<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <template slot="header">
              <h4 class="card-title">Task List</h4>
              <p class="card-category">Here is a Task for this table</p>
            </template>
            <l-table class="table-hover table-striped"
                     :columns="tableColumns"
                     :data="tableData">
            </l-table>
          </card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LTable from '@/components/Table.vue';
import Card from '@/components/Cards/Card.vue';

export default {
  components: {
    LTable,
    Card
  },
  data() {
    return {
      tableColumns: ['ID', 'Name', 'Description', 'Status'],
      tableData: [
        {
          ID: 1,
          Name: 'Create DB',
          Description: 'Create a database',
          Status: 'Pending'
        },
        {
          ID: 2,
          Name: 'Design UI',
          Description: 'Design user interface',
          Status: 'In Progress'
        },
        {
          ID: 3,
          Name: 'Implement Backend',
          Description: 'Implement backend logic',
          Status: 'Completed'
        },
        {
          ID: 4,
          Name: 'Testing',
          Description: 'Perform testing',
          Status: 'Pending'
        },
        {
          ID: 5,
          Name: 'Deploy',
          Description: 'Deploy the application',
          Status: 'In Progress'
        }
      ]
    };
  }
};
</script>

<style>
/* Add any custom styles here if needed */
</style>
