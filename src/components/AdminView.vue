<template>
  <div class="h-[500px] flex justify-center">
    <form class="flex flex-col w-[300px] m-auto gap-8">
      <h2 class="self-center text-xl">Add new project</h2>

      <label class="flex justify-center items-center gap-2">
        Project title
        <input v-model="title" class="border" />
      </label>
      <label class="flex justify-center items-center gap-2">
        Project URL
        <input v-model="image" type="url" class="border" />
      </label>
      <label class="flex justify-center items-center gap-2"
        >Description
        <textarea v-model="description" class="border"></textarea>
      </label>
      <button
        @click.prevent="handleSubmit"
        class="border border-b-2 px-3 bg-red-200 w-[50%] self-center"
      >
        SUBMIT
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      title: "",
      image: "",
      description: "",
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("createProject", {
        title: this.title,
        img: this.image,
        description: this.description,
      });
    },
  },
};
</script>

<style></style>
