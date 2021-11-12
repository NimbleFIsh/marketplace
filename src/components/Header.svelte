<script lang="ts">
    import Icon from "@iconify/svelte"

</script>

<header class="header">
    <div class="header-inner">
        <div class="header-inner-logo">
            выф
        </div>
        <div class="header-inner-search">
            <div class="search-field">
                <input class="search-field-input" placeholder="Найти ферерский товар...">
                <div class="search-field-icon-holder">
                    <Icon class="search-field-icon" icon="bi:search"/>
                </div>
            </div>
        </div>
        <div class="header-inner-nav_bar">
            <nav class="nav-bar">
                <div class="nav-bar-item">Профиль</div>
                <div class="nav-bar-item">Корзина</div>
                <div class="nav-bar-item">Заказы</div>
                <div class="nav-bar-item">Избраное</div>
            </nav>
            <div class="header-inner-enter">
                <div>Войти</div>
            </div>
        </div>
    </div>
</header>

<style>

    .header {
        height: 4rem;
        width: 100%;

        border-bottom: 1px solid #333333;
    }

    .header-inner {
        width: 100%;
        height: 100%;

        padding: 0 16px;
        box-sizing: border-box;

        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }

    .header-inner-logo {
        width: 200px;
    }

    .header-inner-search {
        width: 500px;
    }

    .search-field-input {
        height: 100%;
        width: 100%;
        border: none;

        padding: 0;
        margin: 0;
    }

    .search-field-input:focus {
        outline: none;
    }

    .search-field {
        background: white;
        height: 22px;
        max-width: 100%;

        padding: 12px 14px;
        font-size: 17px;
        border: 1px solid #dddfe2;
        border-radius: 6px;

        display: flex;
        align-items: center;
        justify-content: space-between;
        user-select: none;
    }

    .search-field-icon-holder{
        width: 30px;
        height: 30px;
        cursor: pointer;

        display: flex;
        align-items: center;
        justify-content: center;
    }

    .header-inner-nav_bar, .nav-bar {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;

        font-family: 'Roboto', sans-serif;
        font-weight: 400;
        font-size: 18px;
        color: #464646;
    }

    .nav-bar {
        border-right: 1px solid #333333;
        padding: 0 12px;
    }

    .nav-bar-item {
        margin: 0 4px;
        padding: 8px;
        box-sizing: border-box;
    }

    .header-inner-enter {
        margin: 0 8px;
        padding: 0 16px;
    }

</style>