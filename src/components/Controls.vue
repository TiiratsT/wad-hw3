<template>
    <div class="controls">
        <button @click="SwitchButton('Profile')" id="profile-button" v-bind:class="{'pill active':isProfileActive, 'pill':isCoursesActive}">Profile</button>
        <button @click="SwitchButton('Course')" id="courses-button" v-bind:class="{'pill':isProfileActive, 'pill active':isCoursesActive}">Courses</button>
    </div>
</template>

<script>
    export default {
        name: "ControlsComponent",
        props: {
            switchContainer: Function,
        },
         data: () => {
            return {
                isProfileActive: true,
                isCoursesActive: false
            }   
        },
        methods: {
            SwitchButton: function(text) {
                if (text == 'Course') {
                    this.isProfileActive = false;
                    this.isCoursesActive = true;
                    
                } else if (text == 'Profile') {
                    this.isProfileActive = true;
                    this.isCoursesActive = false;
                }
                this.switchContainer(text);
            }
        }
    }
</script>



<style scoped>

</style>