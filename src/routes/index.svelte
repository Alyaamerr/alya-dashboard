<script>
    import supabase from "$lib/db";
  
    // let timetable = {
    //   Monday: [],
    //   Tuesday: [],
    //   Wednesday: [],
    //   Thursday: [],
    //   Friday: [],
    // };
  
    let timetable = {
      Monday: [
        {
          name: "PH",
          period: 1,
          style: "",
        },
        {
          name: "PM",
          period: 1,
          style: "",
        },
        {
          name: "BI",
          period: 2,
          style: "",
        },
        {
          name: "R",
          period: 1,
          style: "table-success",
        },
        {
          name: "BM",
          period: 2,
          style: "",
        },
        {
          name: "M3",
          period: 2,
          style: "",
        },
        {
          name: "BC",
          period: 2,
          style: "",
        },
      ],
      Tuesday: [
        {
          name: "PJPK",
          period: 1,
          style: "",
        },
        {
          name: "M3",
          period: 2,
          style: "",
        },
        {
          name: "BI",
          period: 1,
          style: "",
        },
        {
          name: "E",
          period: 1,
          style: "table-success",
        },
        {
          name: "BM",
          period: 2,
          style: "",
        },
        {
          name: "BC",
          period: 3,
          style: "",
        },
        {
          name: "PJPK",
          period: 1,
          style: "",
        },
      ],
      Wednesday: [
        {
          name: "BC",
          period: 3,
          style: "",
        },
        {
          name: "PM",
          period: 1,
          style: "",
        },
        {
          name: "H",
          period: 1,
          style: "table-success",
        },
        {
          name: "PKS",
          period: 3,
          style: "",
        },
        {
          name: "BM",
          period: 2,
          style: "",
        },
      ],
      Thursday: [
        {
          name: "SA",
          period: 1,
          style: "",
        },
        {
          name: "PJPK",
          period: 1,
          style: "",
        },
        {
          name: "BM",
          period: 2,
          style: "",
        },
        {
          name: "A",
          period: 1,
          style: "table-success",
        },
        {
          name: "PM",
          period: 1,
          style: "",
        },
        {
          name: "BC",
          period: 2,
          style: "",
        },
        {
          name: "M3",
          period: 2,
          style: "",
        },
      ],
      Friday: [
        {
          name: "BI",
          period: 2,
          style: "",
        },
        {
          name: "BM",
          period: 2,
          style: "",
        },
        {
          name: "T",
          period: 1,
          style: "table-success",
        },
        {
          name: "BC",
          period: 2,
          style: "",
        },
        {
          name: "PM",
          period: 1,
          style: "",
        },
        {
          name: "SA",
          period: 2,
          style: "",
        },
      ],
    };

    let curDay;
  let curIndex;
  let curName;
  let curPeriod;
  let curStyle;

  function showCurData(day, index, name, period, style) {
	curDay = day;
	curIndex = index;
	curName = name;
	curPeriod = period;
	curStyle = style;
  }

    function addTimeSlot(day) {
	if (day === "Monday") {
  	timetable.Monday = [
    	...timetable.Monday,
    	{ name: "??", period: 1, style: "" },
  	];
	} else if (day === "Tuesday") {
  	timetable.Tuesday = [
    	...timetable.Tuesday,
    	{ name: "??", period: 1, style: "" },
  	];
	} else if (day === "Wednesday") {
  	timetable.Wednesday = [
    	...timetable.Wednesday,
    	{ name: "??", period: 1, style: "" },
  	];
	} else if (day === "Thursday") {
  	timetable.Thursday = [
    	...timetable.Thursday,
    	{ name: "??", period: 1, style: "" },
  	];
	} else if (day === "Friday") {
  	timetable.Friday = [
    	...timetable.Friday,
    	{ name: "??", period: 1, style: "" },
  	];
	}
  }
    </script>
  
    <div class="container mt-5">
  <h1>My Dashboard</h1>
  <table class="table table-bordered table-striped text-center caption-top">
	<caption>School Timetable</caption>
	<thead>
  	<tr class="table-dark">
    	<th scope="col">#</th>
    	<th scope="col">1</th>
    	<th scope="col">2</th>
    	<th scope="col">3</th>
    	<th scope="col">4</th>
    	<th scope="col">-</th>
    	<th scope="col">5</th>
    	<th scope="col">6</th>
    	<th scope="col">7</th>
    	<th scope="col">8</th>
    	<th scope="col">9</th>
    	<th scope="col">10</th>
  	</tr>
	</thead>
	<tbody>
  	<tr>
    	<th scope="row" class="table-dark">MON</th>
    	{#each timetable.Monday as timeSlot, index}
      	<td colspan={timeSlot.period} class={timeSlot.style}>
        	<button
          	type="button"
          	class="btn"
            data-bs-toggle="modal"
          	data-bs-target="#editTimeSlot"
            on:click={() =>
            	showCurData(
              	"Monday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
        	>
          	{timeSlot.name}
        	</button>
      	</td>
    	{/each}
      <td>
      	<button on:click={() => addTimeSlot("Monday")} class="btn">+</button>
    	</td>
  	</tr>
  	<tr>
    	<th scope="row" class="table-dark">TUE</th>
    	{#each timetable.Tuesday as timeSlot, index}
      	<td colspan={timeSlot.period} class={timeSlot.style}>
        	<button
          	type="button"
          	class="btn"
            data-bs-toggle="modal"
          	data-bs-target="#editTimeSlot"
            on:click={() =>
            	showCurData(
              	"Monday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
        	>
          	{timeSlot.name}
        	</button>
      	</td>
    	{/each}
      <td>
      	<button on:click={() => addTimeSlot("Tuesday")} class="btn">+</button>
    	</td>
  	</tr>
  	<tr>
    	<th scope="row" class="table-dark">WED</th>
    	{#each timetable.Wednesday as timeSlot, index}
      	<td colspan={timeSlot.period} class={timeSlot.style}>
        	<button
          	type="button"
          	class="btn"
            data-bs-toggle="modal"
          	data-bs-target="#editTimeSlot"
            on:click={() =>
            	showCurData(
              	"Monday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
        	>
          	{timeSlot.name}
        	</button>
      	</td>
    	{/each}
      <td>
      	<button on:click={() => addTimeSlot("Wedensday")} class="btn">+</button>
    	</td>
  	</tr>
  	<tr>
    	<th scope="row" class="table-dark">THU</th>
    	{#each timetable.Thursday as timeSlot, index}
      	<td colspan={timeSlot.period} class={timeSlot.style}>
        	<button
          	type="button"
          	class="btn"
            data-bs-toggle="modal"
          	data-bs-target="#editTimeSlot"
            on:click={() =>
            	showCurData(
              	"Monday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
        	>
          	{timeSlot.name}
        	</button>
      	</td>
    	{/each}
      <td>
      	<button on:click={() => addTimeSlot("Thursday")} class="btn">+</button>
    	</td>
  	</tr>
  	<tr>
    	<th scope="row" class="table-dark">FRI</th>
    	{#each timetable.Friday as timeSlot, index}
      	<td colspan={timeSlot.period} class={timeSlot.style}>
        	<button
          	type="button"
          	class="btn"
            data-bs-toggle="modal"
          	data-bs-target="#editTimeSlot"
            on:click={() =>
            	showCurData(
              	"Monday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
        	>
          	{timeSlot.name}
        	</button>
      	</td>
    	{/each}
      <td>
      	<button on:click={() => addTimeSlot("Friday")} class="btn">+</button>
    	</td>
  	</tr>
	</tbody>
  </table>
</div>

<!-- Modal Edit Time Slot -->
<div
  class="modal fade"
  id="editTimeSlot"
  tabindex="-1"
  aria-labelledby="modalLabel"
  aria-hidden="true"
>
  <div class="modal-dialog">
	<div class="modal-content">
  	<div class="modal-header">
    	<h5 class="modal-title" id="modalLabel">Edit Time Slot</h5>
    	<button
      	type="button"
      	class="btn-close"
      	data-bs-dismiss="modal"
      	aria-label="Close"
    	/>
  	</div>
  	<div class="modal-body">
    	<div class="input-group mb-3">
      	<span class="input-group-text" id="basic-addon1">Name</span>
      	<input type="text" class="form-control" bind:value={curName} />
    	</div>
    	<div class="input-group mb-3">
      	<span class="input-group-text" id="basic-addon1">Period</span>
      	<input type="number" class="form-control" bind:value={curPeriod} />
    	</div>
    	<div class="input-group mb-3">
      	<label class="input-group-text" for="styleSelect">Style</label>
      	<select class="form-select" id="styleSelect" bind:value={curStyle}>
        	<option value="">Default</option>
        	<option value="table-primary">Blue</option>
        	<option value="table-success">Green</option>
        	<option value="table-danger">Red</option>
        	<option value="table-warning">Yellow</option>
        	<option value="table-secondary">Grey</option>
      	</select>
    	</div>
  	</div>
  	<div class="modal-footer">
    	<button type="button" class="btn btn-secondary" data-bs-dismiss="modal"
      	>Cancel</button
    	>
    	<button
      	type="button"
      	class="btn btn-danger"
      	data-bs-dismiss="modal"
      	on:click={() => deleteTimeSlot(curDay, curIndex)}>Delete</button
    	>
    	<button
      	type="button"
      	class="btn btn-primary"
      	data-bs-dismiss="modal"
      	on:click={() =>
        	setTimeSlot(curDay, curIndex, curName, curPeriod, curStyle)}
      	>Save changes</button
    	>
  	</div>
	</div>
  </div>
</div>

<div class="text-center mt-5">
  <button class="btn btn-dark" on:click={logout}>Log Out</button>
</div>