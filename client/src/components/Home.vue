<template>
  <div class="hello">
    <div class="container">
      <div class="row">
        <h2> Kanban Firebase </h2>
            <button type="button" class="btn btn-info" data-toggle="modal" data-target="#addProjectModal"> Add Project </button>
      </div>
    </div>


    <!-- Modal -->
    <div class="modal fade" id="addProjectModal" role="dialog">
      <div class="modal-dialog">
        <!-- Modal content-->
        <div class="modal-content">
          <div class="modal-header">
            <button type="button" class="close" data-dismiss="modal">&times;</button>
            <h4 class="modal-title">Add Your Project</h4>
          </div>
          <div class="modal-body">
            <form>
              <div class="form-group">
                <label>Title:</label>
                <input type="text" v-model="addProjectState.title" class="form-control" placeholder="Your Project Title">
              </div>
              <div class="form-group">
                <label>Description:</label>
                <input type="text" v-model="addProjectState.description" class="form-control" placeholder="Project Description">
              </div>
              <div class="form-group">
                <label>Point:</label>
                <input type="text" v-model="addProjectState.point" class="form-control" placeholder="0">
              </div>
              <div class="form-group">
                <label>Assign to:</label>
                <input type="text" v-model="addProjectState.assignTo" class="form-control" placeholder="Input Name">
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
            <button type="button" @click="addProject" class="btn btn-info" data-dismiss="modal">Submit Project</button>
          </div>
        </div>
      </div>
    </div>




  </div>
</template>

<script>
import firebase from 'firebase'

const config = {
  databaseURL: 'https://kanban-firebase.firebaseio.com',
  projectId: 'kanban-firebase'
}
var firebaseApp = firebase.initializeApp(config)
var db = firebaseApp.database().ref('projects')

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      detailProjectModal: false,
      addProjectState: {
        title: '',
        description: '',
        point: '',
        assignTo: '',
        status: 'backlog'
      },
      currentProject: null
    }
  },
  firebase: {
    backlogs: db
  },
  methods: {
    addProject () {
      db.push(this.addProjectState)
      this.addProjectState.title = '',
      this.addProjectState.description ='',
      this.addProjectState.point = '',
      this.addProjectState.assignTo =''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>



















<!-- aaaa -->
