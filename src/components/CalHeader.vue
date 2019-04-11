<template>
    <div class="header-box">
        <div class="button-box">
            <button class="btn" @click="$emit('prev-month')">
                <i class="fas fa-angle-left"></i>
            </button>
        </div>
        <div class="title-box">
            <span>{{ month }}</span>
            <span>{{ year }}</span>
        </div>
        <div class="button-box">
            <button class="btn" @click="$emit('next-month')">
                <i class="fas fa-angle-right"></i>
            </button>
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
        background: #e9e9e9;
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
        font-size: 150%;
        padding: 0 5px;
    }
</style>