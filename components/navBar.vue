<template>
    <div class="nav">
        <h3>Movie Finder</h3>
        <ul>
            <li>contact</li>
            <li>about</li>
        </ul>
    </div>
</template>
<style lang="scss">
.nav, .nav ul {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
}
.nav{
    margin: 0 auto;
    width: 90vw;
    color: white;
    height: 10vh;
    h3{
        font-size: calc(1rem + 1vw);
        cursor: pointer;
    }
    ul{
        width: 30%;
        max-width: 300px;
        list-style: none;
        cursor: pointer;
        li{
            text-transform: capitalize;
        }
    }
}
</style>