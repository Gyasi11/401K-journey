<template>
<div class="flex-container">
    <div class="row">
        <div class="flex-item">
            <Journey />
        </div>
    </div>
</div>
</template>

<script>
import Journey from './components/Journey.vue'

export default {
    name: 'App',
    components: {
        Journey
    }
}
</script>

<style>
html,
body {
    height: 100%;
    background: #fafafa;
}

body {
    margin: 0;
}

.flex-container {
    height: 100%;
    padding: 0;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: center;
}

.row {
    width: auto;
    border: 1px solid blue;
}

.flex-item {
    padding: 5px;
    width: auto;
    height: auto;
    margin: 10px;
    line-height: 20px;
    font-weight: bold;
    font-size: 2em;
    text-align: center;
}
</style>
