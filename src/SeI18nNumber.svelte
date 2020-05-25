<script>
  import { beforeUpdate, afterUpdate } from 'svelte'
  export let locale
  export let number
  let convertednumber
  afterUpdate(() => {
    if (number !== undefined && locale !== undefined && number !== '' && locale !== '' ) {
      convertednumber = new Number(number).toLocaleString(locale)
    }
  })
</script>

<svelte:options tag="se-i18n-number" accessors={true} />
{#if convertednumber}{convertednumber}{/if}
