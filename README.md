local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/title33/SaveManager/main/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Options = Fluent.Options

-- ตัวแปร
local free -- ตัวแปรที่ใช้เก็บข้อมูลเลือก Mob
local Boss -- ตัวแปรที่ใช้เก็บข้อมูลเลือก Boss
local MONName -- ตัวแปรที่ใช้เก็บชื่อของ Mob

-- ฟังก์ชัน AutoAttack
function AutoAttack()
    game:GetService('VirtualUser'):CaptureController()
    game:GetService('VirtualUser'):Button1Down(Vector2.new(1280, 672))
end

-- ฟังก์ชัน AutoAttackBoss
function AutoAttackBoss()
    game:GetService('VirtualUser'):CaptureController()
    game:GetService('VirtualUser'):Button1Down(Vector2.new(1280, 672))
end

-- ฟังก์ชัน SelectMonster
function SelectMonster()
    if free == "Bandit" then
        MONName = "Bandit [LV.5]"
    elseif free == "Bandit Leader" then
        MONName = "Bandit Leader [LV.15]"
    elseif free == "Clown Pirate" then
        MONName = "Clown Pirate [LV.50]"
    elseif free == "Marine" then
        MONName = "Marine [LV.300]"
    elseif free == "Monkey" then
        MONName = "Monkey [LV.750]"
    elseif free == "Monkey King" then
        MONName = "Monkey King [LV.1000]"
    elseif free == "Bomb Man" then
        MONName = "Bomb Man [LV.1500]"
    elseif free == "Sand Man" then
        MONName = "Sand Man [LV.2000]"
    elseif free == "Snow Bandit" then
        MONName = "Snow Bandit [LV.1750]"
    elseif free == "Snow Bandit Leader" then
        MONName = "Snow Bandit Leader [LV.2350]"
    end
end

-- ฟังก์ชัน SelectQuest
function SelectQuest()
    if free == "Bandit" then
        CFrameQuest = CFrame.new(-953.566528, 34.5999947, -552.164612, -0.0109250434, -3.3378329e-09, -0.999940336, 1.94075778e-09, 1, -3.35923622e-09, 0.999940336, -1.97734162e-09, -0.0109250434)
    elseif free == "Bandit Leader" then
        CFrameQuest = CFrame.new(-1097.55042, 34.6000023, -492.550354, -0.0683717504, 2.67226739e-08, 0.997659922, 5.38579563e-08, 1, -2.30943531e-08, -0.997659922, 5.21529238e-08, -0.0683717504)
    elseif free == "Clown Pirate" then
        CFrameQuest = CFrame.new(-71.5784531, 36.4347496, 50.7921715, 0.00707866857, 2.668971e-08, 0.999974966, -5.85915032e-08, 1, -2.62756199e-08, -0.999974966, -5.84040372e-08, 0.00707866857)
    elseif free == "Marine" then
        CFrameQuest = CFrame.new(848.661377, 35.5073013, 1264.83777, -0.998497367, 5.36386899e-08, 0.0548002385, 5.90094018e-08, 1, 9.63871685e-08, -0.0548002385, 9.94760612e-08, -0.998497367)
    elseif free == "Monkey" then
        CFrameQuest = CFrame.new(771.192871, 42.3243141, -1220.74805, -0.996942639, 2.59707669e-08, 0.0781369284, 2.55865924e-08, 1, -5.91784355e-09, -0.0781369284, -3.90049282e-09, -0.996942639)
    elseif free == "Monkey King" then
        CFrameQuest = CFrame.new(727.094971, 42.2545357, -1380.22131, -0.0418852083, 2.64795439e-08, 0.999122441, -2.36735005e-08, 1, -2.74952416e-08, -0.999122441, -2.48043701e-08, -0.0418852083)
    elseif free == "Snow Bandit" then
        CFrameQuest = CFrame.new(1507.57898, 102.05999, -290.12558, -0.998586833, -8.202373e-09, -0.0531440228, -1.01186872e-08, 1, 3.57898209e-08, 0.0531440228, 3.62769903e-08, -0.998586833)
    elseif free == "Bomb Man" or free == "Sand Man" or free == "Snow Bandit Leader" then
        CFrameQuest = nil
    end
