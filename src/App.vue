<template>
  <div id="app" class="small-container">
    <h1>Employee Table</h1>
    <employee-form @add:employee="addEmployee"/>
    <employee-table 
    :employees="employees" 
    @delete:employee="deleteEmployee" 
    @edit:employee="editEmployee" 
    />
    <!-- Same thing -->
    <!-- <employee-table v-bind:employees="employees" /> -->

  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import EmployeeTable from "@/components/EmployeeTable.vue";
import EmployeeForm from "@/components/EmployeeForm.vue";

export default {
  name: "app",
  components: {
    EmployeeTable,
    EmployeeForm,
  },
  data(){
    return {
      employees: [
        {
          id: 1,
          name: 'Muneeb Ur Rehman',
          email: 'muneebkh5@gmail.com',
        },
      ],
    }
  },
  methods: {
    addEmployee(employee) {
      const lastId = this.employees.length > 0 ? this.employees [ this.employees.length -1].id : 0;
      const id = lastId + 1;
      const newEmployee= { ...employee, id };
      this.employees= [...this.employees, employee]
    },
    deleteEmployee(id) {
      this.employees = this.employees.filter(
        employee => employee.id !== id
      )
    },
    editEmployee(id, updatedEmployee) {

    }
  }
};
</script>

<style>
button {
  background: #009435;
  border: 1px solid #009435;
}
.small-container{
  max-width: 680px;
}
</style>
