<template>
  <div>
    <h1>Create A Post</h1>
    <form @submit.prevent="addPostAsync">
      <div>
        <div>
          <div>
            <label>Post Title:</label>
            <input type="text" v-model="post.title" />
          </div>
        </div>
      </div>
      <div>
        <div>
          <div>
            <label>Post Body:</label>
            <textarea v-model="post.body" rows="5"></textarea>
          </div>
        </div>
      </div>
      <br />
      <div>
        <button>Create</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      post: {},
    };
  },
  methods: {
    addPost() {
      let uri = "//localhost:4000/posts/add";
      this.axios.post(uri, this.post).then(() => {
        this.$router.push({ name: "posts" });
      });
    },
    async addPostAsync() {
      let uri = "//localhost:4000/posts/add";
      let r = await this.axios.post(uri, this.post);
      console.log(r);
      this.$router.push({ name: "posts" });
    }
  }
};
</script>