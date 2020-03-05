<template>
    <div>
        <div class="container mt-5" v-if="showForm">
        <div class="card shadow p-3 mb-5 bg-white rounded">
        <div class="card-body">
            
            <div class="row">
                <div class="col-sm-6 mt-5">
                    <h1 class="text_edit mt-5">Create a blog and share your voice in minutes</h1>
                    <p class="text_edit2">Venus blog makes it easy to create your own blog, Join our community to start sharing ideas </p>
               <center> <button class="btn btn-secondary btn-lg"  @click="displayForm"> Create Blog Post</button>  </center>
                </div>
                <div class="col-sm-6 mt-5">
                        <img src="@/assets/blog.jpg" alt="no image" class="img-fluid" srcset="">
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
                    <form @submit.prevent = addPost>
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

                 <button type="submit" class="btn btn-outline-success btn-lg">Add Post</button>
              </form>
              </div>
            
            <div class="col-sm-6">
                     <div class="card shadow m-3 mb-5 bg-white rounded" >
                    <div class="card-body">

                    <div class="display">
                 <h3> Post Preview</h3> 
                 <!-- <h3> Post {{index+1}} </h3> -->
                
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
</template>
<script>
// import func from '../../vue-temp/vue-editor-bridge'
import swal from 'sweetalert'
import axios from 'axios'
export default {
    data(){
        return {
            showForm : true,
            postBlog :
                {
            title : '',
            categories: '',
            content : '',
            author : '',
         }
            
        }
    },
    methods : {
        displayForm(){
            this.showForm = !this.showForm
        },
        addPost(){
             if(this.postBlog.title === '' || this.postBlog.categories === '' || this.postBlog.content === '' || this.postBlog.author === ''){
             swal("hoops ", "Field cannot be empty!", "warning")
             }
          else(  axios.post('https://mynuxtjsblog.firebaseio.com/BlogPost.json', this.postBlog)
            .then(function(res){
                console.log(res)
                swal("Successful! ", "Blog Post created!", "success")
            })
            .catch(function(error){
                console.log(error)
            }))
            this.postBlog = {
                            title : '',
                            categories: '',
                            content : '',
                            author : '',
                        }
                
        }
    }
}
</script>
<style scoped>
.text_edit{
    font-size: 40px !important;
    text-align: center;
    color: #521751;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-weight: 400px;
}
.text_edit2{
    font-size: 20px !important;
    text-align: center;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>