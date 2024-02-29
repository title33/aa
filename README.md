local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/title33/SaveManager/main/README.md"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "Xylo Hub",
    SubTitle = "by Sky",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

--Fluent provides Lucide Icons https://lucide.dev/icons/ for the tabs, icons are optional
local Tabs = {
    General = Window:AddTab({ Title = "General", Icon = "home" }),
    Skil = Window:AddTab({ Title = "Skil", Icon = "battery-charging" }),
    TP = Window:AddTab({ Title = "Tp", Icon = "chevrons-right" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local Options = Fluent.Options




local Dropdown = Tabs.General:AddDropdown("Boss", {
    Title = "Boss",
    Values = {"Shadow", "Gojo", "Kashimo", "Sukuna", "Snow Bandit Leader", "Shank", "Monkey King", "Sand Man", "Bomb Man", "Bandit Leader", "Artoria", "Uraume", "Gojo [Unleashed]", "Sukuna [Half Power]", "Rimuru", "Killua"},
    Multi = false,
    Default = 1,
})

Dropdown:SetValue("None")

Dropdown:OnChanged(function(Value)
    SelectedBoss = Value
end)

local Toggle = Tabs.General:AddToggle("MyToggle", {Title = "Auto Farm Boss", Default = false })

Toggle:OnChanged(function(Value)
    _G.AutoFarm = Value

    while _G.AutoFarm do
        wait()
        if SelectedBoss ~= "None" then
            local BossCFrame = game.Workspace[SelectedBoss].HumanoidRootPart.CFrame * CFrame.new(0, 0, 3)
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = BossCFrame
        end
    end
end)

Options.MyToggle:SetValue(false)


local Weaponlist = {}
local Weapon = nil
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
    end

Tabs.General:AddDropdown("Weapon", {
        Title = "Weapon",
        Values = Weaponlist,
        Multi = false,
        Default = nil,
        Callback = function(v)
        _G.Weapon = v
       end
   })



     local Toggle = Tabs.General:AddToggle("Auto Equip", {Title = "Auto Equip", Default = false })
    Toggle:OnChanged(function(a)
    _G.AutoEquiped = a
    end)
    
spawn(function()
while wait() do
if _G.AutoEquiped then
pcall(function()
game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(_G.Weapon))
end)
end
end
end)    

    local Toggle = Tabs.General:AddToggle("Auto Attack", {Title = "Auto Attack", Default = false })
    Toggle:OnChanged(function(ah)
_G.Ato = ah
while _G.Ato do wait()
game:GetService'VirtualUser':CaptureController()
game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
end
    end)


    local Toggle = Tabs.General:AddToggle("Auto Chests", {Title = "Auto Chests", Default = false })
    Toggle:OnChanged(function(wow)
        _G.aa = wow
        while _G.aa do wait()
for i,v in pairs(game:GetService("Workspace").Chests:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
                end
            end
        end
    end)








    local Toggle = Tabs.Skil:AddToggle("Auto Skil Z", {Title = "Auto Skil Z", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoZ = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoZ then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)
    


    local Toggle = Tabs.Skil:AddToggle("Auto Skil X", {Title = "Auto Skil X", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoX = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoX then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)


    local Toggle = Tabs.Skil:AddToggle("Auto Skil C", {Title = "Auto Skil C", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoC = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoC then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)
 


    local Toggle = Tabs.Skil:AddToggle("Auto Skil V", {Title = "Auto Skil V", Default = false })

    Toggle:OnChanged(function(G)
       _G.AutoV = G

spawn(function()
while wait(.1) do
    pcall(function()
if _G.AutoV then
game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
                end
        end)
   end
end)

    end)

    Options.MyToggle:SetValue(false)

players = {}

for i, v in pairs(game:GetService("Players"):GetChildren()) do
    table.insert(players, v.Name)
end

local DropdownPlayer = Tabs.TP:AddDropdown("Player", {
    Title = "Player",
    Values = players,
    Multi = false,
    Default = 1,
})

DropdownPlayer:SetValue("None")

DropdownPlayer:OnChanged(function(V)
    Select = V
end)

Tabs.TP:AddButton({
    Title = "Refresh",
    Description = "Refresh",
    Callback = function()
        Window:Dialog({
            Title = "Refresh",
            Content = "Refresh",
            Buttons = {
                {
                    Title = "Confirm",
                    Callback = function()
                        table.clear(players)
                        for i, v in pairs(game:GetService("Players"):GetChildren()) do
                            table.insert(players, v.Name)
                        end
                    end
                },
                {
                    Title = "Cancel",
                    Callback = function()
                        print("no")
                    end
                }
            }
        })
    end
})

Tabs.TP:AddButton({
    Title = "Teleport to Player",
    Description = "Teleport to the selected player",
    Callback = function()
        Window:Dialog({
            Title = "Teleport to Player",
            Content = "Teleport to the selected player",
            Buttons = {
                {
                    Title = "Confirm",
                    Callback = function()
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[Select].Character.HumanoidRootPart.CFrame
                    end
                },
                {
                    Title = "Cancel",
                    Callback = function()
                        print("no")
                    end
                }
            }
        })
    end
})


    shop = {}
for i ,v in pairs(game:GetService("Workspace").Shop:GetChildren()) do
table.insert(shop,v.Name)
end

Tabs.TP:AddDropdown("shop", {
        Title = "shop",
        Values = shop,
        Multi = false,
        Default = nil,
        Callback = function(ma)
        shop = ma
       end
   })



        Tabs.TP:AddButton({
        Title = "TP To Shop",
        Description = "",
        Callback = function()
      		for i,v in pairs(game:GetService("Workspace").Shop[shop]:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame * CFrame.new(0,5,0)
end
      end
        end
    })
    


map = {}
for i ,v in pairs(game:GetService("Workspace").Locations:GetChildren()) do
table.insert(map,v.Name)
end

Tabs.TP:AddDropdown("island", {
        Title = "island",
        Values = map,
        Multi = false,
        Default = nil,
        Callback = function(mt)
        map = mt
       end
   })
   
        Tabs.TP:AddButton({
        Title = "TP To island",
        Description = "TP To island",
        Callback = function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.workspace.Locations[map].CFrame * CFrame.new(0,-100,0)
        end
    })

-- Addons:
-- SaveManager (Allows you to have a configuration system)
-- InterfaceManager (Allows you to have a interface managment system)

-- Hand the library over to our managers
SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

-- Ignore keys that are used by ThemeManager.
-- (we dont want configs to save themes, do we?)
SaveManager:IgnoreThemeSettings()

-- You can add indexes of elements the save manager should ignore
SaveManager:SetIgnoreIndexes({})

-- use case for doing it this way:
-- a script hub could have themes in a global folder
-- and game configs in a separate folder per game
InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")

InterfaceManager:BuildInterfaceSection(Tabs.Settings)
SaveManager:BuildConfigSection(Tabs.Settings)


Window:SelectTab(1)


-- You can use the SaveManager:LoadAutoloadConfig() to load a config
-- which has been marked to be one that auto loads!
SaveManager:LoadAutoloadConfig()
