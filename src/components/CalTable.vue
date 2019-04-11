<template>
    <div>
        <table>
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
                    v-bind:class="{ 'highlight': day === targetDay }" 
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
    div {
        background: #d9d9d9;
    }

    table {
        width: 100%;
    }

    th, td {
        padding: 5px;
    }

    tr.even {
        background: #e9e9e9;
    }    

    td {
        cursor: pointer;
    }

    td:hover {
        background: #c9c9c9;
    }

    .highlight {
        background: yellow;
        font-weight: bold;
    }

</style>