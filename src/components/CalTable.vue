<template>
    <div>
        <table class="table table-hover table-sm">
            <tr>
                <th>Sun</th>
                <th>Mon</th>
                <th>Tue</th>
                <th>Wed</th>
                <th>Thu</th>
                <th>Fri</th>
                <th>Sat</th>
            </tr>
            <tr v-for="week in daysInMonth" 
                v-bind:key="week.id" 
                v-bind:class="{ 'even': week % 2 }">
                <td v-for="day in week" 
                    v-bind:key="day.id" 
                    v-bind:class="{ 'table-info': day === targetDay }" 
                    @click="$emit('select-day', day)">
                    {{ day }}
                </td>        
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    name: 'CalTable',
    props: ['daysInMonth','targetDay'],
    data() {
        return {
            
        }
    },
    methods: {
        
    }
}
</script>

<style scoped>
    table {
        width: 100%;
    }

    th, td {
        font-size: 90%;
        padding: 5px;
    }    

    td {
        border: none;
        cursor: pointer;
    }

    td:hover {
        background: #e9e9e9;
    }

</style>