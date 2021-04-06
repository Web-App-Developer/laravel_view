<template>
  <div  :class="[creator? ' logged-in': '',isAdminPage? 'is-admin-page':'']">
    <div v-if="isAuthPage === false">
          <navigation :creator="creator" :user="user" ref="nav"/>
    </div>

    <router-view :creator="creator" :user="user" class="page-content" :class="$root.isMobile ? 'mobile-content' : '' " />
    <div v-if="isAuthPage === false">
        <app-footer v-if="!isAdminPage"/>  
    </div>
    
  </div>
</template>

<script>
import User from "../../apis/User";
import Api from "../../apis/Api";
export default {
  data() {
    return {
      user:null,
      creator:null,
      authAttempt:false,
      isAdminPage: false,
      isAuthPage:false,
    };
  },
  watch: {
    $route(val) {
      if(localStorage.auth && !this.authAttempt){
        this.authAttempt=true;
        var that=this;
        User.auth().then(response => {

          that.user = response.data;

          Api.get('/api/creator/'+that.user.id)
          .then(response => {
            that.creator=response.data;
          });
        });
      }
      if(this.$route.path.includes('/admin')){
        this.isAdminPage = true;
      }else{
        this.isAdminPage = false;
      }

     
    },
  },
  methods:{
  },
  created() {
    if(localStorage.auth && !this.authAttempt){
      this.authAttempt=true;
      var that=this;
      User.auth().then(response => {
        that.user = response.data;
        Api.get('/api/creator/'+that.user.id)
        .then(response => {
          that.creator=response.data;
        });
      });
    }
  },
  mounted() {
    if(this.$route.path.includes('/admin')){
      this.isAdminPage = true;
    }else{
      this.isAdminPage = false;
    }

     if(this.$route.path.includes('/login') || this.$route.path.includes('/register') ){
        this.isAuthPage = true;
      }else{
        this.isAuthPage = false;
      }
  }
};
</script>

<style>
.h-screen {
  height: 100vh;
}
</style>
