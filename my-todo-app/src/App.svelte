<script>


// do the part a button to make more buttons
let categories = [
		{ done: false, text: 'General' },
		{ done: false, text: 'Homework'},
		{ done: false, text: 'Chores'}
	];

	function add() {
		categories = categories.concat({ done: false, text: '' });
	}

	/*function deletecategory() {
		if (categories.done) 
			categories = categories.;		
	}*/



//do the task remaining

/*function taskleft() {
	/*todos1.forEach(todo => {
		if (todo.status == 'incomplete'){
			count = count + 1;
		}
	});	
	return taskstodo;
}*/




//do the label changing accoring to what button was clicked
 


	"first do the same thing for the general that you did for the todos portion"
	"so you will have two different arrays that aren't related to each other/"
	"Once yuo do that you will have a click action on each task that should toggle"
	"the categories section "

	"What you can do is "
	$: taskstodo = 0;


	let todos1 = []
	let bigTasks1 = []
	let subCategories1 = []
	let task1 = "";
	let bigTask1 = "";
	let filter1='all';
	function addTask1(){
		taskstodo = taskstodo + 1;
		todos1 = [{
			task1:task1,
			status1:"pending"
		}, ...todos1];
		task1 = "";
	}
	function markComplete1(i){
		todos1[i].status1 = "completed";
		taskstodo = taskstodo - 1;
		console.log("Suh dudes marking as complete");
		todos1 = [...todos1];
	}
	function removeTask1(i){
		if(i.status==='incomplete') {
			taskstodo = taskstodo - 1;
		}
		console.log(taskstodo);
		todos1.splice(i,1);
		todos1 = [...todos1];
	}
	function addBigTask1(){
		bigTasks1 = [{
			bigTask1:bigTask1,
			subCategories1: todos1

		}, ...bigTasks1];
		bigTask1 = "";
	}


	
</script>

<main>
    <head>

        <title>To Do List</title>
		
    </head>
    <body>
        <h1>Jumana's To Do List</h1>
        <hr>


	<div class ="categoryBox">
		<h2>Categories</h2>
		{#each categories as category}
		<div class:done={category.done}>
			<input
				type=checkbox
				checked={category.done}
			>

			<input
				placeholder="Enter new category"
				value={category.text}
			>
		</div>
		{/each}


		<button on:click={add}>
			Add new
		</button>
		<!--<button on:click={deletecategory}>
			Delete Checked List
		</button>-->
		

	
	</div>	



		<!--
        <div class = "categoryBox">
            <h2>Categories</h2>
            <ul class = "categoryList" data-category>
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
-->
		<div class="taskBox">
			<div>


                <h2 id = "taskheader">
					{#each categories as category}
						{#if category.done}
							hello {category.text}
						{/if}
					{/each}
				</h2>



				
                <p id = "taskremaining"> {taskstodo} tasks remaining</p>
            </div>

			<div class="todo1">     
				<div class="tasks1">
					{#each todos1 as todo1, i}
						{#if filter1=='all'}
							<div class="task1">
								<div>
									{todo1.task1}
								</div>
								<button class="{todo1.status1=='completed'?'active':''}" on:click={()=>{markComplete1(i)}}>
									&#10004;
								</button>
								<button on:click={()=>{removeTask1(i)}}>
									&#10006;
								</button>
							</div>
						{:else if filter1=='completed'}
							{#if todo1.status1=='completed'}
								<div class="task">
									<div>
										{todo1.task1}
									</div>
									<button on:click={()=>{removeTask1(i)}}>
										&#10006;
									</button>
								</div>
							{/if}
						{:else}
							{#if todo1.status1=='pending'}
								<div class="task">
									<div>
										{todo1.task1}
									</div>
									<button class="{todo1.status1=='completed'?'active':''}" on:click={()=>{markComplete1(i)}}>
										&#10004;
									</button>
								</div>
							{/if}
						{/if}
					{/each}
					<div class="form">
						<input type="text" bind:value={task1}/>
						<button on:click={addTask1}>
							Add
						</button>
					</div>
			</div>
			<div class="filters">
				<button class="{filter1=='all'?'active':''}" on:click={()=>{filter1='all'}}>
					All
				</button>
				<button class="{filter1=='completed'?'active':''}" on:click={()=>{filter1='completed'}}>
					Completed
				</button>
				<button class="{filter1=='incomplete'?'active':''}" on:click={()=>{filter1='incomplete'}}>
					Incomplete
				</button>
			</div>
		</div>










<!-- 
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
                    </div>    -->
                    <!--task 1 under General above-->
<!-- 
                    <div class="task">
                        <div class="task">
                            <input type="checkbox" id="task2"/>
                            <label for="task2" class ="label1">
                                <span class="customCheckbox"></span>
                                Complete all Homework
                            </label>
                        </div>   -->
                        <!--task 2 under General above-->
 <!--                </div>

                <div class="createNewTask">  <!-- enter new task for the list at the bottom of task list-->
 <!--                    <form action="">
                        <input 
                          type="text" bind:value={bigTask}
                          class="new_task"
                          placeholder="Enter New Task"
                          aria-label="new_task_name"
                        />

                        <button on:click={addBigTask} class="btn_create" aria-label="create_new_task">+</button>
                      </form>

                </div>


            </div>
        </div>   -->




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
		margin-bottom: 5px;
        
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

