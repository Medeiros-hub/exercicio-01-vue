<template>
  <div style="display: flex;">
    <section id="left-section">
      <FormUser :addStudent="addStudent" />
    </section>
    <section id="right-section">
      <TableData :approvedStudents="approvedStudents" :failedStudents="failedStudents" />
    </section>
  </div>
</template>

<script lang="ts">
import FormUser from './components/FormUser.vue';
import TableData from './components/TableData.vue';

export default {
  components: {
    FormUser,
    TableData
  },
  data() {
    return {
      approvedStudents: [] as { name: string; note: number }[],
      failedStudents: [] as { name: string; note: number }[],
    };
  },
  methods: {
    addStudent(name: string, note: number) {
      if (note >= 5) {
        this.approvedStudents.push({ name, note });
      } else {
        this.failedStudents.push({ name, note });
      }
    },
  },
};
</script>

<style scoped>
#right-section {
  width: 50vw;
  height: 100vh;
  background-color: #333;
}

#left-section {
  height: 100vh;
  width: 50vw;
}
</style>
