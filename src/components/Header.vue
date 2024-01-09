<script setup>

</script>

<template>
    <header>
        <img class="logo" src="../assets/tesla_logo.svg" alt="tesla_logo">
        <nav>
            <p class="button button_desktop">Vehicles</p>
            <p class="button button_desktop">Energy</p>
            <p class="button button_desktop">Charging</p>
            <p class="button button_desktop">Discover</p>
            <p class="button button_mobile">Menu</p>
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

.button_desktop {
    display: block;
}

.button_mobile {
    display: none;
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

@media (width < 768px) {

    .button {
        background-color: rgba(158, 158, 158, 0.2);
        margin-top: -0.2rem;
        margin-right: 0.5rem;

    }

    .button_desktop {
        display: none;
    }

    .button_mobile {
        display: block;
    }

    .icon_box {
        display: none;
    }
}
</style>