<template>
  <div class="form-container">
    <input type="text" v-model="studentName" placeholder="Nome do Aluno">
    <input type="number" max="10" v-model="studentNote" placeholder="Nota do Aluno">
    <button @click="addStudentCallback">Adicionar Aluno</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    addStudent: {
      type: Function as unknown as () => (name: string, note: number) => void,
      required: true
    }
  },
  data() {
    return {
      studentName: '',
      studentNote: 0,
    };
  },
  methods: {
    addStudentCallback() {
      if (this.studentName.trim() === '') {
        alert('Por favor, insira um nome válido');
        return;
      }

      this.addStudent(this.studentName, this.studentNote)

      // Limpar os campos de entrada
      this.studentName = '';
      this.studentNote = 0;
    },
  },
});
</script>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 5px;
}

input[type="text"],
input[type="number"] {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

/* Estilize o botão */
button {
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>

