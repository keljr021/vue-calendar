<template>
    <div class="header-box">
        <div class="button-box">
            <button @click="$emit('prev-month')">&lt;</button>
        </div>
        <div class="title-box">
            <span>{{ month }}</span>
            <span>{{ year }}</span>
        </div>
        <div class="button-box">
            <button  @click="$emit('next-month')">&gt;</button>
        </div>        
    </div>
</template>

<script>
export default {
    name: 'CalHeader',
    props: ['month','year']
}
</script>

<style scoped>
    div.header-box {
        background: #ccc;
        padding: 15px;
        display: flex;
    }

    .button-box {
        flex: 1;
    }

    .title-box {
        flex: 2;
    }

    span {
        padding: 0 5px;
    }
</style>