<script lang="ts">
    import Header from "../components/Header.svelte";
    import ModalWindow from "../components/ModalWindow.svelte";

    let showModalWindow = true; // Юра, эта переключатель для окна с логиом/регистрацией🙃
    let isLogin = true;
</script>

<div id="app">
    <div class="layout_page">
        <Header/>
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

</style>