<template>
  <div class="container">
    <header class="jumbotron">
      <h3>{{content}}</h3>
      <h2>test</h2>
    </header>
  </div>
</template>
  
  <script>
import UserService from "../../service/user.service";

export default {
  name: "Home",
  data() {
    return {
      content: "",
    };
  },
  mounted() {
    UserService.getPublicContent().then(
      (response) => {
        this.content = response.data;
      },
      (error) => {
        this.content =
          (error.response && error.response.data) ||
          error.message ||
          error.toString();
      }
    );
  },
};
</script>