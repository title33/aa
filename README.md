

local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/title33/SaveManager/main/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()
local Options = Fluent.Options

-- Variables
local Boss -- Variable to store the selected Boss

-- Function to define No
function No()
    for i, v in ipairs(workspace.Lives:GetChildren()) do
        if not game:GetService("Players"):GetPlayerFromCharacter(v) then
            local cleanedName = string.gsub(v.Name, "%d+$", "")
            v.Name = tostring(cleanedName)
        end
    end

    workspace.Lives.ChildAdded:Connect(function(model)
        task.wait()
        if not game:GetService("Players"):GetPlayerFromCharacter(model) then
            local cleanedName = string.gsub(model.Name, "%d+$", "")
            model.Name = cleanedName
        end
    end)
end

function TP(CFramePosition)
    local Players = game:GetService("Players")
    local LocalPlayer = Players.LocalPlayer
    local HumanoidRootPart = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")

    if HumanoidRootPart then
        HumanoidRootPart.CFrame = CFramePosition
    end
end

No() -- Call the function No

-- Global variables
_G.p = false
_G.SelectWeapon = "YourDefaultWeaponName"

-- Function to handle Auto Farm Boss
function AutoFarmBoss()
    _G.p = true

    function A()
        game:GetService('VirtualUser'):CaptureController()
        game:GetService('VirtualUser'):Button1Down(Vector2.new(1280, 672))
    end

    spawn(function()
        while wait() do
            pcall(function()
                if _G.p then
                    for _, v in pairs(game:GetService("Workspace").Lives:GetDescendants()) do
                        if v.Name == Boss and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health >= 1 then
                            repeat task.wait()
                                A()
                                v.HumanoidRootPart.Size = Vector3.new(10, 10, 10)
                                v.HumanoidRootPart.Transparency = 0.9
                                v.Humanoid.WalkSpeed = 0
                                v.Humanoid.JumpPower = 0
                                TP(v.HumanoidRootPart.CFrame * CFrame.new(0, 5, 0) * CFrame.Angles(math.rad(-90), 0, 0))
                            until _G.p == false
                        end
                    end
                end
            end)
        end
    end)

    spawn(function()
        while wait() do
            pcall(function()
                if _G.p then
                    for i, v in pairs(game:GetService("Workspace").Chests:GetDescendants()) do
                        if v.ClassName == "ProximityPrompt" then
                            repeat task.wait()
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame
                                fireproximityprompt(v, 30)
                            until _G.p == false
                        end
                    end
                end
            end)
        end
    end)

    spawn(function()
        while _G.p do
            wait()
            pcall(function()
                for i, v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                    if v.Name == _G.SelectWeapon then
                        game.Players.LocalPlayer.Character.Humanoid:EquipTool(v)
                    end
                end
            end)
        end
    end)
end

-- Create Fluent window
local Window = Fluent:CreateWindow({
    Title = "Xylo Hub",
    SubTitle = "by Sky",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true,
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl
})

-- Add Tabs
local Tabs = {
    Farm = Window:AddTab({ Title = "General", Icon = "home" }),
    Skil = Window:AddTab({ Title = "Skills", Icon = "database-zap" }),
    TP = Window:AddTab({ Title = "Teleport", Icon = "fast-forward" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local boss = {
    'Shadow',
    'Gojo',
    'Kashimo',
    'Sukuna',
    'Snow Bandit Leader',
    'Shank',
    'Monkey King',
    'Sand Man',
    'Bomb Man',
    'Bandit Leader',
    'Artoria',
    'Uraume',
    'Gojo [Unleashed]',
    'Sukuna [Half Power]',
    'Rimuru',
    'Killua',
}

-- Add Dropdowns in the "General" Tab
Tabs.Farm:AddDropdown("Select Boss", {
    Title = "Select Boss",
    Values = boss,
    Multi = false,
    Default = 1,
    Callback = function(v)
        Boss = v
    end
})

-- Add Toggle in the "General" Tab
Tabs.Farm:AddToggle("Auto Farm Boss", {
    Title = "Auto Farm Boss", 
    Default = false, 
    Callback = function(t) 
        No()
        _G.p = t
        AutoFarmBoss()
    end
})

-- Ignore Theme Settings of SaveManager
SaveManager:IgnoreThemeSettings()
SaveManager:SetLibrary(Fluent)
SaveManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")
SaveManager:BuildConfigSection(Tabs.Settings)

-- Select the 1st Tab
Window:SelectTab(1)

-- Load Autoload Config of SaveManager
SaveManager:LoadAutoloadConfig()
