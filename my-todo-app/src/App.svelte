<script>
// do the part a button to make more buttons
$: categories = [
		{ done: false, text: 'General' },
		{ done: false, text: 'Homework'},
		{ done: false, text: 'Chores'}
	];

	function add() {
		categories = [{
			done: false,
			text: ''
		}, ...categories];
		//categories = categories.concat({ done: false, text: '' });
	}

	function showlabel(categories) {
		categories.forEach(category => {
			if (category.done===true){
				return category.text;
			}
		});
	}


	$: taskstodo = todos1.length;
	$: selected = "";
	$: selected1 = {done: false,
					text: ''};
	let mytasks = [];

	let todos1 = [];
	let bigTasks1 = []
	let task1 = "";
	let bigTask1 = "";
	let filter1='all';


	function addTask1(){
		//taskstodo = taskstodo + 1;
		todos1 = [{
			task1:task1,
			status1:"pending",
			category: selected
		}, ...todos1];
		task1 = "";
		assignsubCategories()
	}
	function assignsubCategories() {
		mytasks = []
		todos1.forEach(element => {if (element.category === selected) {
  		mytasks = [...mytasks,element]}})
	}
	function markComplete1(i){
		todos1[i].status1 = "completed";
		//taskstodo = taskstodo - 1;
		todos1 = [...todos1];
	}
	function removeTask1(i){
		if(i.status==='incomplete') {
			//taskstodo = taskstodo - 1;
		}
		console.log(taskstodo);
		todos1.splice(i,1);
		todos1 = [...todos1];
	}
	function addBigTask1(){
		bigTasks1 = [{
			bigTask1:bigTask1,
			subCategories1: []
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
		<div>
			<input
				type=checkbox
				bind:group={selected} 
				value={category.text}
				on:input={assignsubCategories}	

			>
			<input
				placeholder="Enter new category"
				value={category.text}
			>
		</div>
		{/each}
		<!--<button on:click={add}>
			Add new
		</button> -->
	
	</div>	
	
		<div class="taskBox">
			<div>
				{#if selected === "" }
				<p>Click on a Category to add Tasks</p>
				{/if}
                <h2 id = "taskheader">
					{selected}
				</h2>
				
                <p id = "taskremaining"> {taskstodo} tasks remaining</p>
            </div>


			<div class="todo1">     
				<div class="tasks1">
					{#each mytasks as todo1, i}
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
					{#if selected != "" }
					<div class="form">
						
						<input type="text" bind:value={task1}/>
						<button on:click={addTask1}>
							Add
						</button>
						
					</div>
					{/if}




			</div>
		
			{#if selected != "" }
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
			{/if}
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

