<template>
    <div>
        <p>{{ hours }} : {{ minutes }} : {{ seconds }}</p>
        <hr>
        <button @click="startTimer">Start</button>
        <button @click="stopTimer">Stop</button>
        <button @click="resetTimer">Reset</button>
        <button @click="pomodoroTime">Pomodoro Timer</button>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            timeVar: null,
            total: '3595',
            minutes: '59',
            hours: '0',
            seconds: '55'
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
            this.seconds = '00';
            this.minutes = '00';
            this.hours = '0';
            this.total = 0;
        },
        display(){
            this.minutes = Math.floor(this.total / 60);
            this.seconds = this.total - this.minutes * 60;
            this.hours = Math.floor(this.total / 3600);
            (this.seconds < 10 ? this.seconds = ('0' + this.seconds) : this.seconds = this.seconds);
            (this.minutes > 59 ? this.minutes = 0 : this.minutes = this.minutes);
            (this.minutes < 10 ? this.minutes = ('0' + this.minutes) : this.minutes = this.minutes);
        },
        setTime() {
            this.total++;
            this.display();
        },
        pomodoroTime(){
            this.resetTimer();
            this.total = 5;
            this.display();
            this.timeVar = setInterval(this.reverseSetTime, 1000);
        },
        reverseSetTime() {
            this.total--;
            this.display();
            if (this.total === 0){
                alert("Break Time!");
                this.stopTimer();
            }
            
        }
    }
}
</script>
