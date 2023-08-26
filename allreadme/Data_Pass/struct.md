# Passing Data

- using props
- slots

### Passing Data using Props

<code> export </code> is used to pass data.

```
<!-- Simple Name Component  Name.svelte -->
    <script>
        export let name;
    </script>
    <main>
        Hello, {name}
    </main>
```

access the components and pass the props

```
    <script>
        import Name from '$lib/Name.svelte';
    </script>
    <main>
        <Name name="Aditya" />
    </main>

    <!-- Output will render : Hello, Aditya -->
```

Defautl Values for Props

```
    export let name="Default Value";
```

## Slots in Svelte

Components can have child content, in same way that elements can.

```
    <slot> ....</slot>
```

```
    <slot name="title"> ....</slot>
```

```
    <slot prop={value} > ....</slot>
```

Examples

```
    <!-- Widget.svelte -->
    <div>
    <slot>
        this fallback content will be rendered when no content is provided, like in the first example
    </slot>
    </div>

    <!-- App.svelte -->
        <Widget />
    <!-- this component will render the default content -->

    <Widget>
      <p>this is some child content that will overwrite the default slot content</p>
    </Widget>
```

- Named slots allow consumers to target specific areas.

```
    <!-- Widget.svelte -->
    <div>
        <slot name="header">No header was provided</slot>
        <p>Some content between header and footer</p>
        <slot name="footer" />
    </div>

    <!-- App.svelte -->
    <Widget>
        <h1 slot="header">Hello</h1>
        <p slot="footer">Copyright (c) 2019 Svelte Industries</p>
    </Widget>
```

Passing slots in components

```
    <!-- Box.svelte -->
    <h1>
        <slot/>
    </h1>
```

```
    <!-- MainBox.svelte -->
    <slot name="header">default is provided if nothing is passed</slot>
    <p>simple text</p>
    <slot name="footer"/>
```

file : <code>+page.svelte</code>

```
    <script>
        import MainBox from '$lib/MainBox.svelte';
        import Box from '$lib/Box.svelte';
    </script>

    <MainBox>
        <Box slot="header"> Svelte Coder</Box>

        <svelte:fragment slot="footer">
            <p>All rights reserved.</p>
            <p>Copyright (c) 2019 Svelte Industries</p>
        </svelte:fragment>
    <MainBox>
```

## $$Slots

    If Slots are passed then only component will render the element or else it would not render

```
<!-- Card.svelte -->
    <div>
        <slot name="title/>

        {#if $$slot.desc}
            <h1>
                <slot name="desc"/>
            <h1>
            <EditButton>Edit<EditButton>
        {/if}
    </div>
```

if <code>$$slot.desc</code> is provided then only user will able to edit the data and can able to see the <code>h1</code> Tags and Component.

## Slot key={value}

Slots can be rendered zero or more times and can pass values back to parent using props.
using <code>let</code> directive.

Shorthand :

```
    let:item       ->     let:item={item}
                    &&
    <slot {item}   ->     <slot item={item}>
```

```
<!-- Fancy List -->
    <ul>
        {#each items as item}
            <li class="fancy">
                <slot prop={item} />
            </li>
        {/each}
    </ul>

    <!-- +page.svelte -->

    <FancyList {items} let:prop={thing}>
        <div>{thing.text}</div>
    </FancyList>
```

Example : Another Example 
```
    <!-- FancyList.svelte -->
    <ul>
    {#each items as item}
        <li class="fancy">
        <slot name="item" {item} />
        </li>
    {/each}
    </ul>

    <slot name="footer" />

    <!-- App.svelte -->
    <FancyList {items}>
        <div slot="item" let:item>{item.text}</div>
        <p slot="footer">Copyright (c) 2019 Svelte Industries</p>
    </FancyList>
```
