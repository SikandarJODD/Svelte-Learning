# Events

Use the <code>on:</code> directive to listen to DOM events.

```
    on:eventname={handler}
```

```bash
    <script>
        let count = 0;

        /** @param {MouseEvent} event */
        function handleClick(event) {
            count += 1;
        }
    </script>

    <button on:click={handleClick}>
        scount: {count}
    </button>
```

#### Inline events

```bash
    <button on:click={() => (count += 1)}>
        count: {count}
    </button>
```

### Modifiers

Add modifiers to DOM events with the <code>|</code> character.

PreventDefault

```bash
    <button on:submit|preventDefault={handleSubmit}>
        <!-- the `submit` event's default is prevented,
     so the page won't reload -->
        Submit
    </button>
```

Once : it will work at first click, then it will stop working

```bash
    <button on:click|once={() => (count += 1)}>
        count: {count}
    </button>
```

It's possible to have multiple event listeners for the same event:

```bash
    <script>
        let counter = 0;
        function increment() {
            counter = counter + 1;
        }

        /** @param {MouseEvent} event */
        function track(event) {
            trackEvent(event);
        }
    </script>

    <button on:click={increment} on:click={track}>
        Click me!
    </button>
```

For detail infomation visit [svelte.dev](https://svelte.dev/docs/element-directives#on-eventname)

[Home](../README.md)

[Inputs and Bindings](/Inputs/struct.md)
