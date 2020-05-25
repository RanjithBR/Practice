<script>
  import { onMount, afterUpdate, beforeUpdate } from 'svelte'
  export let style
  export let locale
  export let currency
  export let number
  export let displayedNumber
  beforeUpdate(() => {
    if (currency !== undefined && number !== undefined && locale !== undefined && currency !== '' && number !== '' && locale !== '') {
      displayedNumber = Intl.NumberFormat(locale, {
        style: 'currency',
        currency: currency,
      }).format(Number(number))
    }
  })
</script>

<svelte:options tag="se-i18n-currencynumber" accessors={true} />
{#if displayedNumber}{displayedNumber}{/if}
