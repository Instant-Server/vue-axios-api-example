<template>
<div>
    <h1>User List</h1>
    <ul>
    <li v-for="user in users" :key="user.id">{{ user.username }}</li>
    </ul>
</div>
</template>

<script>
import axios from "axios";

export default {
    data() {
        return {
            users: [],
        };
    },
    mounted() {
        axios.get("http://localhost:8911/getJsonEndpointResult?id=b9c567bf-7e79-482d-bb20-241d4b2035c1")
        .then((response) => {
            this.users = response.data.data.users;
        })
        .catch((error) => {
            console.error("Error fetching users:", error);
        });
    },
};
</script>