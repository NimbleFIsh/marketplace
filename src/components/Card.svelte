<script>
    import ModalWindow from "../components/ModalWindow.svelte";
    export let tovar;
    let showCardPreview = false;
    let purchase = false;

    function addToPurchase(e) { // Сергей ~ прочитай - поймёшь
        const ls = localStorage['cart'] ? JSON.parse(localStorage['cart']) : []; // Чтение хранилища, если есть - читать, если нет - создать массив
        ls.push(e.target.parentNode.parentNode.id); // Добавление id товара в массив
        localStorage['cart'] = JSON.stringify(ls); // Перевод в строку и записс в хранилище
    }

</script>

{#if showCardPreview}
    <ModalWindow on:close="{() => showCardPreview = false}">
        <div class="card-name" slot="header">{tovar.title}</div>
        <div class="card-body">
            <!-- svelte-ignore a11y-img-redundant-alt -->
            <div class="card-image"><img src={tovar.img} alt="tovar image" /></div>
            <div class="card-description">
                <div class="addToCartButton">Добавить в корзину</div>
                <div class="card-text">{tovar.description}</div>
            </div>
        </div>
    </ModalWindow>
{/if}

<div id={tovar.id} class="card" on:mouseenter={() => purchase = true} on:mouseleave={() => purchase = false}>
    <div on:click = {() => showCardPreview = true}>
        <!-- svelte-ignore a11y-img-redundant-alt -->
        <div class="image-conrainer"><img src={tovar.img} alt="tovar image" /></div>
        <div class="tovar-info">
            <div class="tovar-price">{tovar.price.substring(0, tovar.price.length-3)}</div>
            <div class="tovar-name">{tovar.title}</div>
        </div>
    </div>
    {#if purchase}
        <div class="purchase-container"><div class="purchase" on:click={addToPurchase}>Добавить в корзину</div></div>
    {/if}
</div>

<style>

    .card {
        box-sizing: border-box;
        position: relative;
        width: 16%;
        padding: 15px;
        margin: 8px 0;
        border-radius: 15px;
        cursor: pointer;
    }

    .card:hover {
        box-shadow: 0 0 20px rgb(0 0 0 / 10%);
    }
   
    .tovar-name {
        color: #999;
        margin-bottom: 8px;
    }

    .tovar-price {
        font-size: 18px;
        font-weight: bold;
        margin-bottom: 5px;
    }

    .image-conrainer {
        position: relative;
        display: flex;
        justify-content: center;
        margin-bottom: 5px;
    }

    .image-conrainer > img {
        width: 100%;
        z-index: 1;
        border-radius: 5px;
    }

    .addToCartButton {
        margin-top: 15px;
        cursor: pointer;
        margin-bottom: 15px;
    }

    .card-name {
        margin-bottom: 10px;
    }

    .card-body {
        display: flex;
    }

    .card-image {
        width: 60%;
        margin-right: 15px;
    }

    .card-image > img {
        width: 100%;
    }

    .card-description {
        width: 30%;
    }

    .purchase-container {
        position: absolute;
        width: 100%;
        margin-top: 5px;
        left: 0;
        display: flex;
        justify-content: center;
        bottom: -15px;
        align-items: end;
        padding: 0 0 5px 0;
        background-color: #fff;
        border-radius: 0 0 5px 5px;
        box-shadow: 0px 5px 20px rgb(0 0 0 / 10%);
    }

</style>