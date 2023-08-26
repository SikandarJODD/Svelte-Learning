# Inputs

Data ordinarily flows down, from parent to child. The <code>bind:</code> directive allows data to flow the other way, from child to parent. Most bindings are specific to particular elements.

```
    <input bind:value={name} />
    <textarea bind:value={text} />

    <input type="checkbox" bind:checked={yes} />
```

Using shorthand :

```
    <input bind:value />
```

### Input for file

```
    <label for="avatar">Upload a picture:</label>
    <input accept="image/png, image/jpeg" bind:files id="avatar" name="avatar" type="file" />
```

### Prefer using <code>on</code> after bindings

```
    <script>
        let value = 'Hello World';
    </script>

    <input
    on:input={() => console.log('Old value:', value)}
    bind:value
    on:input={() => console.log('New value:', value)}
    />
```

### Select specific element

```
    <script>
    let selected = "a";
    </script>
    // for selecting multipy items put multiple inside <select multiple >

    <select bind:value={selected}>
        <option selected value="a">a</option>
        <option value="b">b</option>
        <option value="c">c</option>
    </select>
    <h1>The selected element is {selected}</h1>
```

### bind:group

```
<script>
  let tortilla = "Plain";

  /** @type {Array<string>} */
  let fillings = [];
</script>

    <!-- grouped radio inputs are mutually exclusive -->
    <input type="radio" bind:group={tortilla} value="Plain" />
    <input type="radio" bind:group={tortilla} value="Whole wheat" />
    <input type="radio" bind:group={tortilla} value="Spinach" />

    <!-- grouped checkbox inputs populate an array -->
    <input type="checkbox" bind:group={fillings} value="Rice" />
    <input type="checkbox" bind:group={fillings} value="Beans" />
    <input type="checkbox" bind:group={fillings} value="Cheese" />
    <input type="checkbox" bind:group={fillings} value="Guac (extra)" />


    <!--  Prints the Selected value based on Radio.......Plain, whole wheat, spinach.. -->
    <h1>You have selected a {tortilla}</h1>
    
    <!--  prints the selected items based on checkboxes -->
    {#each fillings as filling}
        <p>{filling}</p>
        {:else}
        <p>No filling</p>
    {/each}
```
