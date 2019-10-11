<template>
    <header class="header">
        <img
            class="profile-image"
            src="https://sabrinapalm.github.io/images/profile-image-secondary.PNG"
            alt="profile"
        />
        <h1>My todo</h1>
    </header>
</template>


<script>
export default {
    name: 'Header',
}
</script>

<style scoped>
.header {
    background: #64b2cd;
    color: #fff;
    text-align: center;
    padding: 10px;
}

.header a {
    color: #fff;
    padding-right: 5px;
}

.profile-image {
    width: 80px;
    border: 2px solid #fff;
    border-radius: 100px;
}
</style>