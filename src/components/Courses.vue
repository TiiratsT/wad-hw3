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
       <!--<tbody v-for="()"> 
            <tr>
                <td></td>
                <td>Agile software development</td>
                <td>1</td>
                <td>82</td>
            </tr>
        </tbody> -->
    </table>
</template>

<script>
    export default {
        name: "CoursesComponent",
        props: {
            tableContent: Array,
            // Add addCourse: Function
        }
    }
</script>