<template>
    <div class="main">
        <cal-header v-bind:month="month" 
                    v-bind:year="year" 
                    v-on:prev-month="previousMonth" 
                    v-on:next-month="nextMonth" />
        <cal-table v-bind:daysInMonth="daysInMonth" 
                   v-bind:targetDay="targetDay" 
                   v-on:select-day="selectDay" />
        <!-- <cal-events></cal-events> -->
    </div>
</template>

<script>
import CalHeader from './../components/CalHeader.vue'
import CalTable from './../components/CalTable.vue'
import CalEvents from './../components/CalEvents.vue'

export default {
    name: 'Calendar',
    components: {
        CalHeader,
        CalTable,
        CalEvents
    },
    methods: {
        setStartingPoint() {

            //Store the day of the week (0-6)
            let firstDayOfMonth = new Date(this.date.setDate(1));
            let dow = firstDayOfMonth.getDay();
            
            //Store the starting cell based on dow value
            this.startingCell = dow;

            //Store the month and year of today's date
            let monthNum = this.date.getMonth() + 1;
            let year = this.date.getFullYear();

            this.year = year;

            //Based on month, store the string value and total number of days
            switch(monthNum) {
                case 1:
                    this.month = "January";
                    this.totalDays = 31;
                    break;
                case 2:
                    this.month = "February";

                    //For Feb, need to check if year is a leap year before total
                    let isLeapYear = (new Date(year, 1, 29).getMonth() == 1);                    
                    this.totalDays = (isLeapYear) ? 29 : 28;
                    break;
                case 3:
                    this.month = "March";
                    this.totalDays = 31;
                    break;
                case 4:
                    this.month = "April";
                    this.totalDays = 30;
                    break;                    
                case 5:
                    this.month = "May";
                    this.totalDays = 31;
                    break;                    
                case 6:
                    this.month = "June";
                    this.totalDays = 30;
                    break;                    
                case 7:
                    this.month = "July";
                    this.totalDays = 31;
                    break;                    
                case 8:
                    this.month = "August";
                    this.totalDays = 31;
                    break;                    
                case 9:
                    this.month = "September";
                    this.totalDays = 30;
                    break;                    
                case 10:
                    this.month = "October";
                    this.totalDays = 31;
                    break;               
                case 11:
                    this.month = "November";
                    this.totalDays = 30;
                    break;
                case 12:
                    this.month = "December";
                    this.totalDays = 31;
                    break;                                        
                default:
                    this.totalDays = 31;
                    break;
            }
            
            //Call this function; stores the total days in a 2d array
            this.setDays();
            
        },
        setDays() {

            let dom = 1;
            let daysArray = [];
            let weekArray = [];
        
            //Loop through each week of month
            for(let w = 0; w < 6; w++) {

                //If the day of the month exceeds the total days of the month, break
                if (dom > this.totalDays) 
                    break;
                

                //Check if pointer is on the first week
                let firstWeek = false;
                
                if (w === 0) 
                    firstWeek = true;
                
                weekArray = [];
                
                //Loop though each day of the week
                for (let d = 0; d < 7; d++) {

                    //If the day of the month exceeds the total days of the month, break
                    if (dom > this.totalDays) 
                        break;

                    //If week pointer is the first week, and the day pointer is not on the starting cell
                      //Make it blank
                    if (firstWeek && d < this.startingCell) {
                        weekArray.push("");
                    }

                    //Otherwise, add the day of the month to the week array, and increment the value
                    else {
                        weekArray.push(dom);
                        dom++;
                    }
                    
                }

                //Add the week array to the days array
                daysArray.push(weekArray);

            }

            //Add the 2D array to the state after the values created
            this.daysInMonth = daysArray;

        },
        selectDay(day) {
            console.log('clicked day: ', day);
        },
        previousMonth() {

            //Store a new date based on the previous month
            let prevDate = new Date(this.date.setMonth(this.date.getMonth() - 1));
            this.targetDay = (this.currentMonth === prevDate.getMonth()) ? this.currentDay : 0;
            this.date = prevDate;
            
            //Date has been changed, so reload the values
            this.setStartingPoint();
            
        },
        nextMonth() {

            //Store a new date based on the next month
            let nextDate = new Date(this.date.setMonth(this.date.getMonth() + 1));
            this.targetDay = (this.currentMonth === nextDate.getMonth()) ? this.currentDay : 0;
            this.date = nextDate;

            //Date has been changed, so reload the values
            this.setStartingPoint();

        }
    },
    mounted() {

        //First log in today's day
        this.currentDay = this.date.getDate();
        this.currentMonth = this.date.getMonth();
        
        this.targetDay = this.currentDay;

        this.setStartingPoint();
    },
    data() {
        return {
            date: new Date(),
            month: 'Month',
            year: '20XX',
            currentDay: 0,
            targetDay: 0,
            currentMonth: 0,
            targetCell: 0,
            startingCell: 0,            
            daysInMonth: [],
            totalDays: 31,
        }
    }
}
</script>

<style scoped>
    div.main {
        width: 50%;
        margin: 0 auto;
    }

    table {
        font-size: 12px;
    }
</style>
