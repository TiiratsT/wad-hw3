<template>
    <table id="courses">
        <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
        </thead>
       <tbody v-for="(course, index) in tableContent" :key="index"> 
            <tr>
                <td>{{ index + 1 }}</td>
                <td>{{ course.title }}</td>
                <td>{{ course.semester }}</td>
                <td>{{ course.grade }}</td>
            </tr>
        </tbody> 
    </table>
</template>

<script>
    export default {
        name: "CoursesComponent",
        props: {
            tableContent: Array
        }
    }
</script>

<style scoped>

</style>