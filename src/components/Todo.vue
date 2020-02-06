<template>
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
                                    <button type="button" v-if="display" v-on:click="update()" class="btn btn-secondary">Update</button>
                                    <button v-else type="button" v-on:click="addTodos()" class="btn btn-primary">Create</button>
                                </form>
                            </div>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-md-12 mt-5">
                            <center><h2>ToDos</h2></center>
                            <ul class="list-group">
                                <li v-for="(todo, index) in todos" :key="index" class="list-group-item">
                                    <p>{{ index + 1 }}- <span @click="strikeThrough(index)" class="myHov" >{{ todo }}</span>
                                    <span @click="deleteTodos(index)"><button type="button" class="close" aria-label="Close"><span aria-hidden="true">&times;</span></button></span>
                                    <span class="mys mr-2" @click="editTodos(todo)">Edit</span></p>       
                                </li>
                            </ul>
                        </div>
                        <div class="col-md-12 mt-5">
                            <center><h2>Done</h2></center>
                            <ul class="list-group">
                                <li v-for="(complete, i) in completed" :key="i" class="list-group-item">
                                    <p>{{ i + 1 }}- <span @click="strikeThrough(i)" class="myHov" >{{ complete }}</span></p>       
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

                completed: [],
                display: false,
                todoToUpdate: null,
                editField: null,
                
            }
        },
        methods: {
            addTodos() {
                if(this.myList.input === ''){
                    Swal.fire({
                        icon: 'error',
                        title: 'Oops...',
                        text: 'Please insert a to-do',
                    })
                }else{
                    this.todos.push(this.myList.input);
                    this.myList.input = "";
                }
            },
            deleteTodos(index){
                this.todos.splice(index, 1)
            },
            editTodos(id){
                this.myList.input = id
                this.display = true
                console.log(this.myList.input)
                this.todoToUpdate = this.todos.indexOf(id)
            },
            update(){
                Swal.fire(
                    'Good job!',
                    'You Updated your toDos',
                    'success'
                )
                this.display = false;
                this.todos[this.todoToUpdate] = this.myList.input;
                this.myList.input = "";
            },
            strikeThrough(i){
                console.log(this.todos[i])
                this.completed.push(this.todos[i]);
                this.todos.splice(i, 1)
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
@media (max-width: 575.98px) {
    span{
        font-size: 15px !important;
    }
    .mys{
        font-size: 15px !important;
        padding: 5px !important;
    }
}
</style>