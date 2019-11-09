<template>
    <div>
        <div id="profile">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{ userProps.firstname + " " + userProps.lastname}}</li>
                    <li id="birthdate">{{ userProps.birthdate }}</li>
                    <li id="faculty">{{ userProps.faculty }}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{ userProps.gpa }}</strong>
             </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ProfileComponent",
        props: {
            userProps: Object
        }
    }
</script>

<style scoped>

</style>