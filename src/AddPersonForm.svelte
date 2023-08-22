<script>

  import { createEventDispatcher } from 'svelte';
  let dispatch = createEventDispatcher();


  let name;
  let beltColour;
  let age;
 
  const handleSubmit = () => {
    const person = {
      name,
      beltColour,
      age, 
      id : Math.random()
    };
    dispatch('addPerson', person);
  };
  let skills = [];
  

  

</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name}>
  <input type="number" placeholder="age" bind:value={age}>
  <!-- svelte-ignore a11y-label-has-associated-control -->
  <label> Skills: </label>
  

  <input type="checkbox" bind:group={skills} value = "fighting">fighting <br>
  <input type="checkbox" bind:group={skills} value = "sneaking">sneaking <br>
  <input type="checkbox" bind:group={skills} value = "running">running <br>
  <!-- svelte-ignore a11y-label-has-associated-control -->
  <label> Belt color:</label>
  <select bind:value={beltColour}>
    <option value="black"> black</option>
    <option value="orange"> orange</option>
    <option value="white"> white</option>
  </select>
  <button>Add person</button>

</form>

<style>

</style>