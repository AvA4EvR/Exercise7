<template>
    <div class="container">
        <form>
            <div class="row" v-if="!isSubmitted">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <!-- Part 1 5 Points-->
                    <h1>Signup Form!</h1>
                   <appName v-model="fullName"></appName> <!--Received from child as "value"-->
                    <div class="form-group">
                        <label for="mail">Mail</label>
                        <input
                                type="text"
                                id="mail"
                                class="form-control"
                                :value="userData.mail"
                                @input="userData.mail = $event.target.value">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                                type="password"
                                id="password"
                                class="form-control"
                                v-model.trim.lazy="userData.password">

                    </div>

                    <div class="form-group">

                            <label for="yes">Store Data?
                                <input
                                        type="radio"
                                        id="yes"
                                        value="Yes"
                                        v-model="storeData"> Yes
                            </label>
                            <label for="no">
                                <input
                                        type="radio"
                                        id="no"
                                        value="No"
                                        v-model="storeData"> No
                            </label>

                    </div>

                    <div class="row">
                        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                            <button
                                    class="btn btn-primary"
                                    @click.prevent="submitted">Submit
                            </button>
                        </div>
                    </div>
                    <!-- Create a Signup Form where you retrieve the following Information -->
                    <!-- Full Name (First Name + Last Name) -->
                    <!-- Mail -->
                    <!-- Password -->
                    <!-- Store Data? Yes/No -->

                    <!-- Part 2 5 Points -->
                    <!-- Only display the Form if it has NOT been submitted -->
                    <!-- Display the Data Summary ONCE the Form HAS been submitted -->

                    <!-- Part 3 5 Points -->
                    <!-- Edit the Example from above and create a custom "Full Name" Control -->
                    <!-- which still holds the First Name and Last Name Input Field -->
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="isSubmitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>Your Data</h4>
                    </div>
                    <div class="panel-body">
                        <p>Full Name: {{fullName}}</p>
                        <p>Mail: {{userData.mail}}</p>
                        <p>Password: {{userData.password}}</p>
                        <p>Store in Database?: {{storeData}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Name from './Name.vue'
    export default {

        data() {
            return {
                userData: {
                    mail: '',
                    password: '',

                },
                storeData: 'Yes',
                fullName: '',
                isSubmitted: false,
            }
        },

        components: {
          appName: Name
        },

        methods: {
            submitted(){
                this.isSubmitted = true;
            },
        }
    }
</script>

<style>
</style>
