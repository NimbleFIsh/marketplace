<script>
    export let tovar;
    let showCardPreview = false;
</script>

<div class="card" on:click = {() => showCardPreview = true}>
    <!-- svelte-ignore a11y-img-redundant-alt -->
    {#if showCardPreview}
        <div class="cardModal">
            <div class="cardClose"></div>
            <div>
                
            </div>
        </div>
    {/if}
    <div class="image-conrainer">
        <img src={tovar.img} alt="tovar image" />
    </div>
    <div class="tovar-info">
        <div class="tovar-price">{tovar.price} ₽</div>
        <div class="tovar-name">{tovar.name}</div>
    </div>
</div>

<style>

    .card {
        width: 16%;
        padding: 8px;
        border-radius: 15px;
        cursor: pointer;
    }

    .card:hover {
        box-shadow: 0 0 20px rgb(0 0 0 / 10%);
    }

    .fastPreview {
        position: absolute;
        background-color: #fff;
        border-radius: 15px;
        padding: 8px;
        box-shadow: 0px 0px 4px 0px lightgray;
        cursor: pointer;
    }
    
    .tovar-name {
        color: #999;
    }

    .tovar-price {
        font-weight: bold;
    }

    .image-conrainer {
        position: relative;
        display: flex;
        justify-content: center;
    }

    .image-conrainer > img {
        width: 100%;
    }

</style>