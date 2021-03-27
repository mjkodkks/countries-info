<script>
import { responseCountries } from "./store/store";
import { fade } from 'svelte/transition';
</script>

<ul class="display-warpper">
    {#if Array.isArray($responseCountries)}
        {#await $responseCountries}
        {:then responseCountries}
            {#each responseCountries as {name, flag, population, region, capital}, i}
                <li class="card" transition:fade>
                        <div class="img-cover">
                             <img class="card-img" src={flag} alt={'flag pic :' + name}>
                        </div>
                        <div class="info-wrapper">
                            <div class="info-name">{name}</div>
                            <div class="info"><span>population</span> : {population}</div>
                            <div class="info"><span>region</span> : {region}</div>
                            <div class="info"><span>capital</span> : {capital}</div>
                        </div>
                </li>
            {/each}
        {/await}
    {:else}
            <p transition:fade class="notfound">Not Found</p>
    {/if}

</ul>

<style>
    .display-warpper {
        display: flex;
        list-style: none;
        margin-block: 0;
        margin-inline: 0;
        padding-inline: 0;
        width: 100%;
        flex-wrap: wrap;
        gap: 24px;
        margin-top: 32px;
    }
    .card {
        width: calc(25% - 24px);
        height: 400px;
        background: #fff;
        box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
        padding: 0;
    }
    .img-cover {
        width: 100%;
        height: 45%;
        overflow: hidden;
    }
    .card-img {
        width: 100%;
        height: -webkit-fill-available;
    }
    .info-wrapper {
        padding: 32px;
        text-align: left;
    }
    .info-name {
        font-weight: bolder;
        margin-bottom: 16px;
    }
    .info span {
        font-weight: bold;
    }
    .notfound {
        width: 100%;
    }
</style>
