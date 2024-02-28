local ScreenGui = Instance.new("ScreenGui")
local ui = Instance.new("ImageButton")
local UICorner = Instance.new("UICorner")

--Properties:

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

ui.Name = "ui"
ui.Parent = ScreenGui
ui.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
ui.BorderColor3 = Color3.fromRGB(0, 0, 0)
ui.BorderSizePixel = 0
ui.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
ui.Size = UDim2.new(0, 68, 0, 67)
ui.Image = "http://www.roblox.com/asset/?id=14420244942"
ui.MouseButton1Click:Connect(function()
    game.CoreGui:FindFirstChild("SereenGui").Enabled = not game.CoreGui:FindFirstChild("SereenGui").Enabled
end)


UICorner.CornerRadius = UDim.new(0.300000012, 0)
UICorner.Parent = ui


local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "SSS HUB ",
    SubTitle = "by noob script",
    TabWidth = 130,
    Size = UDim2.fromOffset(530, 340),
    Acrylic = true, 
    Theme = "Light",

})


local Tabs = {
    Main = Window:AddTab({ Title = "| Main", Icon = "home" }),
    Auto = Window:AddTab({ Title = "| Auto Farm", Icon = "home" }),
    TP = Window:AddTab({ Title = "| Teleport", Icon = "home" }),
    plr = Window:AddTab({ Title = "| Players", Icon = "home" }),
    Boos = Window:AddTab({ Title = "| Auto Spawn [ Soon ]", Icon = "home" })
    
    
    
}

local Options = Fluent.Options

