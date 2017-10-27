<template>
    <div>
        <div class="form-group">
            <label for="firstname">First Name</label>
            <input type="text"
                   id="firstname"
                   class="form-control"
                   @input="fullname(true,$event)">
        </div>
        <div class="form-group">
            <label for="lasttname">Last Name</label>
            <input type="text"
                   id="lasttname"
                   class="form-control""
                   @input="fullname(false,$event)">
        </div>
    </div>
</template>

<script>
    export default {
        props: ['value'],

        methods: {
            fullname(isName, event){
                let fullName = '';
                if(isName){
                    fullName = event.target.value + ' ' + this.lastName
                }
                else {
                    fullName = this.firstName + ' ' + event.target.value
                }
                this.value = fullName;
                this.$emit('input', this.value) //Sends to parent as fullName
            }
        },
        computed: {
            firstName(){
                return this.value.split(' ')[0]
            },
            lastName() {
                return this.value.split(' ')[1]
            }
        }
    }

</script>

<style>

</style>