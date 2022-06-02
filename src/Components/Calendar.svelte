<script>
	import { fade } from 'svelte/transition';
    import { Spinner } from 'sveltestrap';

    const decapitalize = ([first, ...rest], upperRest = false) => first.toLowerCase() + (upperRest ? rest.join('').toUpperCase() : rest.join(''));

    async function getCalData() {
        let x = await fetch('https://nextjs-backend.azurewebsites.net/api/calendar').then((res) => res.json());
        let sanitised_data = [];

        x.forEach(element => {
            let {summary, start, end} = element;

            const dash = '-';
            const colon = ':';
            const [first, second, third, fourth] = [4, 6, 11, 13];

            const startDate = new Date(
                start.slice(0, first) +
                dash +
                start.slice(first, second) +
                dash +
                start.slice(second, third) +
                colon +
                start.slice(third, fourth) +
                colon +
                start.slice(fourth)
            );

            const endDate = new Date(
                end.slice(0, first) +
                dash +
                end.slice(first, second) +
                dash +
                end.slice(second, third) +
                colon +
                end.slice(third, fourth) +
                colon +
                end.slice(fourth)
            );

            const options = {
                weekday: 'short',
            };

            const optionsTwo = {
                hour: '2-digit'
            };

            const day = new Intl.DateTimeFormat('en-US', options).format(startDate);
            const startTime = new Intl.DateTimeFormat('da-DK', optionsTwo).format(startDate);
            const endTime = new Intl.DateTimeFormat('da-DK', optionsTwo).format(endDate);

            sanitised_data.push({"summary": summary, "day": decapitalize(day), "start": 'h'+startTime, "end": 'h'+endTime})
        });

        return sanitised_data;
    }
</script>

<ul class="calendar weekly-byhour">
    {#await getCalData()}
        <!-- promise is pending -->
        <Spinner/>
    {:then value}
        <!-- promise was fulfilled -->
        {#each value as item, i}
            <li class="event" style="grid-column: {item.day}; grid-row: {item.start}/{item.end};" transition:fade="{{delay: 250 * (i + 1), duration: 300}}">{item.summary}</li>
        {/each}
    {/await}


    <!--  DAYS OF THE WEEK  -->
    <li class="day mon">Mon</li>
    <li class="day tue">Tue</li>
    <li class="day wed">Wed</li>
    <li class="day thu">Thu</li>
    <li class="day fri">Fri</li>
    <li class="day sat">Sat</li>
    <li class="day sun">Sun</li>

    <!--  TIMES OF THE DAY  -->
    <li class="time h00">00:00</li>
    <li class="time h01">1:00</li>
    <li class="time h02">2:00</li>
    <li class="time h03">3:00</li>
    <li class="time h04">4:00</li>
    <li class="time h05">5:00</li>
    <li class="time h06">6:00</li>
    <li class="time h07">7:00</li>
    <li class="time h08">8:00</li>
    <li class="time h09">9:00</li>
    <li class="time h10">10:00</li>
    <li class="time h11">11:00</li>
    <li class="time h12">12:00</li>
    <li class="time h13">13:00</li>
    <li class="time h14">14:00</li>
    <li class="time h15">15:00</li>
    <li class="time h16">16:00</li>
    <li class="time h17">17:00</li>
    <li class="time h18">18:00</li>
    <li class="time h19">19:00</li>
    <li class="time h20">20:00</li>
    <li class="time h21">21:00</li>
    <li class="time h22">22:00</li>
    <li class="time h23">23:00</li>

    <!--  TOP LEFT CORNER FILLER  -->
    <li class="corner"></li>

    <!--  EMPTY HOURLY FILLERS:
    Helps us show the grid template lines, and create calendar funtionality later. One for every hour
    cell (7 * 24), because our events are "position:absolute" and will sit over top of empty cells -->
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>

<style>
	/* GRID SETUP */
	.calendar {
		display: grid;
		grid-gap: 1px;
		background-color: #eee;
		position: fixed;
		width: 50%;
		height: 824px;
        padding-left: 0;
	}

	.weekly-byhour {
		/* NAMED LINE NUMBERS (between tracks): 
				COLS: hour markers + 7 days
				ROWS: day markers + 24 hours */
		grid-template-columns: 
			[time] auto [mon] 1fr [tue] 1fr [wed] 1fr [thu] 1fr [fri] 1fr [sat] 1fr [sun] 1fr [end-col];
		grid-template-rows:
			[day]  auto
			[h01]  1fr 
			[h02]  1fr 
			[h03]  1fr 
			[h04]  1fr 
			[h05]  1fr
			[h06]  1fr
			[h07]  1fr 
			[h08]  1fr
			[h09]  1fr
			[h10]  1fr 
			[h11]  1fr 
			[h12]  1fr 
			[h13]  1fr 
			[h14]  1fr 
			[h15]  1fr 
			[h16]  1fr 
			[h17]  1fr 
			[h18]  1fr 
			[h19]  1fr 
			[h20]  1fr 
			[h21]  1fr 
			[h22]  1fr 
			[h23]  1fr 
			[h00]  1fr 
			[end-row];
	}

	/* GENERAL ITEM SETUP */
	.calendar li {
		background-color: white;
		padding: 0.25em;
		display: inline-block;
	}

	/* ITEM TYPES */
	li.day, li.time, li.corner { background-color: #f5f5f5; }
	li.day { text-align: center; }
	li.time { text-align: right; vertical-align: bottom; }
	li.event { background-color: #175f5c; color: white; position: absolute; height: 100%; width: 100%; }

	/* CATEGORIES */
	/*.event.work { background-color: #fecf6a; }
	.event.personal { background-color: #82caaf; }*/

	/* DAY HEADINGS   row / col */
	.sun { grid-area: day / sun; }
	.mon { grid-area: day / mon; }
	.tue { grid-area: day / tue; }
	.wed { grid-area: day / wed; }
	.thu { grid-area: day / thu; }
	.fri { grid-area: day / fri; }
	.sat { grid-area: day / sat; }

	/* TIME HEADINGS  row / col */
	.h00 { grid-area: h00 / time; }
	.h01 { grid-area: h01 / time; }
	.h02 { grid-area: h02 / time; }
	.h03 { grid-area: h03 / time; }
	.h04 { grid-area: h04 / time; }
	.h05 { grid-area: h05 / time; }
	.h06 { grid-area: h06 / time; }
	.h07 { grid-area: h07 / time; }
	.h08 { grid-area: h08 / time; }
	.h09 { grid-area: h09 / time; }
	.h10 { grid-area: h10 / time; }
	.h11 { grid-area: h11 / time; }
	.h12 { grid-area: h12 / time; }
	.h13 { grid-area: h13 / time; }
	.h14 { grid-area: h14 / time; }
	.h15 { grid-area: h15 / time; }
	.h16 { grid-area: h16 / time; }
	.h17 { grid-area: h17 / time; }
	.h18 { grid-area: h18 / time; }
	.h19 { grid-area: h19 / time; }
	.h20 { grid-area: h20 / time; }
	.h21 { grid-area: h21 / time; }
	.h22 { grid-area: h22 / time; }
	.h23 { grid-area: h23 / time; }
</style>