<script>
    export let name;
</script>

<main>
    <head>

        <title>To Do List</title>
    </head>
    <body>
        <h1>Jumana's To Do List</h1>
        <hr>
        <div class = "categoryBox">
            <h2>Categories</h2>
            <ul class = "categoryList">
                <li class = "category_name">General</li>
                <li class = "category_name">Homework</li>
                <li class = "category_name">Chores</li>
            </ul>

            <form action="">
                <input 
                    type = "text"
                    class = "new_category"
                    placeholder = "Enter New Category"
                    aria-label="new_category_name"
                />
            
            <button class="btn_create" aria-label="create_new_category">+</button>   
            </form>
        </div>

        <div class="taskBox">
            <div>
                <h2 id = "taskheader">General</h2>
                <p id = "taskremaining">2 tasks remaining</p>
            </div>

            <div class="toDoTaskListBody">
                <div class="task">
                    <div class="task">
                        <input type="checkbox" id="task1"/>
                        <label for="task1" class ="label1">
                            <span class="customCheckbox"></span>
                            Complete all Chores
                        </label>
                    </div>
                    <!--task 1 under General above-->

                    <div class="task">
                        <div class="task">
                            <input type="checkbox" id="task2"/>
                            <label for="task2" class ="label1">
                                <span class="customCheckbox"></span>
                                Complete all Homework
                            </label>
                        </div>
                        <!--task 2 under General above-->
                </div>

                <div class="createNewTask">  <!-- enter new task for the list at the bottom of task list-->
                    <form action="">
                        <input 
                          type="text"
                          class="new_task"
                          placeholder="Enter New Task"
                          aria-label="new_task_name"
                        />
                        <button class="btn_create" aria-label="create_new_task">+</button>
                      </form>

                </div>

                <div class="delete">  <!--button on bottom of list to delete-->
                    <button class="btn_delete">Clear All Finished Tasks</button>
                    <button class="btn_delete">Delete this List</button>
                </div>

            </div>
        </div>
    </body>
</main>

<style>
    body{
        background-color: #d6cbd3;
        font-family: Verdana;

    }
    h1 {
        font-size: 80px;
        margin-top: 0;
        color: #5979bd;
        text-align: center;
    }
    h2 {
        font-size: 40px;
        color: #d6e0e9;
        text-align: center;
        margin-top: 10px;
    }
    .categoryBox {
        
        text-align: center;
        height: fit-content;
        width: 28%;
        float:left;
        background-color: #B0C4DE;
        margin-top: 100px;
        
    }
    .taskBox {  
        text-align: center;
        height: fit-content;
        width: 65%; 
        float: right;
        background-color: #ADD8E6;
        margin-right: 20px;
        margin-left: 10px;
        margin-top: 70px;
    }
    #taskheader {
        background-color: DarkGrey;
        font-size:80px ;
        text-align: left;
        margin-top: 0;
        margin-bottom: 0;
        color: rgb(228, 248, 250);
        
    }
    #taskremaining {
        text-align: right;
        margin-right: 10px;
        font-size: 15px;
    }
    li {
        text-align: left;
    }
    
    form {
        margin-bottom: 10px;
        margin-top: 10px;
        margin-left: 2px;
        margin-right: 2px;
    }
    :global(body) {
        background-color: #f2eee2;
        font-size: 20px;
    }
    
</style>

