<template>
    <div>
        <button id="add-course-button" @click="Addcourse()" class="blue-button">+</button>
        <span id="add-course" v-bind:class="{'ca':caNotActive, 'ca active':caActive}">
            <input class="input" v-model="inputCourse" type="text" placeholder="Course title" id="title">
            <input class="input" v-model="inputSemester" type="number" min="1" max="8" placeholder="Semester" id="semester">
            <input class="input" v-model="inputGrade" type="number" min="0" max="100" placeholder="Grade" id="grade">
            <button class="green-button" id="save-course" @click="add()">Save</button>
            <button class="grey-button" id="cancel-course" @click="cancel()">Cancel</button>
        </span>
    </div>
</template>

<script>
    export default {
        name: "AddCourseComponent",
        props: {
            tableContent: Array,
            user: Object,
            calculateGPA: Function
        },
         data: () => {
            return {
                caNotActive: true,
                caActive: false,
                inputCourse: "",
                inputSemester: "",
                inputGrade: ""
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
            },
            add: function()  {
                this.tableContent.push({title: this.inputCourse, semester: this.inputSemester, grade: this.inputGrade});
                this.inputCourse = "";
                this.inputSemester = "";
                this.inputGrade = "";
                this.caNotActive = true;
                this.caActive = false;
                this.calculateGPA();
            },
            cancel: function () {
                this.inputCourse = "";
                this.inputSemester = "";
                this.inputGrade = "";
                this.caNotActive = true;
                this.caActive = false;
            }
        }
    }
</script>


<style>

</style>