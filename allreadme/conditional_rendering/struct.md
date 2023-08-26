# Logical Blocks

- {#if expression}...{/if}
- {#if expression}...{:else if expression}...{/if}
- {#if expression}...{:else }...{/if}
- {#each}....{/each} - for Loop

### {#if expression}

```
    <script>
        let number = 10;
    </script>
    <div>
        {#if number%2==0}
            <!-- this means if number is even -->
            <h1> Even Number </h1>
        {/if}
    </div>
```

### {#if expression}....{:else if expression}...{if}

```
    <script>
        let number = 10;
    </script>
    <div>
        {#if number<5}
            <h1> Number is Less than 5</h1>
        {:else if number>=10}
            <h1> Number is Greater equal to 10</h1>
        {/if}
    </div>
```

### {#if expression}....{:else}...{if}

```
    <script>
        let number = 10;
    </script>
    <div>
        {#if number<5}
            <h1> Number is Less than 5</h1>
        {:else }
            <h1> Number is Greater equal to 5</h1>
        {/if}
    </div>
```

### Fop Loop : {#each}

iterating over list of values can be done with each block

```
    <script>
        let friends=["Aditya","Saloni","Pretty","John"];
    </script>
    <ul>
        {#each friends as name}
            <li>{name}</li>
        {/each}
    </ul>
```

### Fop Loop : array of Objects

iterating over list of values can be done with each block

```
    <script>
    let students = [
        {
        name: "Aditya",
        age: 20,
        game: "Cricket",
        },
        {
        name: "Saloni",
        age: 21,
        game: "Candy Crush",
        },
        {
        name: "Pretty",
        age: 20,
        game: "Ludo",
        },
    ];
</script>

    <ul>
        {#each students as item, index}
            <!-- Index starts with 0 -->
            <li>{index + 1} Name : {item.name}, age: {item.age}, I like to play {item.game}</li>
        {/each}
    </ul>

```

### Fop Loop : Each with Else
An each block can also have an <code>{:else}</code> clause, which is rendered if the list is empty.

iterating over list of values can be done with each block

```
    <script>
     /**
     * @type {any[]}
     */
        let tasks = []; // Empty Array
    </script>

    <ul>
        {#each tasks as item}
            <!-- Index starts with 0 -->
            <p>{item}</p>
            {:else}
            <p>No tasks today</p>
        {/each}
    </ul>
```
For detailed Information visit [svelte.dev](https://svelte.dev/docs/logic-blocks) 

[Home](../../README.md)
[Inputs](../Inputs/struct.md)