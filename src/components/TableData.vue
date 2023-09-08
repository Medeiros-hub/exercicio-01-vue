<template>
  <div class="table-container">
    <div>
      <h2>Alunos Aprovados</h2>
      <table>
        <thead>
          <tr>
            <th>Nome</th>
            <th>Nota</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(student, index) in approvedStudents" :key="index">
            <td>{{ student.name }}</td>
            <td>{{ student.note }}</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div>
      <h2>Alunos Reprovados</h2>
      <table>
        <thead>
          <tr>
            <th>Nome</th>
            <th>Nota</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(student, index) in failedStudents" :key="index">
            <td>{{ student.name }}</td>
            <td>{{ student.note }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    approvedStudents: {
      type: Array as () => { name: string; note: number }[],
      required: true,
    },
    failedStudents: {
      type: Array as () => { name: string; note: number }[],
      required: true,
    },
  },
});
</script>

<style scoped>
.table-container {
  color: #fff;
  display: flex;
  justify-content: space-around;
  border-collapse: collapse; 
  width: 100%; 
}

.table-container th, .table-container td {
  padding: 10px; 
  border: 1px solid #fff; 
  text-align: center; 
}

.table-container th {
  background-color: #555; 
}

.table-container tbody tr:nth-child(even) {
  background-color: #666; 
}

.table-container tbody tr:hover {
  background-color: #777; 
}
</style>
