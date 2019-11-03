<template>
    <div class="controls">
        <button @mouseup="switchContainer($event)" id="profile-button" class="pill active">Profile</button>
        <button @mouseup="switchContainer($event)" id="courses-button" class="pill">Courses</button>
    </div>
</template>

<script>
    export default {
        name: "ControlsComponent",
        props: {
            switchContainer: Function,
        }
    }
</script>

<style scoped>

</style>