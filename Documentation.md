# Orion Library
This documentation is for the modified release of Orion Library. (by locality)

## Booting the Library
```lua
local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/skidmaxxing/Orion-Reborn/refs/heads/main/source.lua"))()
```

## Creating a Window
```lua
local Window = OrionLib:MakeWindow({
	Name = "Title of the library", 
	HidePremium = true, 
	Theme = "Default",
	SaveConfig = true, 
	ToggleUIButton = Enum.KeyCode.RightShift,
	UnlockMouse = false,
	ConfigFolder = "Orion",
})

--[[
	Name = <string> - The name of the UI.
	Theme = <string> - Theme.
	HidePremium = <bool> - Whether or not the user details shows Premium status or not.
	PremiumText = <string> - Shows text under user details, only when HidePremium is false
	SaveConfig = <bool> - Toggles the config saving in the UI.
	ConfigFolder = <string> - The name of the folder where the configs are saved.
	IntroEnabled = <bool> - Whether or not to show the intro animation.
	IntroText = <string> - Text to show in the intro animation.
	IntroIcon = <string> - URL to the image you want to use in the intro animation.
	Icon = <string> - URL to the image you want displayed on the window.
	ToggleUIButton = <Enum.KeyCode> - KeyCode for toggle UI visibility.
	UnlockMouse = <bool> - Makes mouse unlocked when opening UI.
	CloseCallback = <function> - Function to execute when the window is closed.
]]
```

### Available Themes
```lua
Theme Name - ThemeIdentifier

Default - Default
Dark Blue - DarkBlue
```

## Creating a Tab
```lua
local Tab = Window:MakeTab({
	Name = "Tab 1",
	Icon = "rbxassetid://4483345998",
	Restricted = false,
	RestrictedMessage = "Unauthorised Access",
	RestrictedIcon = "rbxassetid://3610239960",
	RestrictedLabel = "Premium Features",
	RestrictedLabelIcon = "rbxassetid://4483345875",
	RestrictedContent = "This part of the script is locked to Premium users"
})

--[[
Name: <string> — The name of the tab.
Icon: <string> — The icon of the tab.
Restricted: <bool> — Makes the tab inaccessible.
RestrictedMessage: <string> — Sets the text shown when access is restricted.
RestrictedIcon: <string> — Sets the icon displayed next to the restricted message.
RestrictedLabel: <string> — Text shown for restricted premium features.
RestrictedLabelIcon: <string> — Sets the icon displayed next to the restricted label.
RestrictedContent: <string> — The description or content shown for restricted premium features.
]]

```
## Creating a Section
```lua
local Section = Tab:AddSection({
	Name = "Section"
})

--[[
Name = <string> - The name of the section.
]]
```
You can add elements to sections the same way you would add them to a tab normally.

## Notifying the user
```lua
OrionLib:MakeNotification({
	Name = "Title!",
	Content = "Notification content... what will it say??",
	Image = "rbxassetid://4483345998",
	Time = 5
})

--[[
Title = <string> - The title of the notification.
Content = <string> - The content of the notification.
Image = <string> - The icon of the notification.
Time = <number> - The duration of the notfication.
]]
```



## Creating a Button
```lua
Tab:AddButton({
	Name = "Button!",
	Callback = function()
      		print("button pressed")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
```


## Creating a Checkbox toggle
```lua
Tab:AddToggle({
	Name = "This is a toggle!",
	Default = false,
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the toggle.
Default = <bool> - The default value of the toggle.
Callback = <function> - The function of the toggle.
]]
```

### Changing the value of an existing Toggle
```lua
CoolToggle:Set(true)
```



## Creating a Color Picker
```lua
Tab:AddColorpicker({
	Name = "Colorpicker",
	Default = Color3.fromRGB(255, 0, 0),
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - The name of the colorpicker.
Default = <color3> - The default value of the colorpicker.
Callback = <function> - The function of the colorpicker.
]]
```