do
    Fluent:Notify({
        Title = "SSS HUB",
        Content = "ติดตามกูด้วย",
        SubContent = "NOOB SCRIPT", 
        Duration = 10 
    })

    local Toggle = Tabs.Main:AddToggle("Auto Chests", {Title = "Auto Chests", Default = false })
    Toggle:OnChanged(function(hum)
        _G.LED = hum
        while _G.LED do wait()
for i,v in pairs(game:GetService("Workspace").Chests:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
                end
            end
        end
    end)


    local Toggle = Tabs.Main:AddToggle("Grabtools", {Title = "Grabtools", Default = false })
    Toggle:OnChanged(function(hee)
        _G.EZ = hee
        while _G.EZ do wait()
        for i,v in pairs(game:GetService("Workspace").ItemDrop:GetChildren()) do
  v.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
                end
           end
    end)



Tabs.Main:AddParagraph({
        Title = "",
        Content = ""
    })

        Tabs.Main:AddButton({
        Title = "Go to Traveling merchant",
        Description = "วาปไปหาพ่อค้าสุ่มเกิด",
        Callback = function()
            for i,v in pairs(game:GetService("Workspace").NPC["Traveling merchant"]:GetDescendants()) do

if v.ClassName == "ProximityPrompt" then

game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame * CFrame.new(0,3,0)

wait(.1)

fireproximityprompt(v,30)

end

      end
        end
    })


Tabs.Main:AddParagraph({
        Title = "",
        Content = ""
    })



    local Toggle = Tabs.Main:AddToggle("Auto Z X C V", {Title = "Auto Z X C V", Default = false })
    Toggle:OnChanged(function(he)
        _G.EZo = he
        while _G.EZo do wait()
game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
end
    end)

Tabs.Main:AddParagraph({
        Title = "",
        Content = ""
    })

    local Toggle = Tabs.Main:AddToggle("Auto Random fruit Beli", {Title = "Auto Random fruit Beli", Default = false })
    Toggle:OnChanged(function(hep)
        _G.EZq = hep
        while _G.EZq do wait()
for i,v in pairs(game:GetService("Workspace").Shop:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(790.203735, 35.5073013, 1201.40369, 0.026754817, -8.37544611e-09, 0.999642015, 1.24128064e-07, 1, 5.05623188e-09, -0.999642015, 1.23948354e-07, 0.026754817)
                    end
                end
            end
        end)

    local Toggle = Tabs.Main:AddToggle("Auto Random fruit Gem", {Title = "Auto Random fruit Gem", Default = false })
    Toggle:OnChanged(function(hee)
        _G.EZ = hee
        while _G.EZ do wait()
for i,v in pairs(game:GetService("Workspace").Shop:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-741.048889, 43.4787788, -1933.82019, -0.0251465552, 7.8026531e-08, 0.999683797, -1.09866749e-09, 1, -7.80788483e-08, -0.999683797, -3.06173398e-09, -0.0251465552)
end
end
end
    end)

      Tabs.Auto:AddButton({
        Title = "boost fps",
        Description = "แก้แลค",
        Callback = function()
        local decalsyeeted = true 

local g = game

local w = g.Workspace

local l = g.Lighting

local t = w.Terrain

sethiddenproperty(l,"Technology",2)

sethiddenproperty(t,"Decoration",false)

t.WaterWaveSize = 0

t.WaterWaveSpeed = 0

t.WaterReflectance = 0

t.WaterTransparency = 0

l.GlobalShadows = 0

l.FogEnd = 9e9

l.Brightness = 0

settings().Rendering.QualityLevel = "Level01"

for i, v in pairs(w:GetDescendants()) do

    if v:IsA("BasePart") and not v:IsA("MeshPart") then

        v.Material = "Plastic"

        v.Reflectance = 0

    elseif (v:IsA("Decal") or v:IsA("Texture")) and decalsyeeted then

        v.Transparency = 1

    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then

        v.Lifetime = NumberRange.new(0)

    elseif v:IsA("Explosion") then

        v.BlastPressure = 1

        v.BlastRadius = 1

    elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then

        v.Enabled = false

    elseif v:IsA("MeshPart") and decalsyeeted then

        v.Material = "Plastic"

        v.Reflectance = 0

        v.TextureID = 10385902758728957

    elseif v:IsA("SpecialMesh") and decalsyeeted  then

        v.TextureId=0

    elseif v:IsA("ShirtGraphic") and decalsyeeted then

        v.Graphic=0

    elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then

        v[v.ClassName.."Template"]=0

    end

end

for i = 1,#l:GetChildren() do

    e=l:GetChildren()[i]

    if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then

        e.Enabled = false

    end

end

w.DescendantAdded:Connect(function(v)

    wait()--prevent errors and shit

   if v:IsA("BasePart") and not v:IsA("MeshPart") then

        v.Material = "Plastic"

        v.Reflectance = 0

    elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then

        v.Transparency = 1

    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then

        v.Lifetime = NumberRange.new(0)

    elseif v:IsA("Explosion") then

        v.BlastPressure = 1

        v.BlastRadius = 1

    elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then

        v.Enabled = false

    elseif v:IsA("MeshPart") and decalsyeeted then

        v.Material = "Plastic"

        v.Reflectance = 0

        v.TextureID = 10385902758728957

    elseif v:IsA("SpecialMesh") and decalsyeeted then

        v.TextureId=0

    elseif v:IsA("ShirtGraphic") and decalsyeeted then

        v.ShirtGraphic=0

    elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then

        v[v.ClassName.."Template"]=0

              end

        end)

        end
})

Tabs.Auto:AddParagraph({
        Title = "",
        Content = ""
    })

local Weaponlist = {}
local Weapon = nil
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    table.insert(Weaponlist,v.Name)
    end

Tabs.Auto:AddDropdown("Weapon", {
        Title = "Weapon",
        Values = Weaponlist,
        Multi = false,
        Default = nil,
        Callback = function(v)
        _G.Weapon = v
       end
   })

     local Toggle = Tabs.Auto:AddToggle("Auto Equip", {Title = "Auto Equip", Default = false })
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

Tabs.Auto:AddParagraph({
        Title = "",
        Content = ""
    })

              do
          local P = game:GetService("Workspace"):FindFirstChild("Noclip")
          if NM then
          NM:Destroy()
          end
    end
local Noclip = Instance.new("Part",workspace)
          Noclip.Name = "Noclip"
          Noclip.CanCollide = true
          Noclip.Anchored = true
          Noclip.Transparency = 0
          Noclip.Size = Vector3.new(30,1,30)
          
function Nom()
game:GetService("Workspace"):FindFirstChild("Noclip").CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,-3.5,0)
end



function CA()
for i,v in pairs(game:GetService("Workspace").Chests:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
fireproximityprompt(v,30)
end
      end
      		end

function No()
for i, v in ipairs(workspace.Lives:GetChildren()) do
    if not game:GetService("Players"):GetPlayerFromCharacter(v) then -- if not player 
        local cleanedName = string.gsub(v.Name, "%d+$", "")
        v.Name = tostring(cleanedName)
    end
end

workspace.Lives.ChildAdded:Connect(function(model)
task.wait()
if not game:GetService("Players"):GetPlayerFromCharacter(model) then -- if not player then
        local cleanedName = string.gsub(model.Name, "%d+$", "")
        model.Name = cleanedName
				end
		end)
end





No()

    local Toggle = Tabs.Auto:AddToggle("Auto Attack", {Title = "Auto Attack", Default = false })
    Toggle:OnChanged(function(ah)
_G.Ato = ah
while _G.Ato do wait()
game:GetService'VirtualUser':CaptureController()
game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
end
    end)
    
    Tabs.Auto:AddParagraph({
        Title = "",
        Content = ""
    })
    
    
        local Toggle = Tabs.Auto:AddToggle("Auto Farm Boss", {Title = "Auto Farm Boss", Default = false })
    Toggle:OnChanged(function(ssk)
_G.eami = ssk

function MonsSpawned(Mons)
    for _, v in pairs(game:GetService('Workspace').Lives:GetDescendants()) do
        if v.Name == Mons and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 then
            return true
        end
    end
    return false
end


spawn(function()
    while wait() do
        pcall(function()
            if _G.eami then
                local MonNames = {
                    'Shadow',
                    'Gojo',
                    'Kashimo',
                    'Sukuna',
                    'Artoria',
                    'Uraume',
		            'Gojo [Unleashed]',
                    'Sukuna [Half Power]',
		            'Rimuru',
                    'Killua',
                    'Ichigo',
                    'Choso'
                   
                }

                for _, v in pairs(game:GetService('Workspace').Lives:GetDescendants()) do
                    if table.find(MonNames, v.Name) and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 then
                        repeat
                        CA()
                            wait()   
                            v.HumanoidRootPart.Size = Vector3.new(10, 10, 10)
                            v.HumanoidRootPart.Transparency = 0.9
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 0, 7)
                        until _G.eami == false or v.Humanoid.Health <= 0
                    end
                end
            end
        end)
    end
end)
	
    end)
    
    
    
        local Toggle = Tabs.Auto:AddToggle("Auto Farm Gem", {Title = "Auto Farm Gem", Default = false })
    Toggle:OnChanged(function(ssn)
_G.eam = ssn
function MonsSpawned(Mons)
    for _, v in pairs(game:GetService('Workspace').Lives:GetDescendants()) do
        if v.Name == Mons and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 then
            return true
        end
    end
    return false
end


spawn(function()
    while wait() do
        pcall(function()
            if _G.eam then
                local MonNames = {
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
                    'Ichigo',
                    'Choso'
		    
                }

                for _, v in pairs(game:GetService('Workspace').Lives:GetDescendants()) do
                    if table.find(MonNames, v.Name) and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 then
                        repeat
                        CA()
                            wait()   
                            v.HumanoidRootPart.Size = Vector3.new(10, 10, 10)
                            v.HumanoidRootPart.Transparency = 0.9
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 0, 7)
                        until _G.eam == false or v.Humanoid.Health <= 0
                    end
                end
            end
        end)
    end
end)
	

    end)
    
    
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
        Title = "TP Shop",
        Description = "วาปไปที่ร้านค้า",
        Callback = function()
      		for i,v in pairs(game:GetService("Workspace").Shop[shop]:GetDescendants()) do
