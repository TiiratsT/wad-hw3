<template>
    <main id="app">
        <header>
            <strong>Welcome to your dashboard!</strong>
        </header>
        <section id="container">
            <section id="main">
                <div class="content">
                    <div id="profile-container" v-bind:class="{'tab active': isActive, 'tab': isNotActive}">
                    <!-- Here were profile section -->
                    <Profile :userProps="user"/>
                    </div>
                    <div id="courses-container" v-bind:class="{'tab': isActive, 'tab active': isNotActive}">
                        <h1 class="title">Courses</h1>
                        <!-- Here were courses section -->
                        <Courses :tableContent="coursesTable" />
                        <br>
                        <br>
                        <div>
                        <!-- Here were add course section -->
                            <AddCourse :tableContent="coursesTable" :user="user" :calculateGPA="calculateGPA"/>
                        </div>
                    </div>
                </div>
                <!-- Here were Controls section -->
                <Controls :switchContainer="switchContainer"/>
            </section>
        </section>
        <footer>
            <ul class="links">
                <li>
                    <a href="https://ois2.ut.ee/" target="_blank">OIS</a>
                </li>
                <li>
                    <a href="https://courses.cs.ut.ee/" target="_blank">Courses</a>
                </li>
            </ul>
        </footer>
    </main>
</template>

<script>
    import User from "./models/User"
    import Course from "./models/Course"
    import Profile from "./components/Profile.vue"
    import Courses from "./components/Courses.vue"
    import Controls from "./components/Controls.vue"
    import AddCourse from "./components/AddCourse.vue"

    export default {
        name: 'app',
        components: {
            Profile,
            Courses,
            Controls,
            AddCourse,
        },

       
        data: () => {
            return {
                isActive: true,
                isNotActive: false,
                coursesTable: [
                    new Course("Agile software development", 1, 82),
                    new Course("System modeling", 1, 85),
                    new Course("Object-oriented programming", 2, 99),
                    new Course("Estonian language Level A2",2,65)
               ],
                user: new User("John","Doe","11/10/1990","Software Engineer",2.75)
            }   
        },

        methods: {
            switchContainer: function(text) {      
                if (text == 'Course') {
                    this.isActive = false;
                    this.isNotActive = true;
                    this.calculateGPA();
                    
                } else if (text == 'Profile') {
                    this.isActive = true;
                    this.isNotActive = false;
                }
            },

            calculateGPA: function() {
                let GPsum = 0;
                let i;
                for (i = 0; i < this.coursesTable.length; i++){
                    if (this.coursesTable[i].grade > 90){
                        GPsum += 4;
                    }
                    else if (this.coursesTable[i].grade > 80){
                        GPsum += 3;
                    }
                    else if (this.coursesTable[i].grade > 70){
                        GPsum += 2;
                    }
                    else if (this.coursesTable[i].grade > 60){
                        GPsum += 1;
                    }
                    else if (this.coursesTable[i].grade > 50){
                        GPsum += 0.5;
                    }
                }
                this.user.gpa = Math.round((GPsum / this.coursesTable.length) * 100) / 100;
            }
        },

        beforeMount() {
            this.calculateGPA();
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    .clear-fix {
        clear: both;
    }

    header {
        padding: 20px;
        background-color: #2196F3;
        color: #ffffff;
        text-align: center;
        margin-bottom: 10px;
        height: 60px;
    }

    footer {
        padding: 30px 0;
        background-color: #607D8B;
        margin-top: 10px;
        height: 100px;
        position: absolute;
        bottom: 0;
        width: 100%;
    }

    footer .links {
        display: block;
        width: 100%;
        max-width: 200px;
        margin: 0 auto;
        color: #acd7ff;
        font-size: 11px;
    }

    footer .links a {
        text-decoration: none;
        color: #acd7ff;
    }

    footer .links a:hover {
        text-decoration: underline;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }

    #profile {
        border-bottom: 1px dashed #a7a7a7;
        padding-bottom: 10px;
        margin-bottom: 10px;
    }

    #profile div:not(.clear-fix) {
        height: 190px;
        float: left;
        position: relative;
    }

    #profile .avatar {
        width: 35%;
        text-align: center;
    }

    #profile .avatar img {
        width: 180px;
    }

    #profile .info {
        width: 45%;
    }

    #profile #gpa {
        width: 20%;
    }

    #profile #gpa strong {
        position: absolute;
        width: 100%;
        height: 60px;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto auto;
        font-size: 60px;
        line-height: 60px;
        text-align: center;
    }

    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }

    .content .tab {
        display: none;
    }

    .content .tab.active {
        display: block;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }

    .blue-button {
        background-color: #2196F3;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .green-button {
        background-color: #69f378;
        color: #ffffff;
        border: none;
        padding: 10px 10px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
    }

    .ca{
        display: none;
    }

    .ca.active{
        display: inline;
    }
</style>
