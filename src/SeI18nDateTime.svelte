<script>
  import { beforeUpdate } from 'svelte'
  export let datetime
  export let datetimevalue
  export let locale
  export let myDate
  beforeUpdate(() => {
    if (datetime !== undefined && locale !== undefined && datetime !== '' && locale !== '') {
      var options = {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric',
        hour: '2-digit',
        minute: '2-digit',
      }
      myDate = new Date(datetime)
      datetimevalue = myDate.toLocaleDateString(locale, options);
    }
  })
</script>

<svelte:options tag="se-i18n-datetime" accessors={true} />
{#if datetimevalue}{datetimevalue}{/if}
