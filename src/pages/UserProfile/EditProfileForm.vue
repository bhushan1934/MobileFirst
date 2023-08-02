<template>
  <card>
    <h4 slot="header" class="card-title">Assign Tasks</h4>
    <form>
      <div class="row">
        <div class="col-md-8">
          <base-input type="text"
                    label="Task Name"
                    v-model="user.company">
          </base-input>
        </div>
      </div>
      <div class="row">
          <div class="col-md-10">
          <base-input type="text"
                    label="Task Description"
                    placeholder="Username"
                    v-model="user.username">
          </base-input>
        </div>
       
      </div>

      <div class="row">
        <div class="col-md-8">
         <base-input  label="Select Whom to Assign">
    <select class="form-control">
        <option value="Bhushan">Bhushan</option>
        <option value="Sanket">Sanket</option>
        <option value="Mayur">Mayur</option>
    </select>
    </base-input>
        </div>
      </div>

     
      <div class="text-center">
        <button type="submit" class="btn btn-info btn-fill float-right" @click.prevent="updateProfile">
         Add Task
        </button>
      </div>
      <div class="clearfix"></div>
    </form>
  </card>
</template>
<script>
  import Card from 'src/components/Cards/Card.vue'

  export default {
    components: {
      Card
    },
    data () {
      return {
        user: {
          
        }
      }
    },
    methods: {
      updateProfile () {
        alert('Your data: ' + JSON.stringify(this.user))
      }
    }
  }

</script>
<style>

</style>
