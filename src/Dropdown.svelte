<script>
  export let placeholder = "옵션을 선택하세요.";
  export let width = "320px";
  export let options = [
    { id: 1, value: "옵션1" },
    { id: 2, value: "옵션1" },
    { id: 3, value: "옵션1" },
  ];

  let opened = false;
  export let id = null;
  export let value = null;

  function selectOption(option) {
    id = option.id;
    value = option.value;
    opened = false;
  }
</script>

<button
  class="box"
  class:selected={value}
  style="width: {width}"
  on:click={() => (opened = !opened)}
>
  {value ?? placeholder}
</button>
<div class="items-box">
  <div
    class="items"
    style="width: {width}; display: {opened ? 'block' : 'none'}"
  >
    {#each options as option (option.id)}
      <button
        class="item"
        style="width: {width}"
        on:click={() => selectOption(option)}
      >
        {option.value}
      </button>
    {/each}
  </div>
</div>

<style>
  button {
    font-size: 18px;
    display: flex;
    align-items: center;
    padding: 14px;
    background-color: white;
    border: none;
    color: #676778;
  }
  .box {
    border: 1px solid lightgray;
    border-radius: 10px;
    color: rgb(146, 146, 146);
    margin-bottom: 10px;
  }
  .box.selected {
    color: #676778;
  }

  .items-box {
    position: relative;
  }
  .items {
    position: absolute;
    border: 1px solid lightgray;
    border-radius: 10px;
    overflow: hidden;
  }
</style>
