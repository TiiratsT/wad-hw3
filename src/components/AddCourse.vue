<template>
    <div>
        <button id="add-course-button" @click="Addcourse()" class="blue-button">+</button>
        <span id="add-course" v-bind:class="{'ca':caNotActive, 'ca active':caActive}">
            <input class="input" type="text" placeholder="Course title" id="title">
            <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
            <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
            <button class="green-button" id="save-course">Save</button>
            <button class="grey-button" id="cancel-course">Cancel</button>
        </span>
    </div>
</template>

<script>
    export default {
        name: "AddcourseComponent",
        props: {
            
        },
         data: () => {
            return {
                caNotActive: true,
                caActive: false
            }   
        },
        methods: {
            Addcourse: function() {
                if (this.caNotActive) {
                    this.caNotActive = false;
                    this.caActive = true;
                } else {
                    this.caNotActive = true;
                    this.caActive = false;
                }
            }
        }
    }
</script>


<style>

</style>