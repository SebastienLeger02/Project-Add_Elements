<template>
  <div class="h-[500px] flex flex-col justify-center items-center gap-10 container">
    <h2 class="self-center text-xl">My portfolio</h2>

    <div class="grid grid-cols-3 gap-8">
      <div v-for="proj in proyectos" :key="proj.id">
        <img :src="proj.img" width="150" />
        <div class="text-center">
          <h2>{{ proj.title }}</h2>
          <button
            class="border border-b-2 px-1 bg-red-200 text-xs"
            @click="deleteProject(proj.id)"
          >
            X
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserView",
  props: ["proyectos"],
  methods: {
    deleteProject(id) {
      console.log(id);
      this.$emit("deleteProject", id);
    },
  },
};
</script>

<style></style>
