<template>
  <div class="container">
    
    <div class="row">
        <div class="col-md-10">
            <h1>Posts</h1>
        </div>
        <div class="col-md-2">
            <router-link :to="{ name: 'create' }" class="btn btn-primary">Create Post</router-link>
        </div>
    </div>

    <div class="row">
        <table class="table table-hover">
            <thead>
            <tr>
                <th>ID</th>
                <th>Item Name</th>
                <th>Item Price</th>
                <th>Actions</th>
            </tr>
            </thead>
            <tbody>
                <tr v-for="post in posts" :key="post.id">
                    <td>{{ post.id }}</td>
                    <td>{{ post.title }}</td>
                    <td>{{ post.body }}</td>
                    <td>
                        <router-link :to="{name: 'show', params: { id: post.id }}" class="btn btn-success">View</router-link>
                        <router-link :to="{name: 'edit', params: { id: post.id }}" class="btn btn-primary">Edit</router-link>
                        <a class="btn btn-danger" @click.prevent="deletePost(post.id)">Delete</a>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
  </div>
</template>

<script>
  export default {
      data() {
        return {
          posts: []
        }
      },
      created() {
            let uri = 'http://larav.web/api/posts';
            this.axios.get(uri).then(response => {
                    this.posts = (response.data.data).sort(function(a, b) { return b.id - a.id; });
                });
      },
      methods: {
        deletePost(id){
            let uri = `http://larav.web/api/post/delete/${id}`;
            this.axios.delete(uri).then(response => {
                let i = this.posts.map(item => item.id).indexOf(id);
                this.posts.splice(i, 1);
            });
        }
      }
  }
</script>