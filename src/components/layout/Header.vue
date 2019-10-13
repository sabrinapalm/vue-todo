<template>
    <header class="header">
        <img
            class="profile-image"
            src="../../assets/empty-user.png"
            alt="profile"
        />
        <h1>Tasks</h1>
    </header>
</template>


<script>
export default {
    name: 'Header',
}
</script>

<style scoped>
.header {
    background: #4c278a;
    display: flex;
    align-items: center;
    color: #fff;
    text-align: center;
    padding: 10px;
    font-size: 12px;
}

.header a {
    color: #fff;
    padding-right: 5px;
}

.header h1 {
    margin-left: 10px;
}

.profile-image {
    width: 50px;
    border-radius: 100px;
}
</style>