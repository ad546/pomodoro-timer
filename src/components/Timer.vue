<template>
    <div>
        <p>{{ seconds }}</p>
        <hr>
        <button @click="startTimer">Start</button>
        <button @click="stopTimer">Stop</button>
        <button @click="resetTimer">Reset</button>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            timeVar: null,
            seconds: '0'
        }
    },
    methods: {
        startTimer() {
            this.timeVar = setInterval(this.setTime, 1000);
        },
        stopTimer() {
            clearInterval(this.timeVar);
        },
        resetTimer() {
            this.seconds = 0;
        },
        setTime() {
            this.seconds++;
        }
    }
}
</script>
