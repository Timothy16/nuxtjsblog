<template>
  <div>
  <div class="card container mt-5 shadow p-0 mb-2 bg-white rounded">
    <div class="card-body">
    <div v-if="updateForm">
       <div class="container">
         <div class="row">
           <div class="col-sm-8">
            <div class="card mt-2 shadow p-0 mb-2 bg-white rounded"  v-for="(blog, index) in blogs" :key="index">
                <div class="card-header">
                <h2> {{blog.title}}</h2>
                  </div>
                  <div class="card-body">
                  <blockquote class="blockquote mb-0">
                  <p>{{blog.content}}</p>
                  <footer class="blockquote-footer"><cite title="Source Title"> {{blog.author}} ({{blog.categories}})</cite></footer>
                  </blockquote>
        <button class="btn btn-outline-danger mt-3" @click="deletePost(blog.id)">Delete Post <img src="@/assets/icons/trash.svg" alt="e" width="20" height="20" title="" ></button>
        <button class="btn btn-outline-info mt-3 ml-1" @click="editBlog(blog)">Edit Post <img src="@/assets/icons/pencil.svg" alt="e" width="20" height="20" title="" ></button>
        </div>
        </div>
        </div>
        <div class="col-sm-4 mt-2">
          <div class="card shadow mb-1 bg-white rounded" style="width: 18rem;">
          <img src="@/assets/gls.jpg" class="card-img-top" alt="...">
          <div class="card-body">
          <h5 class="card-title">Global Leadership Summit</h5>
          <p class="card-text">“The Global Leadership Summit is a two-day,
             world-class experience broadcast every August LIVE in HD to hundreds of satellite locations in North America.”</p>
          <a href="#" class="btn btn-outline-dark">Read More <img src="@/assets/icons/arrow-right.svg" alt="e" width="20" height="20" title="" ></a>
          </div>
        </div>
        <div class="card shadow mb-2 bg-white rounded" style="width: 18rem;">
          <img src="@/assets/tech.jpg" class="card-img-top" alt="...">
          <div class="card-body">
          <h5 class="card-title">Africa Tech Summit</h5>
          <p class="card-text">“The Africa Tech Summit attracts delegates from all over the world. 
            This year, AppsAfrica singled out three people and asked them the same five questions.”</p>
          <a href="#" class="btn btn-outline-dark">Read More <img src="@/assets/icons/arrow-right.svg" alt="e" width="20" height="20" title="" ></a>
          </div>
        </div>
        </div>
        </div>
    
  </div>
  </div>
<div class="container mt-5 " v-else>
        <div class="card shadow p-3 mb-5 bg-white rounded">
            <div class="card-body">
            <div class="container" >
            <div class="row">
            <div class="col-sm-4 shadow p-3 mb-1 bg-white rounded">
                    <form>
                <div class="form-group">
                    <label>Title</label>
                    <input type="text"  class="form-control" placeholder="add post title" v-model="postBlog.title">
                </div>
                <div class="form-group">
                    <label>Categories:</label>
                    <select class="form-control" v-model="postBlog.categories">
                        <option disabled selected>Please Chooose</option>
                        <option value="Buiness">Business</option>
                        <option value="Religion">Religion</option>
                        <option value="Entertainment">Entertainment</option>
                        <option value="Sport">Sport</option>
                        <option value="Politics">Politics</option>
                        <option value="Education">Education</option>
                    </select>
                </div>

                <div class="form-group" >
                <label for="comment">Content:</label>
                <textarea class="form-control" rows="5" id="comment" placeholder="add content" v-model="postBlog.content"></textarea>
                </div>

            <div class="form-group">
                    <label>Author</label>
                    <input type="text"  class="form-control" placeholder="add author" v-model="postBlog.author">
                </div>
                <center>
                 <button type="submit" class="btn btn-info btn-lg" @click.prevent="updatePost(postBlog.id)">Update</button>
                 </center>
              </form>
              </div>
            
            <div class="col-sm-6">
                     <div class="card shadow m-3 mb-5 bg-white rounded" >
                    <div class="card-body">

                    <div class="display">
                 <h3> Post Preview</h3> 
                <label> Post Title : </label>
                <h4>{{postBlog.title}}</h4>
                 <label> Post Category  : </label>
                <h4>{{postBlog.categories}}</h4>
                 <label> Post Content  : </label>
                <h4>{{postBlog.content}}</h4>
                 <label> Post Author  : </label>
                <h4>{{postBlog.author}}</h4>
            </div>
            </div>
            </div>
            </div>
            </div>
            </div>
            </div>
            </div>
        </div>
    </div>
</div>
    
    </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return {
      updateForm : true,
      blogs : [],
      postBlog : {
          title : '',
          categories: '',
          content : '',
          author : '',
      },
    }
  },

  methods : {
    reload(){
            var timeout = setTimeout("location.reload(true);", 6000);
            function resetTimeout(){
                clearTimeout(timeout);
                timeout = setTimeout("location.reload(true", 6000);
            }
    },
     editBlog(id){
      this.updateForm = !this.updateForm
      this.postBlog = id
    }, 
    updatePost(i){
            swal({
                title: "Are you sure?",
                text: "Once you Update, previous post will be lost",
                icon: "warning",
                buttons: true,
                dangerMode: true,
              })
              .then((willDelete) => {
                if (willDelete) {
                  axios.put(`https://mynuxtjsblog.firebaseio.com/BlogPost/${i}.json`, this.postBlog)
                    .then(function (res){
                    console.log(res)
                    swal("Post successfully updated!", {
                      icon: "success",
                    });
                    // this.getallBlogs()
                  },
                  function(error){
                    console.log(error)
                })
                this.reload()
                  
                } else {
                  swal("Your post is safe!");
                }
              });

        }, 
      deletePost(i){
                    swal({
                title: "Are you sure?",
                text: "Once deleted, post will be lost",
                icon: "warning",
                buttons: true,
                dangerMode: true,
              })
              .then((willDelete) => {
                if (willDelete) {
                  axios.delete(`https://mynuxtjsblog.firebaseio.com/BlogPost/${i}.json`)
                    .then(function (res){
                    console.log(res)
                   swal("Post successfully deleted!", {
                      icon: "success",
                    });
                    this.getallBlogs()
                    
                  },
                  function(error){
                    console.log(error)
                })
                this.reload()
                  
                } else {
                  swal("Your post is safe!");
                }
              });
    },
    getallBlogs(){
         axios.get('https://mynuxtjsblog.firebaseio.com/BlogPost.json')
          .then(res =>{
            const data = res.data;
            for (let key in data){
              const post = data[key]
              post.id = key
              this.blogs.unshift(post)
            }
          }).catch(error => {
            console.log(error);
          });
      }
    },
  created(){
         this.getallBlogs()
    }
}
</script>



