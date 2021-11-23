<template>
    <div>
      <div class="main-container">
        <div class="main">
          <h3>Devfinder</h3>
        </div>

        <form class="search-box" >
          <input class="search-text" type="text" name="Search User" placeholder="Search User" v-model="username">
          <button class="search-btn" ><i @click="getUserInfo" class="fas fa-search"></i></button>
        </form>
      </div>
    </div>
</template>

<script>
  import {ref} from "vue"; 
  import axios from "axios";
  export default {
    
    setup() {
      const username = ref("");
      const users =  ref(null);

      const getUserInfo = async () => {
        try {
          const response = await axios.get(`https://api.github.com/users/${username.value}`);
          const result = response.data;
          console.log(result)
        } catch (error) {
          alert(error.message);
        }
      };
      return {
        username,
        users,
        getUserInfo
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main-container{
    margin: 50px auto;
    padding:45px;
    width: 800px;
    height:300px;
    color: white;
  }

  .search-box{
    position: absolute;
    top: 35%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: #30336b;
    height: 50px;
    border-radius: 40px;
    padding: 10px;
    color: whitesmoke;
  }

  .search-btn{
    color: #535c68;
    float: right;
    width:27px;
    height: 27px;
    border-radius: 50%;
    background: white;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: 0.4s;
    cursor: pointer;
    border: none;
  }

  .search-btn:hover{
    color:  white;
    background: #30336b;
  }

  .search-text{
    border: none;
    background: none;
    outline: none;
    float: left;
    padding: 0;
    color: white;
    font-size: 16px;
    transition: 0.4s;
    line-height: 28px;
    width: 0px;
    width:600px;
    padding: 0, 6px;
  }

</style>
