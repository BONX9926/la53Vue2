<template>
    <tr>
        <td>{{user.username}}</td>
        <td>{{user.email}}</td>
    </tr>
</template>

<script>
    export default {
        props: ['user']
    }
</script>
