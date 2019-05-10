<template>
    <div>
        <h1>Create a movie</h1>
         <input type="text" placeholder="itle"><br><br>
        <input type="password" placeholder="director"><br><br>
        <button @click="connect()">Create a movie</button>
    </div>
</template>

<script>
export default {
    name: 'newMovie'
}
</script>

