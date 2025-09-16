# Aux Library

🍷 A clean Library you can use on your Script made by Aux 🍷

## Installation

```lua
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Xock1/Aux-Library-/refs/heads/main/Aux-Library.lua"))()
```

## Basic Setup

```lua
-- Create a window
local main = library:CreateWindow("Window Title")

-- Initialize the library
library:Init()
```

## Components

### Label
```lua
main:AddLabel({
    text = "This is a label"
})
```

### Button
```lua
main:AddButton({
    text = "Click Me",
    callback = function()
        print("Button clicked")
    end
})
```

### Toggle
```lua
main:AddToggle({
    text = "Enable Feature",
    state = false,
    callback = function(state)
        print("Toggle is now:", state)
    end
})
```

### Slider
```lua
main:AddSlider({
    text = "Speed",
    min = 1,
    max = 100,
    value = 50,
    float = false,
    callback = function(value)
        print("Slider value:", value)
    end
})
```

### Textbox
```lua
main:AddBox({
    text = "Username",
    value = "default text",
    callback = function(text, enter)
        print("Input:", text, "Enter pressed:", enter)
    end
})
```

### Keybind
```lua
main:AddBind({
    text = "Toggle Speed",
    key = "F",
    hold = false,
    callback = function()
        print("Keybind pressed")
    end
})
```

### Dropdown
```lua
local dropdown = main:AddList({
    text = "Select Option",
    values = {"Option 1", "Option 2", "Option 3"},
    value = "Option 1",
    callback = function(selected)
        print("Selected:", selected)
    end
})
```

### Color Picker
```lua
main:AddColor({
    text = "Player Color",
    color = Color3.fromRGB(255, 0, 0),
    callback = function(color)
        print("Color changed:", color)
    end
})
```

### Folder
```lua
local folder = main:AddFolder("Combat")

folder:AddToggle({
    text = "Auto Attack",
    state = false,
    callback = function(state)
        print("Auto Attack:", state)
    end
})
```

## Methods

### Library Methods
```lua
library:Close()  -- Toggle library visibility
library.flags["FlagName"]  -- Get component value by flag
```

### Dropdown Methods
```lua
dropdown:AddValue("New Option")      -- Add option
dropdown:RemoveValue("Option 1")     -- Remove option
dropdown:SetValue("Option 2")        -- Set selected value
```

### Keybind Methods
```lua
keybind:SetKey("G")  -- Change keybind
```

### Color Picker Methods
```lua
colorpicker:SetColor(Color3.new(0, 1, 0))  -- Set color
```

### Toggle Methods
```lua
toggle:SetState(true)  -- Set toggle state
```

### Slider Methods
```lua
slider:SetValue(75)  -- Set slider value
```

## Options

### Common Options
- `text` - Display text for the component
- `callback` - Function to run when component changes
- `flag` - Custom flag name for library.flags (defaults to text)

### Slider Options
- `min` - Minimum value
- `max` - Maximum value
- `value` - Default value
- `float` - Allow decimal values (true/false)

### Keybind Options
- `key` - Default key (string or KeyCode)
- `hold` - Trigger while holding (true/false)

### Dropdown Options
- `values` - Array of options
- `value` - Default selected option

### Color Picker Options
- `color` - Default Color3 value

## Flags

Access component values using flags:
```lua
print(library.flags["Toggle Name"])  -- Get toggle state
print(library.flags["Slider Name"])  -- Get slider value
print(library.flags["Dropdown Name"])  -- Get selected option
```

## Controls

- Right Shift: Toggle library visibility
- Click outside popups to close them
- Drag window titles to move windows

## Example

```lua
local library = loadstring(game:HttpGet("YOUR_URL"))()

local main = library:CreateWindow("My Script")

main:AddLabel({text = "Player Controls"})

main:AddSlider({
    text = "Walk Speed",
    min = 16,
    max = 100,
    value = 16,
    callback = function(speed)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = speed
    end
})

main:AddToggle({
    text = "Infinite Jump",
    state = false,
    callback = function(state)
        if state then
            -- Enable infinite jump
        else
            -- Disable infinite jump
        end
    end
})

main:AddBind({
    text = "Fly Toggle",
    key = "F",
    callback = function()
        -- Toggle fly
    end
})

library:Init()
```
