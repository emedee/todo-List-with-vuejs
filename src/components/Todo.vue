<template>
    <!-- <div class="container to-do">
        <div class="container mt-5">
            <h1>todos!</h1>
            <p class="p1">Add you first to-do</p>
            <img src="/src/assets/logo.jpg" alt="">
            <p class="p2">What do you want to get done today?</p>
            <input type="text" name="" id="" placeholder="E.g Build a web app" class="myInp mr-3"><button @click="addMyTodos" type="button" class="btn btn-primary">Submit</button>
        </div>

        <div class="container marg">
            <table class="table table-borderless">
                <thead>
                    <tr>
                    <th scope="col">#</th>
                    <th scope="col">todos</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(myTodo,i) in myTodos">
                    <th scope="row">{{parseInt(i) + 1}}</th>
                    <td>{{myTodo.item}}</td>
                    <td><button type="button" class="btn btn-secondary mr-3">Edit To-Do</button><button type="button" class="btn btn-danger">Delete To-Do</button></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div> -->

   <div class="myCenter">
        <div class="row justify-content-center">
            <div class="col-sm-5">
                <div class="card shadow p-4">
                    <div class="row">
                        <div class="col-md-12">
                            <div class="well">
                                <h2>Create a New Todo</h2>
                                <form>
                                    <div class="form-group">
                                        <label for="todoitem">What do you want to get done today??</label>
                                        <input type="text" v-model="myList.input" class="form-control" placeholder="E.g Build a web app" />
                                    </div>
                                    <button type="button" v-if="display" v-on:click="update" class="btn btn-secondary">Update</button>
                                    <button v-else type="button" v-on:click="addTodos()" class="btn btn-primary">Create</button>
                                </form>
                            </div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12 mt-5">
                            <h2>ToDos</h2>
                            <ul class="list-group">
                                <li v-for="(todo, index) in todos" :key="index" class="list-group-item">
                                    <p>{{ index + 1 }}- <span @click="strikeThrough(index)" class="myHov" >{{ todo }}</span>
                                    <span @click="deleteTodos(index)"><button type="button" class="close" aria-label="Close"><span aria-hidden="true">&times;</span></button></span>
                                    <span class="mys mr-2" @click="editTodos(todo)">Edit</span></p>       
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
   </div>
</template>

<script>
export default {
        data () {
            return {
                myList:{
                    input: "",
                },
                todos: [],
                display: false,
                completed: true,
            }
        },
        methods: {
            addTodos() {
                this.todos.push(this.myList.input);
                this.myList.input = "";
            },
            deleteTodos(index){
                this.todos.splice(index, 1)
            },
            editTodos(id){
                this.myList.input = id
                this.display = true
            },
            update(){
                Swal.fire(
                    'Good job!',
                    'You Updated your toDos',
                    'success'
                )
                this.display = false;
                this.myList.input = "";
            },
            strikeThrough(index){
                this.completed = false;
            },
        }
}
</script>

<style scoped>
.mys{
    float: right;
    width: 70px;
    height: 40px;
    padding: 2px;
    text-align: center;
    color: gray;
    border-radius: 10px;
}
.myHov2{
    text-decoration: line-through;
}
.myHov:hover, .myHov2:hover{
    cursor: pointer;
}
.mys:hover{
    cursor: pointer;
}
@media screen {
    
}
</style>