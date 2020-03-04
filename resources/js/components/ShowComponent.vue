

<template>
  <div class="container">
    <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <h1>{{this.post.title}}</h1>
            <p>{{this.post.body}}</p>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
    export default {

      data() {
        return {
          post: {}
        }
      },
      created() {
        let uri = `http://larav.web/api/post/show/${this.$route.params.id}`;
        this.axios.get(uri).then((response) => {
            this.post = response.data;
        });
      },
      
    }
</script>