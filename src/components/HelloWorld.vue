<template>
<div>
<div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand href="#">WELCOME</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#">Subject</b-nav-item>
        <b-nav-item href="#">Topic</b-nav-item>
        <b-nav-item href="#">Questions</b-nav-item>
        <b-nav-item-dropdown text="Utilities">
          <b-dropdown-item href="#">1</b-dropdown-item>
          <b-dropdown-item href="#">2</b-dropdown-item>
          <b-dropdown-item href="#">3</b-dropdown-item>
          <b-dropdown-item href="#">3</b-dropdown-item>
          </b-nav-item-dropdown>


        <b-nav-item-dropdown text="Page">
          <b-dropdown-item href="#">page1</b-dropdown-item>
          <b-dropdown-item href="#">page2</b-dropdown-item>
          <b-dropdown-item href="#">page3</b-dropdown-item>
          <b-dropdown-item href="#">page3</b-dropdown-item>


          </b-nav-item-dropdown>
          
        
          <b-nav-item href="#">chart</b-nav-item>
          <b-nav-item href="#">Table</b-nav-item>
        
      </b-navbar-nav>

      

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search for"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>

        

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template slot="button-content"><em>User</em></template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
  </div>
  


<div id="hello">
<div align="right">



<b-button v-b-modal.modal-1 variant="primary" >Add to Subject</b-button>


    <b-modal id="modal-1" title="ADD SUBJECT DETAILS" hide-footer>
    <table>
    <tr><td>Subject ID</td><td><input type="text" v-model="sid"></td></tr>
    <tr><td>Subject Name</td><td><input type="text" v-model="sname" ></td></tr>
    <tr><td>Class</td><td><input type="text" v-model="cls"></td></tr>
    <tr><td>Board</td><td><input type="text" v-model="brd"></td></tr>
    <tr><td><button @click="addTableRow()" >ADD SUBJECT</button></td></tr>
    
    
    </table>
  </b-modal>
<b-button  @click="deleteTableRow()" variant="danger">Remove</b-button>
</div>
 
  
<br>
<table  class="table table-striped">
<thead>
<th>Subject ID</th>
<th>Subject Name</th>
<th>Class</th>
<th>Board</th>
<th>Action</th>
</thead>
<tr>
<tr v-for="item in rowData" :key="item.sid">
  <td>{{ item.sid}}</td>
  <td>{{ item.sname}}</td>
  <td>{{ item.cls }}</td>
  <td>{{ item.brd }}</td>
<td><b-button v-b-modal.modal-2 variant="success">Edit</b-button>
    <b-modal id="modal-2" title="EDIT SUBJECT DETAILS">
    <table>
    <tr><td>Subject ID</td><td><input type="text" v-model="sid"></td></tr>
    <tr><td>Subject Name</td><td><input type="text" v-model="sname" ></td></tr>
    <tr><td>Class</td><td><input type="text" v-model="cls"></td></tr>
    <tr><td>Board</td><td><input type="text" v-model="brd"></td></tr>
    </table>
  </b-modal></td>
</tr>
</table>
</div>
</div>


</template>

<script>
import login from '@/components/login'
export default {
  name: 'HelloWorld',
  data () {
    return {
         sid:'01',
         sname:'english',
         cls:'10th',
         brd:'SSC',
         rowData:[]
    }
  },
  methods:{
    addTableRow: function () { 
       var my_object = {
        sid:this.sid,
        sname:this.sname,
        cls:this.cls,
        brd: this.brd

      };
      this.rowData.push(my_object);
      this.$bvModal.hide('modal-1');
   },
    deleteTableRow: function() { 
    this.rowData.pop();
    alert("ok");
      
   }
	}

}

</script>


