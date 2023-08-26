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