<template>
    <div>
        <div class="container">
        <p class="location">{{ location }}</p>
        <p class="date">{{ year }}/{{ month | zeroPad }}/{{ day | zeroPad(2) }}</p>
        <div class="time">
            <p class="time-item hours">{{ hours | zeroPad(2) }}</p>
            <p class="time-item minutes">{{ minutes | zeroPad(2) }}</p>
            <p class="time-item seconds">{{ seconds | zeroPad(2) }}</p>
        </div>
        </div>
    </div>
</template>


<script>
export default {
    props: {
        location: {
            type: String,
            default: 'TOKYO'
        },
        diff: {
            type: Number,
            default: 0,
            validator(value) {
                return value <= 24
            }
        }
    },
    filters: {
        zeroPad(num, digit = 1) {
            digit = Math.max(digit, `${num}`.length)
            return (Array(digit).join("0") + num).slice(-digit)
        }
    },
    data() {
        return {
            date: new Date(),
            timerId: undefined
        }
    },
    computed: {
        year() {
            return this.date.getFullYear()
        },
        month() {
            return this.date.getMonth() + 1
        },
        day() {
            return this.date.getDate()
        },
        hours() {
            return this.date.getHours()
        },
        minutes() {
            return this.date.getMinutes()
        },
        seconds() {
            return this.date.getSeconds()
        }
    },
    mounted() {
        this.timerId = setInterval(() => this.setDate(), 1000)
        /* eslint-disable */
        console.log('started', this.timerId)
    },
    beforeDestroy() {
        /* eslint-disable */
        console.log('stopping', this.timerId)
        clearInterval(this.timerId)
    },
    methods: {
        setDate() {
            this.date = new Date()
            this.date.setHours(this.date.getHours() + this.diff)
        }
    }
}
</script>


<style scoped>
.container {
    background-color: #5f9ea0;
    padding: 2%;
}

.location {
    color: #6e5fa1;
    font-family: 'Wallpoet',sams-serif;
    font-size: 4rem;
    letter-spacing: .05em;
    lone-height: 1;
}
 
 
.date {
    text-align: right;
    color: #fff;
    font-family: 'Wallpoet', sans-serif;
    font-size: 4rem;
    letter-spacing: .1em;
    margin: .0em 0;
    line-height: 1;
}
 
 
.time {
     display: flex;
}
 
 
.time-item {
    display: flex;
    justify-content: center;
    align-items: center;
    flex: 1 1;
    height: 100px;
    position: relative;
    z-index: 1;
    padding: 0.5em;
    margin: 3px;
    color: #fff;
    font-family: 'Wallpoet', monospace;
    font-size: 5rem;
    line-height: 1;
    background-color: #6e5fa1;
    box-sizing: border-box;
}
 
 
.time-item:before {
    position: absolute;
    right: 5px;
    bottom: 1px;
    z-index: 1;
    color: #3a4a5e;
    font-family: 'Teko', sans-serif;
    font-size: 1.4rem;
    letter-spacing: .05em;
}
 
 
.hours:before {
    content: "Hours";
}
 
 
.minutes:before {
     content: "Minutes";
}
 
 
.seconds:before {
     content: "Seconds";
}
</style>