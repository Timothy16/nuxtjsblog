<template>
    <div>
        <div class="container mt-5">
            <div class="card mx-auto shadow p-3 mb-2 bg-white rounded" style="width:40%">
            <div class="card-body">
               <h1 class="text-center">Contact Us</h1>
               <p class="text-center">Got a question? We'd love to hear from you. Send us a message and we'll respond as soon as possible</p>
               <form @submit.prevent="sendMessage">
                <div class="form-group">
                    <label>Name</label>
                    <input type="text"  class="form-control" v-model="contactUs.name">
                </div>
                <div class="form-group">
                    <label>Email</label>
                    <input type="text"  class="form-control" v-model="contactUs.email" pattern="[^ @]*@[^ @]*">
                </div>
                <div class="form-group" >
                <label for="comment">Message</label>
                <textarea class="form-control" rows="5" id="comment" v-model="contactUs.message"></textarea>
                </div>
                <center>
                 <button type="submit" class="btn btn-outline-primary btn-lg">Send</button>
                 </center>
              </form>

            </div>
</div>
        </div>
    </div>
</template>

<script>
import swal from "sweetalert"
import axios from 'axios'
export default {
    data(){
        return {
            contactUs : {
                name : '',
                email : '',
                message : ''
            }
        }
    },
    methods : {
        sendMessage(){
             if(this.contactUs.name === '' || this.contactUs.email === '' || this.contactUs.message === ''){
         swal("hoops ", "Field cannot be empty!", "warning")
       }
          else(  axios.post('https://mynuxtjsblog.firebaseio.com/contect.json', this.contactUs)
            .then(function(res){
                console.log(res)
                swal("Thanks for Contacting Us!", "Message sent successfully!", "success")
            })
            .catch(function(error){
                console.log(error)
            }))
            this.contactUs = {
                name : '',
                email : '',
                message : ''    
        }
        }
        
    }
}
</script>

<style scoped>
h1{
    font-family: 'Times New Roman', Times, serif;
    font-size: 60px;
}
p{
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    font-size: 17px;
}
input {
  outline: 0;
  border-width: 0 0 1px 0;
  border-color: black;
}
textarea{
  outline: 0;
  border-width: 0 0 1px 0;
  border-color: black;
}
@media screen and (max-width : 700px){
    .card{
        width: 100% !important;
    }
}
</style>