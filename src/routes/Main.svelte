<script lang="ts">
    import Header from "../components/Header.svelte";
    import Card from "../components/Card.svelte";
    import ModalWindow from "../components/ModalWindow.svelte";
    import InputField from "../components/InputField.svelte";
    import PasswordField from "../components/PasswordField.svelte";
    import { testTovars } from '../testTovars.js';

    let showModalWindow = false;
    let isLogin = true;

    let Login = {
        login: '',
        password: ''
    }

    let confirmPass = ''

    let Registration = {
        email: '',
        password: '',
        name: ''
    }

    function closeModalWindow() {
        showModalWindow = false;
        isLogin = true;
    }

    if (!localStorage['cart'] || !localStorage['cart'].includes('[')) localStorage['cart'] = JSON.stringify([]);
</script>

<div id="app">
    <div class="layout_page">
        <Header on:enterBtn={() => showModalWindow = true}/>
        <main id="mainContainer">
            <div class="mainContainer-inner">
                <div class="wrapper">
                    <div class="wrapper-banner">
                        <div class="banner-container">
                            <!--                            <img class="banner-container-image" src="/img/Background.jpg" alt="banner-background"/>-->
                        </div>
                    </div>
                    <div class="wrapper-products-card">
                        <h1 class="wrapper-products-card-title"> Товары </h1>
                        <div class="wrapper-products-card-container">
                            {#each testTovars as tovar}
                                <Card {tovar}/>
                            {/each}
                        </div>
                    </div>
                    <div class="wrapper-footer">
                        <!--TODO:-->
                    </div>
                </div>
            </div>
        </main>
    </div>
</div>
<div class="popper__overlay">
    <div class="login__popper">
        {#if showModalWindow}
            <ModalWindow on:close="{closeModalWindow}">
                <div class="window-header" slot="header">
                    <div class="{isLogin ? 'window-header-item-btn-active' : 'window-header-item-btn'}"
                         on:click={() => isLogin = true}
                    >
                        Войдите
                    </div>
                    <div class="window-header-item">или</div>
                    <div class="{!isLogin ? 'window-header-item-btn-active' : 'window-header-item-btn'}"
                         on:click={() => isLogin = false}
                    >
                        Зарегестрируйтесь
                    </div>
                </div>
                <div class="window-wrapper">
                    <div class="window-wrapper-inner">
                        {#if isLogin}
                            <div class="login-fields">
                                <div class="login-fields-item">
                                    <InputField bind:bindText={Login.login} placeholderText="Email"/>
                                </div>
                                <div class="login-fields-item">
                                    <PasswordField bind:password={Login.password} placeholderText="Пароль"
                                                   newPass="false"/>
                                </div>
                            </div>
                            <div class="buttons">
                                <button class="login-button" type="button">
                                    Вход
                                </button>
                            </div>
                            <div class="void"></div>
                        {:else}
                            <div class="login-fields">
                                <div class="login-fields-item">
                                    <InputField bind:bindText={Registration.email} placeholderText="Email"/>
                                </div>
                                <div class="login-fields-item">
                                    <PasswordField bind:password={Registration.password} placeholderText="Пароль"
                                                   newPass="true"/>
                                </div>
                                <div class="login-fields-item">
                                    <PasswordField bind:password={confirmPass} placeholderText="Подтвердите пароль"
                                                   newPass="true"/>
                                </div>
                                <div class="login-fields-item">
                                    <InputField bind:bindText={Registration.name} placeholderText="Имя"/>
                                </div>
                            </div>
                            <div class="buttons">
                                <button class="login-button" type="button">
                                    Зарегестрироваться
                                </button>
                            </div>
                            <div class="void"></div>
                        {/if}
                    </div>
                </div>
            </ModalWindow>
        {/if}
    </div>
</div>

<style>

    .void {
        height: 4rem;
    }

    .window-header {
        height: 46px;

        display: flex;
        flex-direction: row;
        justify-content: center;
    }

    .window-header-item-btn, .window-header-item-btn-active {
        margin: 0 16px;
        padding: 8px 0;

        cursor: pointer;

        font-family: 'Roboto', sans-serif;
        font-weight: 400;
        font-size: 18px;
        border: 1px solid #fff;
        color: rgba(0, 0, 0, 0.85);
    }

    .window-header-item-btn-active {
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

    .window-wrapper {
        max-height: 580px;
    }

    .window-wrapper-inner {
        height: 100%;
        width: 100%;

        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
    }

    .login-fields {
        margin-top: 1.5rem;
        margin-bottom: 1.5rem;

        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .login-fields-item {
        width: 65%;

        margin: 8px;
    }

    .buttons {
        width: 100%;

        display: flex;
        align-items: center;
        justify-content: center;
    }

    .login-button {
        margin: 0;
        width: 65%;
        height: 40px;

        background: #5C8777;
        border-radius: 6px;

        color: white;
        font-family: 'Roboto', sans-serif;
        font-size: 16px;
        font-weight: 400;
    }

    #mainContainer {
        width: 100vw;
        min-height: calc(100vh - 4rem - 1px);
        height: calc(100vh - 4rem - 1px);
        overflow-y: auto;
        overflow-x: hidden;
        z-index: 1;
    }

    .mainContainer-inner {
        width: 100%;
        height: 100%;

        padding: 2rem;
        box-sizing: border-box;
    }

    .wrapper {
        height: 100%;
        width: 100%;
    }

    .wrapper-banner {
        width: 100%;
        height: 370px;

        display: flex;
        justify-content: center;
    }

    .banner-container {
        width: 100%;
        min-width: 650px;
        max-height: 370px;

        display: flex;
        justify-content: center;

        background: url("/img/Background.jpg") center bottom no-repeat;
        background-size: cover;

        border-radius: 16px;
    }

    .banner-container-image {
        display: block;
        width: 100%;
        object-fit: cover;
        border-radius: 16px;
    }

    .wrapper-products-card {
        margin-top: 10px;

        display: flex;
        flex-direction: column;
    }

    .wrapper-products-card-title {
        margin: 16px 0;
        font-size: 36px;
    }

    .wrapper-products-card-container {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        align-items: baseline;
    }

    .modal {
        z-index: 2;
    }

</style>