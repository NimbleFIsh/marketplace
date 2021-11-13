<script>
    import ModalWindow from "../components/ModalWindow.svelte";
    export let tovar;
    let showCardPreview = false;
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

<div class="card" on:click = {() => showCardPreview = true}>
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <div class="image-conrainer"><img src={tovar.img} alt="tovar image" /></div>
    <div class="tovar-info">
        <div class="tovar-price">{tovar.price.substring(0, tovar.price.length-3)}</div>
        <div class="tovar-name">{tovar.title}</div>
    </div>
</div>

<style>

    .card {
        box-sizing: border-box;
        width: 16%;
        padding: 8px;
        margin: 8px 0;
        border-radius: 15px;
        cursor: pointer;
    }

    .card:hover {
        box-shadow: 0 0 20px rgb(0 0 0 / 10%);
    }
   
    .tovar-name {
        color: #999;
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
        cursor: pointer;
        margin-bottom: 15px;
    }

    .card-name {

    }

    .card-body {

    }

    .card-image {

    }

    .card-description {

    }

    .card-text {

    }

    .modal {
        z-index: 2;
    }

</style>