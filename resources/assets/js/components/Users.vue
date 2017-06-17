<template>
    <div>
<!--         <form v-on:submit.prevent="createUser" method="post">
            <div :class="{'form-group':true}">
                <input type="text" v-model="user.username" class="form-control">
            </div>            
            <div class="form-group">
                <input type="email" v-model="user.email" class="form-control">
            </div>            
            <div class="form-group">
                <button type="submit" class="btn btn-primary">Create New User</button>
            </div>
        </form> -->
        <table class="table table-hover">
            <thead>
                <tr>
                    <th>username</th>
                    <th>email</th>
                </tr>
            </thead>
            <tbody>
<!--                 <tr v-for="user in users">
                    <td>{{user.username}}</td>
                    <td>{{user.email}}</td>
                </tr> -->
                <User v-for="user in users" v-bind:user="user"></User>
            </tbody>
        </table>
    </div>
    </div>
</template>

<script>
import User from './User.vue';
    export default {
        data(){
            return{
                users: []
                // user: {
                //     'username': '',
                //     'email' : ''
                // }
            }
        },
        components: { User },
        created(){
            this.fetchUsers();
        },
        methods: {
            fetchUsers(){
                // var baseUrl = this.$http.options.root;
                this.$http.get(this.$http.options.root+'users').then(response => {
                    this.users = response.data.users;
                });
            },
            createUser(){
                this.$http.post(this.$http.options.root+'users', this.user).then(response => {
                    this.users.push(response.data.user);
                    console.log(response.data);
                });
            }
        }
    }
</script>
