<script>
  import { beforeUpdate } from 'svelte'
  export let locale
  export let displayedCurrency
  export let displayedCurrencyvalue
  const cur = {
    EUR: '€',
    GBP: '£',
    USD: '$',
    JPY: '¥',
    SAR: 'ر.س',
    FJD: 'FJ$',
    DEM: '€',
    INR: '₹',
    BRL: 'R$',
    CAD: 'C$',
  }

  const lang_cur_lookup = {
    JPY: 'ja-JP',
    USD: 'en-US',
    JPY: 'ja-JP',
    DEM: 'de-DE',
    INR: 'en-IN',
    FJD: 'fi-FI',
    SAR: 'ar-SA',
    BRL: 'pt-BR',
    CAD: 'fr-CA',
    EUR: 'fr-FR',
  }
  beforeUpdate(() => {
    console.log(locale)
    if (locale !== undefined && locale !== '') {
      displayedCurrency = cur[Object.keys(lang_cur_lookup).find(key => lang_cur_lookup[key] === locale)]
      displayedCurrencyvalue = Object.keys(lang_cur_lookup).find(key => lang_cur_lookup[key] === locale)
    }
  })
</script>

<svelte:options tag="se-i18n-currency" accessors={true} />
{#if displayedCurrency}{displayedCurrency}{/if}
