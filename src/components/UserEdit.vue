<template>
    <div class="component">
        <h3>You may edit the User here</h3>
        <p>Edit me!</p>
        <p>User age: {{ userAge }}</p>
        <button @click="editAge">Edit age</button>
        <!-- <button @click="editAgeFn">Edit age</button> -->
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    props: {
        userAge: [Number, String],
        // editAgeFn: Function
    },

    methods: {
        editAge() {
            this.userAge = 20
            // this.$emit('ageWasEdited', this.userAge)
            // eventBus.$emit('ageWasEdited', this.userAge)
            eventBus.changeAge(this.userAge)
        }
    }
}
</script>

<style scoped>
    div {
        background-color: lightgreen;
    }
</style>
