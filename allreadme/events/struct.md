# Events and Events Passing ( Component Directives)

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

### Inline events

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

# Component Directives
we can forward our own events, functions using <code>createEventDispatcher</code>

```
    <!-- Button.svelte : passing on:click event to parent component  -->
    <button on:click>
        two
    </button>
```
Example : 
```
   <script>
        import Button from '$lib/Button.svelte';
        let printConsole=()=>{
            console.log("Hello this function is passed from Child Component");
        }
   </script>

   <Button on:click={printConsole} > 

```

Passing Your own Function 
```
    <!-- BoxComponent.svelte -->
    <script>
        import { createEventDispatcher } from "svelte";

        const dispatch = createEventDispatcher();
        function sayHello() {
            dispatch("message", {
            text: "Bhide",
            });
        }
    </script>

    <button on:click={sayHello}> Click to say hello </button>

```
Example 
```
<!-- +page.svelte -->
    <script>
        import BoxComponent from "$lib/BoxComponent.svelte";

        let mint = (e) => {
            console.log("This will print Bhide in Console: ",e.detail.text);
        };
    </script>

    <BoxComponent on:message={mint} />

```



For detail infomation visit [svelte.dev](https://svelte.dev/docs/element-directives#on-eventname)

[Home](../../README.md)

[Inputs and Bindings](../Inputs/struct.md)
