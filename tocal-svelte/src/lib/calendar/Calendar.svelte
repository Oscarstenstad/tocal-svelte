<script>
    import Overlay from 'svelte-materialify';
    let today = new Date();
    let year = new Date().getFullYear();
    let month = new Date().getMonth();
    //let date = new Date().getDate();
    let weekdays = ["sun", "mon", "tue", "wed", "thu", "fri", "sat"];
    let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];

    let getDateInMonth = (year, month, date) => new Date(year, month, date).getDate();
    let getDayInMonth = (year, month, date) => new Date(year, month, date).getDay();

    let nextMonth = () => {
        if (month == 11) year+= 1;
        month = (month == 11 ? month = 0 : month+=1);
    }

    let prevMonth = () => {
        if (month == 0) year-=1;
        month = (month == 0 ? month = 11 : month-=1);
    }

    let displayCal = (year, month) => {
        var tmpDate = 1;
        const daysInMonth = [[], [], [], [], [], [], []];
            for (let i = 0; i < 6; i++){
                for (let j = 0; j < 7; j++) {
                    if (i==0 && j<getDayInMonth(year, month, tmpDate)) {
                        daysInMonth[i][j] = [[j], []];
                    } else if (tmpDate < getDateInMonth(year, month+1, 0)+1) {
                        daysInMonth[i][j] = [[getDayInMonth(year, month, tmpDate)], [getDateInMonth(year, month, tmpDate)]]; 
                        tmpDate++;
                    } else if (tmpDate >= getDateInMonth(year, month+1, 0)+1) {
                        daysInMonth[i][j] = [[j], []];
                        tmpDate++;
                    }
            }
        }
        console.log(daysInMonth);
        return daysInMonth;
    }

</script>

<main>
    <div id="calenderCon">
        <div id="calTopDiv">
            <div id="yearMonthDisp">
                <h2>{months[month]} {year}</h2>
            </div>
            <div id="buttonDiv">
                <button id="backButton" on:click={prevMonth}>back</button>
                <button id="nextButton" on:click={nextMonth}>next</button>
            </div>
        </div>
        <div>
            <table id="calTable">
                <thead>
                    <tr>
                    {#each weekdays as weekday}
                        <th class="weekdayCal">{weekday}</th>
                    {/each}
                    </tr>
                </thead>
                <tbody>
                    {#each displayCal(year, month) as week}
                        <tr>
                            {#each week as weekday} 
                                {#if weekday[0] == today.getDay() && weekday[1] == today.getDate() && month == today.getMonth() && year == today.getFullYear()}
                                    <td class="dayCal" id="todaysDate">{weekday[1]}</td>
                                {:else}
                                    <td class="dayCal">{weekday[1]}</td> 
                                {/if}
                            {/each}
                        </tr>
                    {/each}
                </tbody>
            </table>
        </div>
    </div>
</main>

<style>

</style>