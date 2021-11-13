<script>
    export let tovar;
    let showPreviewButton = false;
</script>

<div class="card" on:mouseenter={() => showPreviewButton = true} on:mouseleave={() => showPreviewButton = false}>
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <div class="image-conrainer">
        {#if showPreviewButton}
            <div class="fastPreview">Быстрый просмотр</div>
        {/if}
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
    }

    .fastPreview {
        background-color: #fff;
        border-radius: 15px;
    }
    
    .tovar-name {
        color: #999;
    }

    .tovar-price {
        font-weight: bold;
    }

    .image-conrainer > img {
        width: 100%;
    }

</style>