<script setup>

</script>

<template>
    <header>
        <img class="logo" src="../assets/tesla_logo.svg" alt="tesla_logo">
        <nav>
            <p class="button">Vehicles</p>
            <p class="button">Energy</p>
            <p class="button">Charging</p>
            <p class="button">Discover</p>
        </nav>
        <div class="icon_box">
            <img class="icon" src="../assets/images/info.svg" alt="info.svg">
            <img class="icon" src="../assets/images/world.svg" alt="world.svg">
            <img class="icon" src="../assets/images/user.svg" alt="user.svg">
        </div>
    </header>
</template>

<style scoped>
header {
    padding-top: 1rem;
    position: fixed;
    width: 100%;
    display: flex;
    justify-content: space-between;
}

nav {
    display: flex;
    gap: 0.5rem;
}

.logo {
    padding-left: 2rem;
    height: 1.25rem;
    width: 8rem;
}

.button {
    color: rgb(15, 15, 15);
    font-weight: 600;
    border-radius: 5px;
    padding: 0.25rem 1rem;
    transition: background-color 0.5s;
    transition-delay: 0.5s;
}

.button:hover {
    cursor: pointer;
    background-color: rgba(158, 158, 158, 0.3);
    transition-delay: 0s;
}

.icon_box {
    display: flex;
    gap: 0.5rem;
    margin-right: 3rem;
}

.icon {
    width: 30px;
    height: 30px;
    opacity: 0.6;
    padding: 0.2rem;
}

.icon:hover {
    cursor: pointer;
    background: rgba(158, 158, 158, 0.3);
}
</style>