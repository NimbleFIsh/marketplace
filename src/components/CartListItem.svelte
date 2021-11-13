<script lang="ts">
    import Icon from "@iconify/svelte";

    export let product = {
        selected: '',
        image: '',
        title: '',
        description: '',
        price: '',
        count: ''
    };

</script>

<div class="item">
    <div class="item-checkbox">
        <input type="checkbox" bind:value={product.selected}>
    </div>
    <div class="item-image">
        <img src="{product.image}" alt="image"/>
    </div>
    <div class="item-info">
        <div class="item-info-text">
            <div class="item-info-text-title">{product.title}</div>
            <div class="item-info-text-description">{product.description}</div>
        </div>
        <div class="item-delete-btn">
            Удалить
        </div>
    </div>
    <div class="item-price">
        <span>{product.price}</span>
    </div>
    <div class="item-count">
        <div class="item-count-container">
            <button class="item-count-minus">
                <Icon icon="akar-icons:minus"/>
            </button>
            <div class="item-count-value">{product.count}</div>
            <button class="item-count-plus">
                <Icon icon="akar-icons:plus"/>
            </button>
        </div>
    </div>
</div>

<style>

    .item {
        padding: 0 1rem;

        display: flex;
        flex-direction: row;
        background: #fff;
    }

    .item-checkbox, .item-image, .item-info, .item-price, .item-count {
        display: flex;
        align-items: center;
    }

</style>