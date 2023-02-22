<template>
     <div class="container" id="todo">
      <div class="inputPage">
        <form action="#" @submit.prevent="createdTodo">
          <input type="text" class="todo" placeholder="Create new todo..." v-model="form.text" minlength="2" maxlength="6">
          <br>
        </form>
      </div>
      <div v-for="item in fullName" :key="item" class="toDoTasks">
        <div class="all">
          <div class="tasks">
          <span>   {{ item.text }} </span>
          <div class="icons">
            <span @click="remove(item)" class="item">&nbsp;<img src="../assets/icons/trash-2.svg" alt="removeToDo"></span>
            <span @click="updateFunc(item)" class="item">&nbsp;<img src="../assets/icons/edit.svg" alt="editToDo"></span>
          </div>
        </div>
        </div>
        </div>
     </div>
</template>

<script>

export default {
  name: "TodoComponent",
 data() {
  return {
    form:{
      text: '',
    },
    fullName: [],
    update: false,
    currentIndex: null,
  }
  
 },
 methods:{
  createdTodo(){
    if(this.form.text === null  ||  this.form.text === ''){
      alert('Inputga ma`lumot kiriting')
    } else {
      if(this.update) {
        this.update = false
        this.fullName[this.currentIndex] = this.form
        this.form = { text: ''}
      }
      else {
       this.update = false
        this.fullName.push(this.form)
        this.form = { text: ''}
      }
    }
  },
  remove(item){
   const index = this.fullName.indexOf(item)
   this.fullName.splice(index , 1)
  },
  updateFunc(item){
    this.update = true
    this.currentIndex = this.fullName.findIndex((task) => task.text === item.text)
    this.form.text = item.text
  }
 },
 created(){
  console.log(this.form)
 }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  color: #000;
  font-family: "Open Sans";
}
body{
  color: black;
}
.container{
  width: 100%;
  height: 100vh;
}
.container .inputPage{
  width: 100%;
  height: 40vh;
  background-color: rgb(255, 116, 139);
  display: flex;
  justify-content: center;
  align-items: flex-end;
}
.inputPage input{
  border: 1px solid #999;
  height: 44px;
  width: 550px;
  text-align: center;
  outline: none;
  box-shadow: -1px 1px 1px #999;
  font-size: 16px;
  font-weight: 200;
}
.toDoTasks{
  width: 55%;
  height: 45px;
  margin: 0 auto;
}
.tasks{
  margin: 0;
  border: 1px solid #999;
  width: 100%;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.item{
  cursor: pointer;
}
.icons{
  margin-left: 380px;
}
.all{
  /* border: 0.5px solid gray; */
  margin-top: 15px;
  font-size: 25px;
  width: 550px;
  margin-left: 100px;
}
.inputPage input:focus{
  box-shadow: none;
  transition: .7s;
}
</style>