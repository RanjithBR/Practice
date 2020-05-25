<script>
  import { beforeUpdate } from 'svelte'
  import PhoneNumberJson from 'google-libphonenumber'
  export let defnumber, natnumber, intlnumbet, phonenumber, locale, local
  beforeUpdate(() => {
    if (locale !== undefined && phonenumber !== undefined && locale !== '' && phonenumber !== '') {
      const phoneUtil = PhoneNumberJson.PhoneNumberUtil.getInstance()
      local = locale.slice(3, 5);
      defnumber = phoneUtil.parseAndKeepRawInput(phonenumber, local);
      natnumber = phoneUtil.format(defnumber, PhoneNumberJson.PhoneNumberFormat.NATIONAL);
      intlnumbet = phoneUtil.format(defnumber, PhoneNumberJson.PhoneNumberFormat.INTERNATIONAL);
    }
  })
</script>

<svelte:options tag="se-i18n-phonenumber" accessors={true} />
{#if intlnumbet}
{intlnumbet}
{/if}
