<script lang="ts">
  import TaxEstimate from '$components/taxEstimate/TaxEstimate.svelte'
  import Contribution from '$components/contribution/Contribution.svelte'
  import YearSelector from '$components/yearSelector/YearSelector.svelte'
  //import {taxPaid} from '$stores/tax.store'
  // let {done, taxDone=$bindable(), taxPaid=$bindable()} = $props()
  let {done, taxDone=$bindable()} = $props()

  const contributionDone = () => {
    const el = document.getElementById('where')
    el!.style.opacity = '1'
    // el.style.transition = 'opacity 1s ease 3s'
  }

  const costDone = (ev) => {
    const el = ev.target
    el.disabled = true
    done()
  }



</script>

<svelte:head>
  <title>Home</title>
</svelte:head>
<h1>How much have you paid for wars?</h1>
<section>
  <YearSelector/><div class="separator"></div>
  <TaxEstimate done={taxDone}  /><div class="separator"></div>
  <Contribution bind:start={taxDone} done={contributionDone} />
  <button id="where" onclick={costDone}>Where did the money go?</button>
</section>

<style>
    section {
        display: flex;
        flex-direction: column;
        align-items: center;
        /*justify-content: center;*/
        
    }

    h1 {
        width: 100%;
    }

    button {
        padding: 1.5rem;
        opacity: 0;
    }
    .separator {
      margin: 1rem 0 0 0;
    }

</style>