end

-- ฟังก์ชัน AutoFarmMob
function AutoFarmMob()
    game:GetService('VirtualUser'):CaptureController()
    game:GetService('VirtualUser'):Button1Down(Vector2.new(1280, 672))
end

-- ฟังก์ชัน AutoFarmBoss
function AutoFarmBoss()
    -- นิยาม function No
    function No()
        for i, v in ipairs(workspace.Lives:GetChildren()) do
            if not game:GetService("Players"):GetPlayerFromCharacter(v) then -- if not player then
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

    -- นิยาม function TP
    function TP(CFramePosition)
        -- นิยามการเคลื่อนที่หรือทำงานที่ต้องการ
    end

    No()  -- เรียกใช้ function No()

    _G.p = t

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

-- สร้าง Fluent window
local Window = Fluent:CreateWindow({
    Title = "Xylo Hub",
    SubTitle = "by Sky",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true,
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl
})

-- เพิ่ม Tabs
local Tabs = {
    Farm = Window:AddTab({ Title = "General", Icon = "home" }),
    Skil = Window:AddTab({ Title = "Skills", Icon = "database-zap" }),
    TP = Window:AddTab({ Title = "Teleport", Icon = "fast-forward" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

-- เพิ่ม Dropdowns ใน Tab ที่ชื่อ "General"
Tabs.Farm:AddDropdown("Select Mob", {
    Title = "Select Mob",
    Values = {"ไม่เลือก", "Bandit", "Bandit Leader", "Clown Pirate", "Marine", "Monkey", "Monkey King", "Bomb Man", "Sand Man", "Snow Bandit", "Snow Bandit Leader"},
    Multi = false,
    Default = 1,
    Callback = function(v)
        free = v
    end
})

Tabs.Farm:AddDropdown("Select Boss", {
    Title = "Select Boss",
    Values = boss,
    Multi = false,
    Default = 1,
    Callback = function(v)
        Boss = v
    end
})

-- เพิ่ม Toggle ใน Tab ที่ชื่อ "General"
Tabs.Farm:AddToggle("Auto Farm Mob", {
    Title = "Auto Farm Mob", 
    Default = false, 
    Callback = function(S)
        _G.Farn = S
        spawn(function()
            while _G.Farn do 
                wait()
                pcall(function()
                    MonA()
                    for _,v in pairs(game:GetService("Workspace").Lives:GetChildren()) do
                        if v.Humanoid.DisplayName == MONName and v.Humanoid.Health > 0 then
                            v.HumanoidRootPart.Size = Vector3.new(10,10,10)
                            v.HumanoidRootPart.Transparency = 0.9
                            v.Humanoid.WalkSpeed = 0
                            v.Humanoid.JumpPower = 0
                            repeat task.wait()
                                AutoAttack()
                                TP(v.HumanoidRootPart.CFrame*CFrame.new(0,5,0)*CFrame.Angles(math.rad(-90),0,0))
                            until _G.Farn == false or v.Humanoid.Health <= 0
                        end
                    end
                end)
            end
        end)
    end
})

Tabs.Farm:AddToggle("Auto Farm Boss", {
    Title = "Auto Farm Boss", 
    Default = false, 
    Callback = function(t) 
        No()
        _G.p = t
        AutoFarmBoss()
    end
})

-- Ignore Theme Settings ของ SaveManager
SaveManager:IgnoreThemeSettings()
SaveManager:SetLibrary(Fluent)
SaveManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")
SaveManager:BuildConfigSection(Tabs.Settings)

-- เลือก Tab ที่ 1
Window:SelectTab(1)

-- Load Autoload Config ของ SaveManager
SaveManager:LoadAutoloadConfig()
