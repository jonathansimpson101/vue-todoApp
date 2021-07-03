<template>
  <div id="app">
    <div class='container'>

      <h1>ToDo List</h1>
        <div class="input-container">
        <input
          type="text"
          class='input'
          v-model="newToDo"
        />
        <button class="add-button" @click='add()'>Add </button>
      </div>
      <ul>
        <li v-for='(todo, index) in existingToDo' :key="index">
          <span>
            {{index + 1}}. {{todo.text}}
          </span>
          <button class="delete-button" @click="deleteToDo(index)">❌</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style>

  *{
    padding:  0;
    margin:  0;
    box-sizing: border-box;
  }

  #app{
    height:  100vh;
    width:  100vw;
    padding-top:  50px;
    background-color:  #fff;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    font-family: 'Helvetica';
    background-color: #66c3cc;
  }

  .container{
    width: 40vw;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.6),
                0 0 20px rgba(0, 0, 0, 0.4);
    border-radius: 10px;
    background-color:  #fff;
    padding-right: 10px;
    padding-left: 10px;
    max-width: 400px;
  }


  .container > h1 {
    margin-top: 20px;
  }

  .input-container{
    margin-top: 20px;
    width:  80%;
    height: 30px;
  }

  input{
    height:  100%;
    width:  calc(100% - 60px);
    margin-right: 20px;
  }

  .input-container > button {
    height: 100%;
    width:  40px;
  }

  ul{
    list-style-type: none;
    width: 95%;
    text-align: center;
    background-color:  white;
    margin-top: 10px;
    padding-top: 10px;
    padding-bottom: 10px;
  }

  li{
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid rgba(0, 0, 0, 0.2);
    margin-bottom: 10px;
  }

  .delete-button{
    background-color:  #fff;
    border: none;
  }

@media (max-width: 600px){
  .container{
    width:  90%;
  }
}


</style>

<script>

export default {
  name: 'App',
  data () {
    return {
      newToDo:'',
      existingToDo: [
      {text: 'Get Groceries', id: 0},
      {text: 'Run errands', id: 1},
      {text: 'Walk dog', id: 2},
      ]
    };
  },
  methods: {
    add () {
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf()
      }),
      this.newToDo='';
    },
    deleteToDo(index){
      this.existingToDo.splice(index, 1)
    }
  }
}
</script>

