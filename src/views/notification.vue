<template>
  <div class="container" >
      <navbar />
      <br>
      <div class="butn">
          <button class="signup" @click="onsubmitlatest">Latest</button>
          <button class="signup" @click="onsubmit">Old</button>
      </div>
      <div class="feed" id ="feed" style="margin: 0px 6px;">
          <div id="notifications-container"  v-if="notificationHistory">

                <div class="post" v-for="notification in notificationHistory" :key="notification.id">
                    <div class="plaf" >
                        <span v-if="notification.postedBy.profilePic">
                            <img class = "avatar" :src='notification.postedBy.profilePic' alt="avatar">
                        </span>
                        <span v-else>
                        <img class="avatar" src="https://www.pngitem.com/pimgs/m/78-786293_1240-x-1240-0-avatar-profile-icon-png.png" alt="Avatar">    
                        </span>
                        
                        <div class="feed" style="height: 100px; ">
                            <p> Notification</p>
                            <span v-if="notification.eventType === 'NEWPOST' ">
                                <h2>{{notification.postedBy.fullName}} made a new post</h2>
                            </span>
                            <span v-else-if="notification.eventType === 'FRNDREQ'">
                                <h2><a href="">{{notification.userBaseProfile.fullName}}</a> has sent you a Friend Request</h2>
                                <h3>You and {{notificationuser.BaseProfile.fullName}} are friends now!</h3>
                            </span>
                            <span v-else-if="notification.eventType === 'FRNDREQACC'">
                                <h2>{{notification.acceptedBy.fullName}} has accepted your friend Request</h2>
                            </span>
                            
                        </div>
                    </div>
                </div>
          </div>
          <div v-else>
              <center>
                   <h2>No Recent Notifications</h2>
              </center>
               
          </div>
      </div>
      <div class="butn"></div>
  </div>
</template>
<script>
import axios from 'axios'
import navbar from "../components/navbar.vue"
export default {
    data () {
        return{
            notificationHistory:'',
            index: 0,
            image: null,
            images: [{
                id: 1,
                src: "http://localhost:8080/img/thumbs-down.76c1523f.svg",
                },
                {
                id: 2,
                src: "https://drive.google.com/file/d/1XNzb_sq9mZW4AM9WHvX2-LfaHahlEzVc/view?usp=sharing",
                }
            ]
        }
    },
    
    components:{
        navbar
    },
    methods: {
    
        onsubmit () {
            const obj = {
                sessionId: localStorage.getItem('sessionID')
            }
            
            console.log("for old notifications page")
            axios.post("http://10.177.68.60:8089/notificationHistory",obj).then(res => {
                this.notificationHistory = res.data.notificationHistory
                console.log(this.notificationHistory)
                })
                .catch(err=> console.log(err))
        },
        onsubmitlatest () {
            const obj = {
                sessionId: localStorage.getItem('sessionID')
            }
            
            console.log("for latest notifications page")
            axios.post("http://10.177.68.60:8089/latestNotifications",obj).then(res => {
                this.notificationHistory = res.data.latestNotifications
                 console.log(this.notificationHistory)
                })
                .catch(err=> console.log(err))
        }
    },
    mounted() {
        this.onsubmitlatest()
    },
    
}
</script>
<style scoped>
.plaf{
    display: flex;
    justify-content: space-between;
}
.avatar {
    vertical-align: middle;
    width: 104px;
    height: 100px;
    border-radius: 50%;
    position: relative;
    top: -15px;
    margin-left: -2px;
}
.container{
  height: 700px;
}
.feed{
  width: 1000px;
  float: center;
  height: 700px;
  position: inherit;
  border: grey 2px solid;
  overflow: scroll;
  box-shadow: 7px 4px 5px 1px rgb(0, 0, 0);
}
.post{
    margin: 30px;
    width: 87%;
    height: 14%;
    padding: 29px 8px 10px;
    text-align: center;
    overflow: scroll;
}
.butn{
    height: 200px;
    width:300px;
    float:right;
    margin: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
}
.signup{
   height:30px;
   width: 100px;
   margin: 10px;
   color: green;
    box-shadow: 7px 4px 5px 1px rgb(0, 0, 0);
    
}
</style>