<template>
    <div class="container p-5">
        <table class="table table-borderd tabel-hover">
            <thead>
                <th>Name</th>
                <th>Email</th>    
                <th>Phone</th>
                <th>Action</th>
            </thead>
            <tbody>
             <template v-for="employee in employees" :key="employee.id">
                    <tr>
                        <td>{{ employee.name }}</td>
                        <td>{{ employee.email }}</td>
                        <td>{{ employee.phone }}</td>
                        <td>Edit</td>
                    </tr>
                </template>
            </tbody>
        </table>
    </div>
</template>

<script>
    import { ref, onMounted } from "vue";
    import axios from 'axios';
    export default {
        setup(){
            const employees = ref([]);

            const getEmployee  = async() => {  
                let res = await axios.get('api/employees');
                employees.value = res.data;
            }
            onMounted(getEmployee());

            return{
                employees
            }
        }  

    }
</script>
