<script lang="ts">

    import CartListItem from "../components/CartListItem.svelte";

    let productsCart = JSON.parse(localStorage['cart'])
    let sum = 0;
    productsCart.forEach(e => sum += e.price)

    let regions = [];
    let selected;

</script>

<main id="mainContainer">
    <div class="mainContainer-inner">
        <div class="wrapper">
            <div class="wrapper-container">
                <div class="wrapper-container-title">
                    <h1 class="title">Корзина</h1>
                </div>
                <div class="wrapper-container-card">
                    <div class="products-card">
                        <div class="card-selector">
                            <input type="checkbox">
                            <div class="selector-deleteAll">Удалить выбраные</div>
                        </div>
                        <div class="card-order-delivery">
                            <div class="card-order-delivery-inner">
                                <div class="order-delivery-title">
                                    Доставка
                                </div>
                                <div class="order-delivery-price">
                                    <select class="delivery-region" bind:value={selected}>
                                        {#each regions as region}
                                            <option value={region}>
                                                {region.name}
                                            </option>
                                        {/each}
                                    </select>
                                    <div class="delivery-region-price">
                                        {(selected ? selected.price : 0)}
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="card-list">
                            <CartListItem/>
                        </div>
                    </div>
                    <div class="products-order">
                        <div class="products-order-container">
                            <div class="make-order">
                                <button type="button">Перейти к оформлению</button>
                            </div>
                            <div class="order-info">
                                <div class="order-info-title">
                                    <div class="title-text">Ваша корзина</div>
                                    <div class="order-count">{productsCart.length} товара</div>
                                </div>
                                <div class="order-cart-price">
                                    <div class="cart-title">Товары ({productsCart.length})</div>
                                    <div class="cart-price">{sum}</div>
                                </div>
                                <div class="order-delivery-price">
                                    <div class="delivery-title">Доставка</div>
                                    <div class="delivery-price">0</div>
                                </div>
                                <div class="order-info-summary">
                                    <div class="summary-title">Общая стоимость</div>
                                    <div class="summary-price">{sum}</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</main>

<style>

    button {
        margin: 0;
    }

    #mainContainer {
        width: 100vw;
        min-height: calc(100vh - 4rem - 1px);
        height: calc(100vh - 4rem - 1px);
        overflow-y: auto;
        overflow-x: hidden;
        background: #f7f8f9;
        z-index: 1;
    }

    .mainContainer-inner {
        width: 100%;
        max-width: 1472px;
        height: 100%;

        padding: 2rem;
        margin: 0 auto 0;
        box-sizing: border-box;
    }

    .wrapper {
        height: 100%;
        width: 100%;
    }

    .wrapper-container {
        display: flex;
        flex-direction: column;
    }

    .wrapper-container-card {
        width: 100%;
        min-height: 372px;
        height: 372px;

        display: flex;
        flex-direction: row;
    }

    .products-card {
        width: 60%;
        flex-grow: 1;
    }

    .products-order {
        height: calc(100% - 24px);
        width: 30%;

        margin: 0 0 24px 24px;

        flex-grow: 1;
        background: white;
    }

    .products-order-container {
        height: 100%;
        width: 100%;

        display: flex;
        flex-direction: column;
    }

    .make-order {
        height: 35%;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 24px;
        box-sizing: border-box;
    }

    .make-order button {
        width: 80%;
        height: 56px;
        background: #10ad44;
        border-radius: 6px;

        font-family: 'Roboto', sans-serif;
        font-weight: 700;
        font-size: 16px;
        color: #fff;
    }

    .order-info {
        height: 65%;
        width: 100%;

        padding: 24px;
        box-sizing: border-box;
        border-top: 1px solid rgba(0, 26, 52, .16);

        display: flex;
        flex-direction: column;
        justify-content: space-between;

        font-family: 'Roboto', sans-serif;
        color: #001a34;
    }

    .order-info-title, .order-cart-price, .order-delivery-price, .order-info-summary {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
    }

    .order-info-title {
        padding-bottom: 16px;
    }

    .title-text {
        font-size: 20px;
        font-weight: 700;
        line-height: 1.4em;
    }

    .order-count {

        font-size: 14px;
        line-height: 1.29em;
        text-align: end;
    }

    .cart-title {
        font-size: 14px;
        justify-content: space-between;
        line-height: 18px;
        margin-bottom: 12px;
    }

    .cart-price {
        font-weight: 700;
    }

    .delivery-title {
        font-size: 14px;
        justify-content: space-between;
        line-height: 18px;
        margin-bottom: 12px;
    }

    .delivery-price {
        font-weight: 700;
    }

    .summary-title, .summary-price {
        font-size: 20px;
        font-weight: 700;
        line-height: 1.4em;
    }

    .order-cart-price, .order-delivery-price {
        margin-bottom: 8px;
    }

    .order-info-summary {
        margin-top: 16px;
        padding-top: 16px;

        border-top: 1px solid rgba(0, 26, 52, .16);
    }

</style>