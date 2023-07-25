<template>
    <header>
        <div class="header">
            <div class="header__logo">Blog</div>
            
            <nav class="header__nav">
                <ul class="header__nav__list">
                    <li><slot></slot></li>
                    <li class="header__nav__list__item">About the project</li>
                </ul>
            </nav>
        </div>
    </header>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color:  rgb(0, 128, 255);
    color: #fff;
    min-height: 3rem;
    padding: 1rem;

    &__logo {
        font-weight: 700;
    }

    &__nav {
        &__list {
            list-style: none;
            display: inline-flex;
            gap: 2rem;
            align-items: center;
        }
    }
}




</style>