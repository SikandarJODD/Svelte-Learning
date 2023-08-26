# Building blocks

Components are the building blocks of Svelte applications. They are written into <code>.svelte</code> files.

#### Basic Setup of .svelte file

```bash
    <script>
        # Javascript Code
    <script>

    <main>
        # Html Code
    </main>

    <style>
        # Css Code
    </style>

```

\*all three sections - script,styles,markup are optional

#### Creating Props

<code>export</code> is used to send props

```bash
    <script>
        # Javascript Code
        export let username;
        # or
        export let userName = 'this is default value';
    <script>

    <main>
        # Html Code
    </main>

    <style>
        # Css Code
    </style>

```

#### Assignments are 'reactive'

To change the component state and trigger a <i>re-render</i>, just assign to a locally declared variable

```bash
    <script>
        let count = 0;

        function handleClick() {
            # // calling this function will trigger an
            # // update if the markup references `count`
            count = count + 1;
        }
    </script>
```

as svelte reactivity is based on assignments, using array method like <code>.push()</code> and <code>.splice()</code> won't work automatically trigger updates..

```bash
    <script>
        let values=[1,2];

        function handleClick() {
            values.push(3);
             console.log(values);
            # this will update the array but not trigger an update

            # to trigger an update 
            values = values;
        }
    </script>
```

for more detailed view visit [svelte.dev](https://svelte.dev/docs/svelte-components)


[Home](../README.md)
[Logical Blocks](/conditional_rendering/struct.md)