if v.ClassName == "ProximityPrompt" then
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame * CFrame.new(0,5,0)
end
      end
        end
    })
    
    Tabs.TP:AddParagraph({
        Title = "",
        Content = ""
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
        Title = "TP island",
        Description = "วาปไปที่เกาะ",
        Callback = function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.workspace.Locations[map].CFrame * CFrame.new(0,-100,0)
        end
    })
    
    PlayerTP = {}
for i,v in pairs(game:GetService("Players"):GetChildren()) do
    table.insert(PlayerTP,v.Name) 
end
    
    Tabs.plr:AddDropdown("Pleyers", {
        Title = "Pleyers",
        Values = PlayerTP,
        Multi = false,
        Default = nil,
        Callback = function(t)
        PlayerTP = t
       end
   })
    
            Tabs.plr:AddButton({
        Title = "TP Pleyers",
        Description = "วาปไปที่ผู้เล่น",
        Callback = function()
 game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[PlayerTP].Character.HumanoidRootPart.CFrame
        end
    })
    
        local Toggle = Tabs.plr:AddToggle("Auto TP", {Title = "Auto TP", Default = false })
    Toggle:OnChanged(function(t)
_G.TPPlayer = t
while _G.TPPlayer do wait()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[PlayerTP].Character.HumanoidRootPart.CFrame * CFrame.new(0,0,3)
end
    end)
    

        
Input:OnChanged(function()
        print("Input updated:", Input.Value)
    end)
end

SaveManager:LoadAutoloadConfig()
