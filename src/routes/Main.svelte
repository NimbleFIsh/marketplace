<script lang="ts">
    import Header from "../components/Header.svelte";
    import Card from "../components/Card.svelte";
    import ModalWindow from "../components/ModalWindow.svelte";

    let showModalWindow = true;
    let isLogin = true;

    const tovarTest = [
    {
        'name': 'Test 1',
        'price': 100,
        'img': '/img/Logo.jpg'
    },
    {
        'name': 'Test 2',
        'price': 100,
        'img': '/img/Logo.jpg'
    },
    {
        'name': 'Test 3',
        'price': 100,
        'img': '/img/Logo.jpg'
    },
    {
        'name': 'Test 4',
        'price': 100,
        'img': '/img/Logo.jpg'
    },
    {
        'name': 'Test 5',
        'price': 100,
        'img': '/img/Logo.jpg'
    },
    {
        'name': 'Test 6',
        'price': 350,
        'img': '/img/Logo.jpg'
    }
    ];
</script>

<div id="app">
    <div class="layout_page">
        <Header/>
        <main>
            {#each tovarTest as tovar}
                <Card {tovar} />
            {/each}
        </main>
    </div>
</div>
<div class="popper__overlay">
    <div class="login__popper">
        {#if showModalWindow}
            <ModalWindow on:close="{() => showModalWindow = false}">
                <div class="window-header" slot="header">
                    <div class="window-header-item-btn">Войдите</div>
                    <div class="window-header-item">или</div>
                    <div class="window-header-item-btn">Зарегестрируйтесь</div>
                </div>
                <div>asdasdasd</div>
            </ModalWindow>
        {/if}
    </div>
</div>

<style>

    .window-header {
        height: 46px;

        display: flex;
        flex-direction: row;
        justify-content: center;
    }

    .window-header-item-btn {
        margin: 0 16px;
        padding: 8px 0;

        font-family: 'Roboto', sans-serif;
        font-weight: 400;
        font-size: 18px;
        border: 1px solid #fff;
        color: rgba(0, 0, 0, 0.85);
    }

    .window-header-item-btn {
        font-weight: 500;
        color: #639281;
        border-bottom: 1px solid #639281;
    }

    .window-header-item {
        margin: 0 16px;
        padding: 8px 0;

        font-family: 'Roboto', sans-serif;
        font-weight: 400;
        font-size: 18px;
        color: rgba(0, 0, 0, 0.3);
    }

    main {
        margin-top: 10px;
        display: flex;
        justify-content: space-between;
        padding: 0 15px;
    }

</style>