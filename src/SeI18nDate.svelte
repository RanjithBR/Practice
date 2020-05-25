<script>
  import { beforeUpdate } from 'svelte'
  export let date
  export let date1
  export let locale
  export let myDate
  beforeUpdate(() => {
    if (date !== undefined && locale !== undefined && date !== '' && locale !== '') {
      if (date.toString().length <= 13) {
        myDate = new Date(parseInt(date))
        date1 = myDate.toLocaleString(locale, { day: 'numeric', month: 'numeric', year: 'numeric' })
      } else {
        myDate = new Date(date)
        date1 = myDate.toLocaleString(locale, { day: 'numeric', month: 'numeric', year: 'numeric' })
      }
    }
  })
</script>

<svelte:options tag="se-i18n-date" accessors={true} />
{#if date1}
{date1}{/if}
