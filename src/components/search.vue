<template>
  <div class="insideSearch">
      <form id="content">
        <input type="text" name="input" v-model="input" class="input" id="search-input">
        <button @click="expand" type="reset" class="search" id="search-btn"></button>
       </form>
  </div>
</template>

<script>
export default {
    name:'example',
    data () {
        return{
            input:''
        }
    },
    methods: {
        expand() {
            const input = document.getElementById("search-input");
            const searchBtn = document.getElementById("search-btn");
           searchBtn.classList.toggle("close");
           input.classList.toggle("square");
        },
        validate(){
          if(this.input === ''){
            this.$alert("Don't you wanna stalk someone");
            return 0;
          }
          else{
            return 1;
          }
        }
    }
}


</script>

<style scoped>
body {
  background-color: #ff9800;
  color: #fff;
  margin: 0;
}

#content {
  height: 15px;
  width: 10px;
  margin-left: 170px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#content.on {
  -webkit-animation-name: in-out;
  animation-name: in-out;
  -webkit-animation-duration: 0.7s;
  animation-duration: 0.7s;
  -webkit-animation-timing-function: linear;
  animation-timing-function: linear;
  -webkit-animation-iteration-count: 1;
  animation-iteration-count: 1;
}

input {
  box-sizing: border-box;
  width: 50px;
  height: 50px;
  border: 4px solid #ffffff;
  border-radius: 50%;
  background: none;
  color: #fff;
  font-size: 16px;
  font-weight: 400;
  font-family: Roboto;
  outline: 0;
  -webkit-transition: width 0.4s ease-in-out, border-radius 0.8s ease-in-out,
    padding 0.2s;
  transition: width 0.4s ease-in-out, border-radius 0.8s ease-in-out,
    padding 0.2s;
  -webkit-transition-delay: 0.4s;
  transition-delay: 0.4s;
  -webkit-transform: translate(-100%, -50%);
  -ms-transform: translate(-100%, -50%);
  transform: translate(-100%, -50%);
}

.search {
  background: none;
  position: absolute;
  top: 0px;
  left: 0;
  height: 50px;
  width: 50px;
  padding: 0;
  border-radius: 100%;
  outline: 0;
  border: 0;
  color: inherit;
  cursor: pointer;
  -webkit-transition: 0.2s ease-in-out;
  transition: 0.2s ease-in-out;
  -webkit-transform: translate(-100%, -50%);
  -ms-transform: translate(-100%, -50%);
  transform: translate(-100%, -50%);
}

.search:before {
  content: "";
  position: absolute;
  width: 20px;
  height: 4px;
  background-color: #fff;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
  margin-top: 26px;
  margin-left: 17px;
  -webkit-transition: 0.2s ease-in-out;
  transition: 0.2s ease-in-out;
}

.close {
  -webkit-transition: 0.4s ease-in-out;
  transition: 0.4s ease-in-out;
  -webkit-transition-delay: 0.4s;
  transition-delay: 0.4s;
}

.close:before {
  content: "";
  position: absolute;
  width: 27px;
  height: 4px;
  margin-top: -1px;
  margin-left: -13px;
  background-color: #fff;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
  -webkit-transition: 0.2s ease-in-out;
  transition: 0.2s ease-in-out;
}

.close:after {
  content: "";
  position: absolute;
  width: 27px;
  height: 4px;
  background-color: #fff;
  margin-top: -1px;
  margin-left: -13px;
  cursor: pointer;
  -webkit-transform: rotate(-45deg);
  -ms-transform: rotate(-45deg);
  transform: rotate(-45deg);
}

.square {
  box-sizing: border-box;
  padding: 0 40px 0 10px;
  width: 300px;
  height: 50px;
  border: 4px solid #ffffff;
  border-radius: 0;
  background: none;
  color: #fff;
  font-family: Roboto;
  font-size: 16px;
  font-weight: 400;
  outline: 0;
  -webkit-transition: width 0.4s ease-in-out, border-radius 0.4s ease-in-out,
    padding 0.2s;
  transition: width 0.4s ease-in-out, border-radius 0.4s ease-in-out,
    padding 0.2s;
  -webkit-transition-delay: 0.4s, 0s, 0.4s;
  transition-delay: 0.4s, 0s, 0.4s;
  -webkit-transform: translate(-100%, -50%);
  -ms-transform: translate(-100%, -50%);
  transform: translate(-100%, -50%);
}

</style>
