<script lang="ts">
  import FiatRow from './FiatRow.svelte';
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  import { Fiat } from '../constants';

  export let active: boolean;

  const onCancel = () => {
    active = false;
  };

  const onSelect = (fiat: string) => {
    dispatch('selected', { fiat });
    active = false;
  };
</script>

<div class="modal {active && 'is-active'}">
  <div class="modal-background" on:click={onCancel} />
  <div class="modal-content box has-background-black">
    <div class="columns">
      <div class="column is-half is-offset-one-quarter">
        <h1 class="title has-text-white">Select an asset</h1>
        <ul class="mt-6">
          <li class="mt-3">
            <!-- svelte-ignore a11y-missing-attribute -->
            <a on:click={() => onSelect(Fiat.CAD)}>
              <FiatRow name={Fiat.CAD} />
            </a>
          </li>
          <li class="mt-3">
            <!-- svelte-ignore a11y-missing-attribute -->
            <a on:click={() => onSelect(Fiat.EUR)}>
              <FiatRow name={Fiat.EUR} />
            </a>
          </li>
          <li class="mt-3">
            <!-- svelte-ignore a11y-missing-attribute -->
            <a on:click={() => onSelect(Fiat.USD)}>
              <FiatRow name={Fiat.USD} />
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</div>

<style>
  a {
    color: white;
  }
</style>
