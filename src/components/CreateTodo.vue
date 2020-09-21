<template>
  <div id="app">
    <div class="bottom">
      <b-button class="btn-size" @click="Completed" variant="success">
        Show completed tasks <b-icon icon="clipboard-plus"></b-icon
      ></b-button>
      <b-button @click="NotCompleted" variant="danger">
        Show uncompleted tasks <b-icon icon="clipboard-x"></b-icon
      ></b-button>
    </div>
    <template v-if="show">
      <b-card
        class="decoration"
        v-for="msg in falshTodo"
        :key="msg.id"
        bg-variant="dark"
        text-variant="white"
      >
        <b-card-text>
          {{ msg.text }}
        </b-card-text>
        <b-button
          class="right"
          @click="delitItem(msg.id)"
          href="#"
          variant="primary"
        >
          Delete the task <b-icon icon="basket-fill"></b-icon
        ></b-button>
        <b-button @click="check(msg.id)" class="complited" variant="danger"
          >Not Complited <b-icon icon="arrow-return-left"></b-icon>
        </b-button>
      </b-card>
    </template>
    <template v-else>
      <b-card
        v-for="msg in trueTodo"
        :key="msg.id"
        bg-variant="dark"
        text-variant="white"
      >
        <b-card-text>
          {{ msg.text }}
        </b-card-text>
        <b-button
          class="right"
          @click="delitItem(msg.id)"
          href="#"
          variant="primary"
        >
          Delete the task <b-icon icon="basket-fill"></b-icon
        ></b-button>
        <b-button @click="check(msg.id)" class="complited" variant="danger"
          >Complited <b-icon icon="check2-circle"></b-icon
        ></b-button>
      </b-card>
    </template>
  </div>
</template>

<script>
export default {
  name: "CreateTodo",
  components: {},
  props: {
    message: {
      type: Array,
      required: true,
    },
  },
  data() {
    return { show: false };
  },
  methods: {
    delitItem(index) {
      this.$emit("delitItem", index);
    },
    check(index) {
      this.message.forEach((e) => {
        if (e.id === index) {
          e.status = !e.status;
        }
      });
    },
    NotCompleted() {
      this.show = false;
    },
    Completed() {
      this.show = true;
    },
  },
  computed: {
    trueTodo: function() {
      return this.message.filter((e) => !e.status);
    },
    falshTodo: function() {
      return this.message.filter((e) => e.status);
    },
  },
};
</script>

<style scoped>
#app {
  width: 800px;
  margin: auto;
  margin-top: 30px;
}
.decoration {
  text-decoration: line-through;
  color: green;
}
.right {
  margin-right: 10px;
}
.btn-size {
  margin-right: 10px;
}
.bottom {
  margin-bottom: 10px;
}
</style>
