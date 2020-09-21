<template>
  <div id="app">
    <b-input-group  size="sm" class="mb-2">
      <b-input-group-prepend is-text>
        <b-icon icon="search"></b-icon>
      </b-input-group-prepend>
      <b-form-input class="size" @keyup.enter="click" placeholder="Enter your Task..."></b-form-input>
    </b-input-group>
    <CreateTodo @delitItem="delit" :message="message" />
  </div>
</template>

<script>
import CreateTodo from "@/components/CreateTodo";
export default {
  components: {
    CreateTodo,
  },
  data: () => ({
    message: [],
  }),
  methods: {
    click(e) {
      if (e.target.value === "" ) {
        return alert('The fill field cannot be empty!');
      }
      this.message.push({
        text: e.target.value,
        status: false,
        id: Math.floor(Math.random() * 100),
      });
      e.target.value = "";
    },
    delit(index) {
      for (let i = 0; i < this.message.length; i++) {
        if (index === this.message[i].id) {
          this.message.splice(i, 1);
        }
      }
    },
  },
  mounted() {
    if (localStorage.getItem("message"))
      this.message = JSON.parse(localStorage.getItem("message"));
  },
  watch: {
    message: {
      handler() {
        localStorage.setItem(`message`, JSON.stringify(this.message));
      },
      deep: true,
    },
  },
};
</script>
<style scoped>
.mb-2{
  width: 800px;
  margin: auto;

}
</style>