### Setting the color picker's value
```lua
ColorPicker:Set(Color3.fromRGB(255,255,255))
```


## Creating a Slider
```lua
Tab:AddSlider({
	Name = "Slider",
	Min = 0,
	Max = 20,
	Default = 5,
	Color = Color3.fromRGB(255,255,255),
	Increment = 1,
	ValueName = "bananas",
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the slider.
Min = <number> - The minimal value of the slider.
Max = <number> - The maxium value of the slider.
Increment = <number> - How much the slider will change value when dragging.
Default = <number> - The default value of the slider.
ValueName = <string> - The text after the value number.
Callback = <function> - The function of the slider.
]]
```

### Change Slider Value
```lua
Slider:Set(2)
```
Make sure you make your slider a variable (local CoolSlider = Tab:AddSlider...) for this to work.


## Creating a Label
```lua
Tab:AddLabel("Label")
```

### Changing the value of an existing label
```lua
CoolLabel:Set("Label New!")
```


## Creating a Paragraph
```lua
Tab:AddParagraph("Paragraph","Paragraph Content")
```

### Changing an existing paragraph
```lua
CoolParagraph:Set("Paragraph New!", "New Paragraph Content!")
```


## Creating an Adaptive Input
```lua
Tab:AddTextbox({
	Name = "Textbox",
	Default = "default box input",
	TextDisappear = true,
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - The name of the textbox.
Default = <string> - The default value of the textbox.
TextDisappear = <bool> - Makes the text disappear in the textbox after losing focus.
Callback = <function> - The function of the textbox.
]]
```


## Creating a Keybind
```lua
Tab:AddBind({
	Name = "Bind",
	Default = Enum.KeyCode.E,
	Hold = false,
	Callback = function()
		print("press")
	end    
})

--[[
Name = <string> - The name of the bind.
Default = <keycode> - The default value of the bind.
Hold = <bool> - Makes the bind work like: Holding the key > The bind returns true, Not holding the key > Bind returns false.
Callback = <function> - The function of the bind.
]]
```

### Chaning the value of a bind
```lua
Bind:Set(Enum.KeyCode.E)
```


## Creating a Dropdown menu
```lua
Tab:AddDropdown({
	Name = "Dropdown",
	Default = "1",
	Options = {"1", "2"},
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the dropdown.
Default = <string> - The default value of the dropdown.
Options = <table> - The options in the dropdown.
Callback = <function> - The function of the dropdown.
]]
```

### Adding a set of new Dropdown buttons to an existing menu
```lua
Dropdown:Refresh(List<table>,true)
```

The above boolean value "true" is whether or not the current buttons will be deleted.
### Selecting a dropdown option
```lua
Dropdown:Set("dropdown option")
```

# Finishing your script (REQUIRED)
The below function needs to be added at the end of your code.
```lua
OrionLib:Init()
```

### How flags work.
The flags feature in the ui may be confusing for some people. It serves the purpose of being the ID of an element in the config file, and makes accessing the value of an element anywhere in the code possible.
Below in an example of using flags.
```lua
Tab1:AddToggle({
    Name = "Toggle",
    Default = true,
    Save = true,
    Flag = "toggle"
})

print(OrionLib.Flags["toggle"].Value) -- prints the value of the toggle.
```
Flags only work with the toggle, slider, dropdown, bind, and colorpicker.

### Making your interface work with configs.
In order to make your interface use the configs function you first need to add the `SaveConfig` and `ConfigFolder` arguments to your window function. The explanation of these arguments in above.
Then you need to add the `Flag` and `Save` values to every toggle, slider, dropdown, bind, and colorpicker you want to include in the config file.
The `Flag = <string>` argument is the ID of an element in the config file.
The `Save = <bool>` argument includes the element in the config file.
Config files are made for every game the library is launched in.

### Destroying the element
```lua
local Section = Tab:AddSection({
	Name = "Section"
})
Section:Delete()
```


## Destroying the Interface
```lua
OrionLib:Destroy()
```
