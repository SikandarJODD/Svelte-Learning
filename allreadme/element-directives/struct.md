# Element Directives & Style-Props

### class:name

```
    <div class:name >Hello </div>

    <!-- These are equivalent -->
    <div class={isActive ? 'active' : ''}>...</div>
    <div class:active={isActive}>...</div>

    <!-- Shorthand, for when name and value match -->
    <div class:active>...</div>

    <!-- Multiple class toggles can be included -->
    <div class:active class:inactive={!active} class:isAdmin>...</div>
```
### style:property

```
    style:property={value}
```
example :
```
    <div style:color="red" > Hello</div>
```

shortand : property matches the varialble name
```
    <script>
        let color="red";
    </script>
    <main>
        <div style:color >This text color is Red</div>
    </main>
    
```

## Style Props 

```
    --style-props="anycssvalue"
```
```
    <!-- Create Slider Component and Pass Style Props -->
    <Slide bind:value min={0} max={100}  --bgColor="black" --textColor="white" >

    # --bgColor & --textColor are the CSS Props 
    # Data is Sent from parent Component to Button(child) Component
```
Desugars to this : 
```
    <div style="display: contents; --bgColor: black; --textColor: white">
        <Slider bind:value min={0} max={100} />
    </div>
```