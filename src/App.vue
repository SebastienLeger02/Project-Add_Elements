<template>
  <div>
    <nav class="flex justify-end gap-2">
      <button @click="isAdmin = true" class="border border-b-2 px-3" 
      :class="{'bg-red-200 font-bold': isAdmin}"
      >ADMIN</button>
      <button @click="isAdmin = false" class="border border-b-2 px-3"
      :class="{'bg-red-200 font-bold': !isAdmin}"
      >USER</button>
    </nav>
    
    <AdminView v-if="isAdmin" @createProject="addProject" />
    <UserView v-else :proyectos="allProjects" @deleteProject="deletePr" />
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";
import MyData from "./MyData"

export default {
  name: "App",
  components: {
    UserView,
    AdminView,
  },
  data() {
    return {
      isAdmin: true,
      allProjects: MyData,
      nextId: 7
    };
  },
  methods: {
    addProject(project) {
      this.allProjects.push({...project, id: this.nextId});
      this.nextId++;
      this.isAdmin = false;
    },
    deletePr(id){
      console.log(id)
      //quitar el proyecto con ese id del array
      // let indexProyectoABorrar = this.allProjects.findIndex(proj => proj.id===id) 
      // this.allProjects.splice(indexProyectoABorrar, 1);

      this.allProjects = this.allProjects.filter(proj => proj.id!==id)

    }
  },
};
</script>

<style></style>
