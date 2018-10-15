<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User name: {{ switchName() }}</p>
        <p>User age: {{ userAge }}</p>
        <button @click="resetName">Reset name</button>
        <button @click="resetFn">Reset name</button>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    props: {
        myName: {
            type: String,
            default: 'Madyan'
        },
        resetFn: Function,
        userAge: [Number, String]
    },

    methods: {
        switchName() {
            return this.myName.split('').reverse().join('')
        },
        resetName() {
            this.myName = 'Madyan'
            this.$emit('nameWasReset', this.myName)
        }
    },

    created() {
        eventBus.$on('ageWasEdited', (age) => {
            this.userAge = age
        })
    }
}
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
