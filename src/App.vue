<template>
  <div id="app" class="grid grid-rows-1 bg-green-800 w-full h-screen">
    <div class="bg-auto bg-green-800 p-2">
      <div class="grid grid-rows-1">
        <div class="grid grid-cols-1 pb-2 text-white">
          <div class="text-center p-10">
            <h1 class="h-19 text-5xl text-center uppercase">Work To-Dos</h1>
              <div class="grid grid-cols-1 pb-2 text-2xl ">
                <p class="tracking-wider" id="first">Enter text into the input field to add items to your list.</p>
                <p class="tracking-wider" id="second">Click the item to mark it as complete.</p>
                <p class="tracking-wider" id="third">Click the "X" to remove the item from your list.</p>
              </div>
          </div>
        </div>
    
      <div class="bg-green-800 grid grid-cols-5">
        <div class="col-start-2 col-span-3" >
          <input v-model="todoItemText" @keyup.enter="createTodo" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-900 leading-tight focus:outline-none focus:shadow-outline text-xl" id="userInput" type="text" placeholder="New Todo item..." maxlength="57"> 
        </div>
        <div class="bg-green-800 ml-2">
            <button @click="createTodo" class="rounded bg-blue-700" id="enter">
              <svg 
                viewBox="0 0 20 20" 
                fill="white" 
                class="pencil w-10 h-10  border border-white">
                    <path d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z"></path>
              </svg>
            </button>
          </div>
        </div>
      </div>

      <div class="bg-green-800 grid grid-cols-8">
        <div class="bg-green-800 col-start-2 col-span-6">
          <ul >
            <li 
              v-for ="(item,index) in todoItems" :key="index" 
              class="bg-green-400 shadow-inner rounded-lg p-2 m-4 text-2xl text-white text-center"
              >
              <div class="flex justify-between">
                <h2>{{item.todoText}}</h2>
                <svg 
                  viewBox="0 0 20 20" 
                  fill="currentColor" 
                  class="x w-10 h-10 text-center"
                  @click="onDeleteTodoItem(item.todoText)"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
              </div>
              
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {
    return {
      todoItemText:"",
      todoItems : []
    }
  },
  components: {
    
  },
  methods: {
    createTodo() {

      if (this.todoItemText === "") {

        alert("Todo Item cannot be empty. Please enter todo item text");

      } else {

        let items = this.todoItems.filter(value => value.todoText == this.todoItemText);
        console.log(items);

        if (items.length > 0) {

          alert('todo item already exists');

        } else {

          this.todoItems.push({todoText : this.todoItemText});
          this.todoItemText = "";
          
        }
        
      }
    },
    onDeleteTodoItem(todoItemText) {
      this.todoItems = this.todoItems.filter(item => item.todoText !== todoItemText)
    }
  }
}
</script>

<style src="./assets/css/tailwind.css">

</style>
