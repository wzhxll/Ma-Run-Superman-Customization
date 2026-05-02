local RunSequence = function()
    wait(0.5)

    -- 唯一的一个 local 声明，包含所有顶层局部变量
    local TweenService, RunService, CoreGui, LocalPlayer, ScreenGui, sound, MainContainer, LoaderFrame,
          KSPA_Text, KSPA_Grad, KsPa_Text, K_Grad, BanText, BanGrad,
          LogFrame, LogStroke, Content, List, AddUpdate, updateLabels, CloseBtn, rotate,
          sequence1, sequence2, logSequence, strokeSequence, finishClose

    -- 以下为原代码逻辑，去掉了所有 local 关键字，只保留赋值
    TweenService = game:GetService("TweenService")
    RunService = game:GetService("RunService")
    CoreGui = game:GetService("CoreGui")
    LocalPlayer = game:GetService("Players").LocalPlayer

    ScreenGui = Instance.new("ScreenGui")
    ScreenGui.Name = "ASE_Integrated_System"
    ScreenGui.IgnoreGuiInset = true
    pcall(function() ScreenGui.Parent = CoreGui end)
    if not ScreenGui.Parent then ScreenGui.Parent = LocalPlayer:WaitForChild("PlayerGui") end

    sound = Instance.new("Sound")
    sound.SoundId = "rbxassetid://1846396531"
    sound.Volume = 0.5
    sound.Looped = true
    sound.Parent = ScreenGui
    sound:Play()

    MainContainer = Instance.new("CanvasGroup")
    MainContainer.Size = UDim2.new(1, 0, 1, 0)
    MainContainer.BackgroundTransparency = 1
    MainContainer.GroupTransparency = 1
    MainContainer.Parent = ScreenGui

    LoaderFrame = Instance.new("Frame")
    LoaderFrame.Size = UDim2.new(1, 0, 1, 0)
    LoaderFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    LoaderFrame.BorderSizePixel = 0
    LoaderFrame.Parent = MainContainer

    KSPA_Text = Instance.new("TextLabel")
    KSPA_Text.Size = UDim2.new(0.5, 0, 0, 120)
    KSPA_Text.Position = UDim2.new(0, 0, 0.5, -60)
    KSPA_Text.Text = "马润超人"
    KSPA_Text.TextSize = 120
    KSPA_Text.Font = Enum.Font.GothamBold
    KSPA_Text.TextXAlignment = Enum.TextXAlignment.Right
    KSPA_Text.TextTransparency = 1
    KSPA_Text.TextColor3 = Color3.fromRGB(255, 255, 255)
    KSPA_Text.Parent = LoaderFrame

    KSPA_Grad = Instance.new("UIGradient")
    KSPA_Grad.Color = ColorSequence.new(Color3.fromRGB(230, 57, 124), Color3.fromRGB(26, 26, 29))
    KSPA_Grad.Rotation = 90
    KSPA_Grad.Parent = KSPA_Text

    KsPa_Text = Instance.new("TextLabel")
    KsPa_Text.Size = UDim2.new(0.5, 0, 0, 120)
    KsPa_Text.Position = UDim2.new(0.5, 10, 0.5, -60)
    KsPa_Text.Text = "  vip定制"
    KsPa_Text.TextSize = 120
    KsPa_Text.Font = Enum.Font.GothamBold
    KsPa_Text.TextXAlignment = Enum.TextXAlignment.Left
    KsPa_Text.TextTransparency = 1
    KsPa_Text.TextColor3 = Color3.fromRGB(255, 255, 255)
    KsPa_Text.Parent = LoaderFrame

    K_Grad = Instance.new("UIGradient")
    K_Grad.Color = ColorSequence.new(Color3.fromRGB(0, 0, 0), Color3.fromRGB(255, 255, 255))
    K_Grad.Rotation = 90
    K_Grad.Parent = KsPa_Text

    BanText = Instance.new("TextLabel")
    BanText.Size = UDim2.new(0.7, 0, 0, 70)
    BanText.Position = UDim2.new(0.5, 0, -0.15, 0)
    BanText.AnchorPoint = Vector2.new(0.5, 0.5)
    BanText.Text = "马润超人 定制版"
    BanText.TextSize = 70
    BanText.Font = Enum.Font.GothamBold
    BanText.TextColor3 = Color3.fromRGB(255, 255, 255)
    BanText.BackgroundTransparency = 1
    BanText.TextTransparency = 1
    BanText.Parent = LoaderFrame

    BanGrad = Instance.new("UIGradient")
    BanGrad.Color = ColorSequence.new(Color3.fromRGB(245, 239, 234), Color3.fromRGB(18, 46, 138))
    BanGrad.Rotation = 90
    BanGrad.Parent = BanText

    -- 移除了 SubBanText 和 SubBanGrad（空白文字）

    LogFrame = Instance.new("Frame")
    LogFrame.Size = UDim2.new(0, 100, 0, 100)
    LogFrame.Position = UDim2.new(0.5, -225, 0.5, -160)
    LogFrame.BackgroundColor3 = Color3.fromRGB(18, 46, 138)
    LogFrame.BackgroundTransparency = 1
    LogFrame.ClipsDescendants = true
    LogFrame.Parent = MainContainer
    Instance.new("UICorner", LogFrame).CornerRadius = UDim.new(0, 15)

    LogStroke = Instance.new("UIStroke")
    LogStroke.Thickness = 2
    LogStroke.Color = Color3.fromRGB(255, 255, 255)
    LogStroke.Transparency = 1
    LogStroke.Parent = LogFrame

    Content = Instance.new("ScrollingFrame")
    Content.Size = UDim2.new(1, -40, 1, -100)
    Content.Position = UDim2.new(0, 20, 0, 20)
    Content.BackgroundTransparency = 1
    Content.CanvasSize = UDim2.new(0, 0, 0, 0)
    Content.ScrollBarThickness = 0
    Content.Parent = LogFrame

    List = Instance.new("UIListLayout")
    List.Padding = UDim.new(0, 10)
    List.Parent = Content

    AddUpdate = function(msg)
        msg = msg or "未知消息"
        local t = Instance.new("TextLabel")
        t.Size = UDim2.new(1, 0, 0, 25)
        t.BackgroundTransparency = 1
        t.RichText = true
        t.Text = "» " .. tostring(msg)
        t.TextColor3 = Color3.fromRGB(245, 239, 234)
        t.TextSize = 16
        t.Font = Enum.Font.Ubuntu
        t.TextXAlignment = Enum.TextXAlignment.Left
        t.TextTransparency = 1
        t.Parent = Content
        task.defer(function()
            Content.CanvasSize = UDim2.new(0, 0, 0, List.AbsoluteContentSize.Y)
        end)
        return t
    end

    updateLabels = {
        AddUpdate("马润超人定制"),
        AddUpdate("传奇马润超人"),
        AddUpdate("快手马润超人"),
    }

    CloseBtn = Instance.new("TextButton")
    CloseBtn.Size = UDim2.new(0, 200, 0, 40)
    CloseBtn.Position = UDim2.new(0.5, -100, 1, -55)
    CloseBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    CloseBtn.BackgroundTransparency = 1
    CloseBtn.Text = "已阅读/进入"   -- 原为“马润超人”，已修改
    CloseBtn.TextColor3 = Color3.fromRGB(245, 239, 234)
    CloseBtn.Font = Enum.Font.GothamBold
    CloseBtn.TextSize = 14
    CloseBtn.TextTransparency = 1
    CloseBtn.Parent = LogFrame
    Instance.new("UICorner", CloseBtn).CornerRadius = UDim.new(0, 8)

    TweenService:Create(MainContainer, TweenInfo.new(0.8), {GroupTransparency = 0}):Play()
    task.wait(0.5)
    TweenService:Create(KSPA_Text, TweenInfo.new(1, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {TextTransparency = 0}):Play()
    TweenService:Create(KsPa_Text, TweenInfo.new(1, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out), {TextTransparency = 0}):Play()

    TweenService:Create(BanText, TweenInfo.new(1, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
        Position = UDim2.new(0.5, 0, 0.22, 0),
        TextTransparency = 0
    }):Play()
    -- 移除了 SubBanText 的动画

    rotate = RunService.RenderStepped:Connect(function()
        KSPA_Grad.Offset = Vector2.new(0, math.sin(tick()*2)*0.2)
        K_Grad.Offset = Vector2.new(0, -math.sin(tick()*2)*0.2)
        BanGrad.Offset = Vector2.new(0, math.sin(tick()*2)*0.2)
    end)

    task.wait(2)

    sequence1 = TweenService:Create(KSPA_Text, TweenInfo.new(1.2, Enum.EasingStyle.Exponential, Enum.EasingDirection.InOut), {
        Position = UDim2.new(-0.6, 0, 0.5, -60),
        TextTransparency = 1
    })
    sequence2 = TweenService:Create(KsPa_Text, TweenInfo.new(1.2, Enum.EasingStyle.Exponential, Enum.EasingDirection.InOut), {
        Position = UDim2.new(1.1, 0, 0.5, -60),
        TextTransparency = 1
    })
    sequence1:Play()
    sequence2:Play()
    TweenService:Create(LoaderFrame, TweenInfo.new(1.5, Enum.EasingStyle.Quart), {BackgroundTransparency = 1}):Play()
    task.wait(1.2)

    TweenService:Create(BanText, TweenInfo.new(0.8, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {
        Position = UDim2.new(0.5, 0, -0.25, 0),
        TextTransparency = 1
    }):Play()
    -- 移除了 SubBanText 的动画

    logSequence = TweenService:Create(LogFrame, TweenInfo.new(1, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
        BackgroundTransparency = 0.5,
        Size = UDim2.new(0, 450, 0, 320)
    })
    strokeSequence = TweenService:Create(LogStroke, TweenInfo.new(1), {Transparency = 0.8})
    logSequence:Play()
    strokeSequence:Play()
    task.wait(0.3)
    TweenService:Create(CloseBtn, TweenInfo.new(0.8, Enum.EasingStyle.Exponential), {
        BackgroundTransparency = 0.9,
        TextTransparency = 0
    }):Play()

    task.spawn(function()
        for i, obj in pairs(updateLabels) do
            TweenService:Create(obj, TweenInfo.new(0.5, Enum.EasingStyle.Quart), {TextTransparency = 0}):Play()
            task.wait(0.15)
        end
    end)

    -- 移除了付费宣传弹窗（paidPanel）的创建代码

    clicked = false
    CloseBtn.MouseButton1Click:Connect(function()
        if clicked then return end
        clicked = true
        finishClose = function()
            local closeTween = TweenService:Create(MainContainer, TweenInfo.new(0.5, Enum.EasingStyle.Back, Enum.EasingDirection.InOut), {
                Size = UDim2.new(0, 0, 0, 0),
                Position = UDim2.new(0.5, 0, 0.5, 0),
                GroupTransparency = 1
            })
            closeTween:Play()
            closeTween.Completed:Wait()
            rotate:Disconnect()
            sound:Stop()
            sound:Destroy()
            ScreenGui:Destroy()
        end
        finishClose()
    end)
    repeat task.wait() until clicked
end

RunSequence()

local WindUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/Footagesus/WindUI/main/dist/main.lua"))()

WindUI:Localization({
    Enabled = true,
    Prefix = "loc:",
    DefaultLanguage = "zh-cn",
    Translations = {
        ["ru"] = {
            ["WINDUI_EXAMPLE"] = "WindUI Пример",
            ["WELCOME"] = "Добро пожаловать в WindUI!",
            ["LIB_DESC"] = "Библиотека для создания красивых интерфейсов",
            ["SETTINGS"] = "Настройки",
            ["APPEARANCE"] = "Внешний вид",
            ["FEATURES"] = "Функционал",
            ["UTILITIES"] = "Инструменты",
            ["UI_ELEMENTS"] = "UI Элементы",
            ["CONFIGURATION"] = "Конфигурация",
            ["SAVE_CONFIG"] = "Сохранить конфигурацию",
            ["LOAD_CONFIG"] = "Загрузить конфигурацию",
            ["THEME_SELECT"] = "Выберите тему",
            ["TRANSPARENCY"] = "Прозрачность окна"
        },
        ["en"] = {
            ["WINDUI_EXAMPLE"] = "WindUI Example",
            ["WELCOME"] = "Welcome to WindUI!",
            ["LIB_DESC"] = "Beautiful UI library for Roblox",
            ["SETTINGS"] = "Settings",
            ["APPEARANCE"] = "Appearance",
            ["FEATURES"] = "Features",
            ["UTILITIES"] = "Utilities",
            ["UI_ELEMENTS"] = "UI Elements",
            ["CONFIGURATION"] = "Configuration",
            ["SAVE_CONFIG"] = "Save Configuration",
            ["LOAD_CONFIG"] = "Load Configuration",
            ["THEME_SELECT"] = "Select Theme",
            ["TRANSPARENCY"] = "Window Transparency"
        },
        ["zh-cn"] = {
            ["WINDUI_EXAMPLE"] = "WindUI 示例",
            ["WELCOME"] = "欢迎使用 WindUI！",
            ["LIB_DESC"] = "为 Roblox 设计的精美 UI 库",
            ["SETTINGS"] = "设置",
            ["APPEARANCE"] = "外观",
            ["FEATURES"] = "功能",
            ["UTILITIES"] = "工具",
            ["UI_ELEMENTS"] = "UI 元素",
            ["CONFIGURATION"] = "配置",
            ["SAVE_CONFIG"] = "保存配置",
            ["LOAD_CONFIG"] = "加载配置",
            ["THEME_SELECT"] = "选择主题",
            ["TRANSPARENCY"] = "窗口透明度"
        }
    }
})

WindUI.TransparencyValue = 0.2
WindUI:SetTheme("Indigo")

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local Workspace = game:GetService("Workspace")
local lp = Players.LocalPlayer
local camera = workspace.CurrentCamera
local pgui = lp:WaitForChild("PlayerGui")
local mouse = lp:GetMouse()

-- ==================== 功能文本全局存储表 G ====================
local G = {
    WindowTitle = "马润超人 定制版",
    WindowAuthor = "马润定制",
    TopbarTheme = "主题切换",
    SectionFeatures = "功能",
    SectionKill = "杀戮光环",
    SectionESP = "透视",
    SectionCareer = "职业功能",
    SectionOther = "其他",
    TabMain = "主要",
    TabAuto = "自动功能",
    TabFly = "飞行",
    TabBrush = "获取",
    TabKill = "光环",
    TabZombieESP = "僵尸透视",
    TabPlayerESP = "玩家透视",
    TabEngineer = "工兵",
    TabOfficer = "军官/线列",
    TabAutoShoot = "自动射击",
    TabDoctor = "医生",
    TabChaplain = "牧师",
    TabOther = "其它",
    ToggleSpeedTitle = "启用速度调整",
    ToggleSpeedDesc = "速度控制",
    SliderSpeedTitle = "玩家速度",
    SliderSpeedDesc = "调整移动速度",
    SliderAutoFaceRangeTitle = "自动转向范围",
    SliderAutoFaceRangeDesc = "僵尸进入距离时自动转向",
    ToggleAutoFaceTitle = "自动转向",
    ToggleAutoFaceDesc = "自动面向范围内的僵尸",
    ToggleSkipBarrelTitle = "跳过自爆僵尸",
    ToggleSkipBarrelDesc = "开启后不会转向自爆",
    ToggleAutoJumpTitle = "自动跳跃",
    ToggleAutoJumpDesc = "自动跳跃",
    SliderAutoJumpHeightTitle = "自动跳跃高度",
    SliderAutoJumpHeightDesc = "调节自动跳跃高度",
    ToggleJumpTitle = "无限连跳",
    ToggleJumpDesc = "无限跳跃，无视骨折",
    SliderJumpHeightTitle = "跳跃高度",
    SliderJumpHeightDesc = "调节跳跃高度",
    ToggleNoSlowTitle = "无减速",
    ToggleNoSlowDesc = "移除减速效果（重生后需重新开启）",
    ToggleNoFallTitle = "移除摔伤",
    ToggleNoFallDesc = "移除摔落伤害（注意不防骨折）",
    ToggleBackpackTitle = "显示物品栏",
    ToggleBackpackDesc = "强制显示物品栏",
    ToggleBrightTitle = "亮度提升",
    ToggleBrightDesc = "提高场景亮度",
    ToggleAutoDigTitle = "自动挖雪",
    ToggleAutoDigDesc = "自动挖掘雪堆",
    ToggleAutoLogTitle = "自动拿木头",
    ToggleAutoLogDesc = "自动拿木头",
    ToggleAutoPlaceTitle = "自动放置木头",
    ToggleAutoPlaceDesc = "自动放置收集到的木头",
    ToggleAutoRepairBridgeTitle = "自动修桥",
    ToggleAutoRepairBridgeDesc = "自动搭桥",
    ToggleAutoCollectTitle = "自动收集",
    ToggleAutoCollectDesc = "自动收集物品",
    ToggleAutoDoorTitle = "自动开门",
    ToggleAutoDoorDesc = "自动开门",
    ButtonFlyOriginalTitle = "飞行-无相机锁定",
    ButtonFlyNewTitle = "飞行-优化",
    ButtonGetBaguetteTitle = "获取法棍 (Baguette)",
    ButtonGetVoivodeTitle = "获取吸血鬼刀 (Voivode)",
    ButtonGetStakeTitle = "获取铁桩 (Iron Stake)",
    ButtonGetAllTitle = "获取所有武器并装备",
    ToggleAuraHighFreqTitle = "杀戮光环-高频（防封）",
    ToggleAuraHighFreqDesc = "高频杀戮体验极致爽感（防封）",
    ToggleAuraWaveTitle = "杀戮光环-无尽专用",
    ToggleAuraWaveDesc = "无尽专用防卡, 就是杀戮太慢了",
    ToggleAuraManualTitle = "杀戮光环-手动",
    ToggleAuraManualDesc = "挥刀时开启杀戮光环（防封）",
    ToggleAttackBarrelTitle = "攻击自爆",
    ToggleAttackBarrelDesc = "开启后攻击自爆",
    ToggleHeadshotTitle = "强制爆头",
    ToggleHeadshotDesc = "强制爆头",
    ToggleESPAxeTitle = "透视斧头僵尸",
    ToggleESPEyeTitle = "透视红眼",
    ToggleESPSwordTitle = "透视胸甲骑兵",
    ToggleESPBarrelTitle = "透视自爆",
    ToggleESPFTorsoTitle = "透视提灯人",
    ToggleESPNormalTitle = "透视山伯乐",
    TogglePlayerESPEnableTitle = "启用玩家透视",
    TogglePlayerESPEnableDesc = "开启后对玩家高亮",
    TogglePlayerESPNameTitle = "显示玩家名称",
    TogglePlayerESPNameDesc = "开启显示玩家用户名",
    TogglePlayerESPTeamTitle = "队伍检测",
    TogglePlayerESPTeamDesc = "开启后只高亮透视敌方队伍玩家",
    ToggleEngineerAutoRepairTitle = "自动修建筑",
    ToggleEngineerAutoRepairDesc = "自动修复建筑",
    ToggleEngineerRecycleTitle = "攻击回收",
    ToggleEngineerRecycleDesc = "攻击时自动回收武器来达到移除后摇的效果",
    ToggleEngineerElbowRangeTitle = "肘击范围扩大",
    ToggleEngineerElbowRangeDesc = "扩大肘击范围",
    ToggleEngineerElbowTitle = "肘击",
    ToggleEngineerElbowDesc = "自动肘击",
    ToggleOfficerReloadTitle = "自动换弹",
    ToggleOfficerReloadDesc = "自动换弹",
    ToggleOfficerBlackGunTitle = "自动黑枪",
    ToggleOfficerBlackGunDesc = "已自动为浮木购买无限名刀",
    ToggleOfficerJumpTitle = "自动跳刀",
    ToggleOfficerJumpDesc = "军刀前刺时自动跳跃",
    ToggleAutoShootBomberTitle = "自动射击自爆",
    ToggleAutoShootBomberDesc = "自动射击自爆",
    ToggleAutoShootCuirassierTitle = "自动射击胸甲骑兵",
    ToggleAutoShootCuirassierDesc = "自动射击胸甲骑兵",
    ToggleAutoShootRunnerTitle = "自动射击红眼",
    ToggleAutoShootRunnerDesc = "自动射击红眼",
    ToggleAutoShootElectrocutionerTitle = "自动射击斧头",
    ToggleAutoShootElectrocutionerDesc = "自动射击斧头",
    ToggleBombRangeTitle = "显示自爆有效伤害范围",
    ToggleBombRangeDesc = "显示自爆爆炸范围",
    ToggleFlyOffTitle = "半无敌［碰飞］",
    ToggleFlyOffDesc = "僵尸无法碰到你, 简称半无敌",
    TabPVP = "PVP",
    ToggleBayonetPVPTitle = "杀戮光环［刺刀］",
    ToggleBayonetPVPDesc = "开启秒变刺刀大蛇",
    ToggleMeleePVPTitle = "杀戮光环",
    ToggleMeleePVPDesc = "体验虐杀的快感",
    ToggleBarrelCollisionTitle = "无法攻击自爆",
    ToggleBarrelCollisionDesc = "无法攻击自爆",
    ToggleTeleportTitle = "启用点击传送",
    ToggleTeleportDesc = "开启后加载弹窗",
    ToggleDoctorTitle = "自动治疗受伤玩家",
    ToggleDoctorDesc = "自动向受伤玩家治疗",
    SliderDoctorThresholdTitle = "医疗阈值 (%)",
    SliderDoctorThresholdDesc = "自动治疗低于阀值玩家",
    ToggleChaplainTitle = "自动祝福感染玩家",
    ToggleChaplainDesc = "自动向感染玩家发送祝福",
    SliderChaplainThresholdTitle = "祝福阈值 (%)",
    SliderChaplainThresholdDesc = "感染值高于阀值自动祝福"
}

-- ==================== 将所有功能变量和函数封装到表 L 中 ====================
local L = {}

-- 新增独立攻击距离变量
L.auraRangeHighFreq = 45
L.auraRangeWave = 45
L.auraRangeManual = 45
L.chainKillRange = 45
L.customAuraEnabled = false
L.customAttackThread = nil
L.customAttackCount = 1
L.customAttackRange = 45
L.customAttackDelay = 0.005

L.chainAuraEnabled = false
L.chainAttackThread = nil

-- 自动黑枪配置变量（使用默认值，不再由滑块控制）
L.autoBlackGunSmoothTime = 0.28
L.autoBlackGunCooldown = 0.1
L.autoBlackGunEquipDelay = 0.2
L.autoBlackGunBarrelDistance = 14

-- 获取控制模块
L.ControlModule = require(lp.PlayerScripts:WaitForChild("PlayerModule")):GetControls()

-- 飞行-无相机锁定相关（新版本，由按钮动态加载，此处留空）
-- 飞行-优化相关（UI尺寸已调整）
L.bv_new = nil
L.bg_new = nil
L.animCache_new = nil
L.hrp_new = nil
L.hum_new = nil
L.isFlying_new = false
L.flySpeed_new = 40
L.isWallhack_new = false
L.flyTurner_new = nil
L.originalCollisions_new = {}

function L.getBodyParts(character)
    local parts = {}
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    if humanoid then
        local success, rigParts = pcall(function() return humanoid:GetRigParts() end)
        if success and rigParts then
            for _, part in ipairs(rigParts) do
                if part:IsA("BasePart") then
                    table.insert(parts, part)
                end
            end
        end
    end
    if #parts == 0 then
        local bodyNames = {"Head", "Torso", "UpperTorso", "LowerTorso", "HumanoidRootPart",
                           "Left Arm", "Right Arm", "Left Leg", "Right Leg",
                           "LeftUpperArm", "LeftLowerArm", "RightUpperArm", "RightLowerArm",
                           "LeftUpperLeg", "LeftLowerLeg", "RightUpperLeg", "RightLowerLeg"}
        for _, name in ipairs(bodyNames) do
            local part = character:FindFirstChild(name)
            if part and part:IsA("BasePart") then
                table.insert(parts, part)
            end
        end
    end
    return parts
end

L.SmoothTurner = {}
L.SmoothTurner.__index = L.SmoothTurner

function L.SmoothTurner.new(rootPart, camera, options)
    options = options or {}
    local self = setmetatable({}, L.SmoothTurner)
    self.RootPart = rootPart
    self.Camera = camera or workspace.CurrentCamera
    self.Enabled = false
    self.BodyGyro = nil
    self.P = options.P or 10000
    self.D = options.D or 50
    self.MaxTorque = options.MaxTorque or Vector3.new(math.huge, math.huge, math.huge)
    return self
end

function L.SmoothTurner:Start()
    if self.Enabled then return end
    if not self.RootPart or not self.RootPart.Parent then return end
    local gyro = Instance.new("BodyGyro")
    gyro.MaxTorque = self.MaxTorque
    gyro.P = self.P
    gyro.D = self.D
    gyro.CFrame = self.RootPart.CFrame
    gyro.Parent = self.RootPart
    self.BodyGyro = gyro
    self.Enabled = true
    self:_startHeartbeat()
end

function L.SmoothTurner:Stop()
    if self.BodyGyro then
        self.BodyGyro:Destroy()
        self.BodyGyro = nil
    end
    self.Enabled = false
    if self.HeartbeatConn then
        self.HeartbeatConn:Disconnect()
        self.HeartbeatConn = nil
    end
end

function L.SmoothTurner:SetDirection(direction)
    if not self.Enabled or not self.BodyGyro or not self.RootPart then return end
    local newCFrame = CFrame.lookAt(self.RootPart.Position, self.RootPart.Position + direction.Unit)
    self.BodyGyro.CFrame = newCFrame
end

function L.SmoothTurner:_startHeartbeat()
    if self.HeartbeatConn then self.HeartbeatConn:Disconnect() end
    self.HeartbeatConn = RunService.Heartbeat:Connect(function()
        if not self.Enabled or not self.BodyGyro or not self.RootPart or not self.Camera then return end
        local look = self.Camera.CFrame.LookVector
        self:SetDirection(look)
    end)
end

function L.SmoothTurner:Destroy()
    self:Stop()
    self.RootPart = nil
    self.Camera = nil
end

function L.clearFlyRes_new()
    local char = lp.Character
    if char then
        local bodyParts = L.getBodyParts(char)
        for part, originalState in pairs(L.originalCollisions_new) do
            if part and part.Parent then
                for _, bp in ipairs(bodyParts) do
                    if bp == part then
                        part.CanCollide = originalState
                        break
                    end
                end
            end
        end
        L.originalCollisions_new = {}
    end
    if L.animCache_new and lp.Character then L.animCache_new.Parent = lp.Character end
    if L.bv_new then L.bv_new:Destroy() end
    if L.bg_new then L.bg_new:Destroy() end
    L.bv_new, L.bg_new = nil, nil
    if L.flyTurner_new then L.flyTurner_new:Destroy(); L.flyTurner_new = nil end
    if L.hum_new and L.hum_new.Parent then L.hum_new:ChangeState(Enum.HumanoidStateType.Running) end
end

function L.ensurePhysics_new(hrp, useGyro)
    if hrp:FindFirstChild("LeipzigBV_new") then hrp.LeipzigBV_new:Destroy() end
    if hrp:FindFirstChild("LeipzigBG_new") then hrp.LeipzigBG_new:Destroy() end
    L.bv_new = Instance.new("BodyVelocity", hrp)
    L.bv_new.Name = "LeipzigBV_new"
    L.bv_new.MaxForce = Vector3.new(1e6, 1e6, 1e6)
    if useGyro then
        if L.flyTurner_new then L.flyTurner_new:Destroy() end
        L.flyTurner_new = L.SmoothTurner.new(hrp, workspace.CurrentCamera)
        L.flyTurner_new:Start()
    end
end

function L.applyWallhackState_new()
    local char = lp.Character
    if not char then return end
    if L.isWallhack_new then
        local bodyParts = L.getBodyParts(char)
        L.originalCollisions_new = {}
        for _, part in ipairs(bodyParts) do
            L.originalCollisions_new[part] = part.CanCollide
            part.CanCollide = false
        end
    else
        for part, originalState in pairs(L.originalCollisions_new) do
            if part and part.Parent then
                part.CanCollide = originalState
            end
        end
        L.originalCollisions_new = {}
    end
end

function L.startFlyNormal_new()
    local char = lp.Character
    if not char then return end
    L.hrp_new = char:WaitForChild("HumanoidRootPart")
    L.hum_new = char:WaitForChild("Humanoid")
    local ani = char:FindFirstChild("Animate")
    if ani then L.animCache_new = ani; ani.Parent = nil end
    L.ensurePhysics_new(L.hrp_new, true)
    task.spawn(function()
        while L.isFlying_new and char.Parent do
            local mv = L.ControlModule:GetMoveVector()
            local cf = camera.CFrame
            local dir = (cf.LookVector * -mv.Z) + (cf.RightVector * mv.X)
            if mv.Magnitude > 0 then
                L.bv_new.Velocity = dir.Unit * L.flySpeed_new
            else
                L.bv_new.Velocity = Vector3.new(0,0.01,0)
            end
            L.hum_new:ChangeState(Enum.HumanoidStateType.Climbing)
            RunService.RenderStepped:Wait()
        end
        L.clearFlyRes_new()
    end)
end

function L.startFlyWallhack_new()
    local char = lp.Character
    if not char then return end
    L.hrp_new = char:WaitForChild("HumanoidRootPart")
    L.hum_new = char:WaitForChild("Humanoid")
    local ani = char:FindFirstChild("Animate")
    if ani then L.animCache_new = ani; ani.Parent = nil end
    L.applyWallhackState_new()
    L.ensurePhysics_new(L.hrp_new, true)
    task.spawn(function()
        local lastPos = L.hrp_new.Position
        local lastTime = tick()
        while L.isFlying_new and char.Parent do
            local dt = tick() - lastTime
            lastTime = tick()
            local mv = L.ControlModule:GetMoveVector()
            local cf = camera.CFrame
            local dir = (cf.LookVector * -mv.Z) + (cf.RightVector * mv.X)
            local targetVelocity
            if mv.Magnitude > 0 then
                targetVelocity = dir.Unit * L.flySpeed_new
                L.bv_new.Velocity = targetVelocity
            else
                L.bv_new.Velocity = Vector3.new(0,0.01,0)
                targetVelocity = Vector3.new(0,0.01,0)
            end
            L.hum_new:ChangeState(Enum.HumanoidStateType.Climbing)
            RunService.RenderStepped:Wait()
            local expectedPos = lastPos + targetVelocity * dt
            local actualPos = L.hrp_new.Position
            local deviation = actualPos - expectedPos
            if deviation.Magnitude > 0.00001 then
                L.hrp_new.CFrame = CFrame.new(expectedPos) * L.hrp_new.CFrame.Rotation
                L.bv_new.Velocity = targetVelocity
                lastPos = expectedPos
            else
                lastPos = actualPos
            end
        end
        L.clearFlyRes_new()
    end)
end

function L.startFly_new()
    if L.isFlying_new then return end
    L.isFlying_new = true
    if L.isWallhack_new then
        L.startFlyWallhack_new()
    else
        L.startFlyNormal_new()
    end
end

function L.stopFly_new()
    if not L.isFlying_new then return end
    L.isFlying_new = false
    L.clearFlyRes_new()
end

function L.bindCharacter_new()
    local char = lp.Character or lp.CharacterAdded:Wait()
    L.hrp_new = char:WaitForChild("HumanoidRootPart")
    L.hum_new = char:WaitForChild("Humanoid")
    L.clearFlyRes_new()
    char.AncestryChanged:Connect(function(_, parent)
        if not parent then
            L.clearFlyRes_new()
            L.bindCharacter_new()
        end
    end)
end
L.bindCharacter_new()

-- 渐变文字辅助函数
local function gradient(text, startColor, endColor)
    local result = ""
    for i = 1, #text do
        local t = (i - 1) / (#text - 1)
        local r = math.floor((startColor.R + (endColor.R - startColor.R) * t) * 255)
        local g = math.floor((startColor.G + (endColor.G - startColor.G) * t) * 255)
        local b = math.floor((startColor.B + (endColor.B - startColor.B) * t) * 255)
        result = result .. string.format('<font color="rgb(%d,%d,%d)">%s</font>', r, g, b, text:sub(i, i))
    end
    return result
end

WindUI:Popup({
    Title = gradient("WindUI 演示", Color3.fromHex("#6A11CB"), Color3.fromHex("#2575FC")),
    Icon = "sparkles",
    Content = "loc:LIB_DESC",
    Buttons = {
        {
            Title = "开始使用",
            Icon = "arrow-right",
            Variant = "Primary",
            Callback = function() end
        }
    }
})

local Window = WindUI:CreateWindow({
    Title = G.WindowTitle,
    Icon = "https://...",
    Author = G.WindowAuthor,
    Folder = "WindUI_Example",
    Size = UDim2.fromOffset(650, 450),
    Theme = "Indigo",
    Background = "https://chaton-images.s3.us-east-2.amazonaws.com/1wXChVOd7zROLvHhCUkWeUu4MCc40cVOgd4uzeCg9WU5mAHPPSpAOwI0N1f9IIE4_1147x747x57511.jpeg",
    User = {
        Enabled = true,
        Name = "马润超人",
        Anonymous = false,
        Callback = function()
            WindUI:Notify({
                Title = "用户资料",
                Content = "我操你妈",
                Duration = 3
            })
        end
    },
    SideBarWidth = 220,
    ScrollBarEnabled = true
})

-- 这里添加背景图透明度代码
Window:SetBackgroundImageTransparency(0.4)   -- 数值 0~1，0为完全不透明，1为完全透明

Window:Tag({
    Title = "马润定制",
    Color = Color3.fromHex("#30ff6a")
})

-- 其余代码保持不变...

Window:CreateTopbarButton("theme-switcher", "moon", function()
    WindUI:SetTheme(WindUI:GetCurrentTheme() == "Indigo" and "Dark" or "Indigo")
    WindUI:Notify({
        Title = "主题已更改",
        Content = "当前主题："..WindUI:GetCurrentTheme(),
        Duration = 2
    })
end, 990)

-- ==================== 功能 ====================
local FeatureSection = Window:Section({ Title = G.SectionFeatures, Opened = false })
local MainTab = FeatureSection:Tab({ Title = G.TabMain, Icon = "zap" })

-- ==================== 坐标加速（新增） ====================
local coordSpeedEnabled = false
local coordSpeedValue = 16
local coordSpeedConn = nil

local function startCoordSpeed()
    if coordSpeedConn then return end
    coordSpeedConn = RunService.Heartbeat:Connect(function(dt)
        if not coordSpeedEnabled then return end
        local char = lp.Character
        if not char then return end
        local hrp = char:FindFirstChild("HumanoidRootPart")
        local hum = char:FindFirstChild("Humanoid")
        if not hrp or not hum then return end
        local moveDir = hum.MoveDirection
        if moveDir.Magnitude > 0 then
            hrp.CFrame = hrp.CFrame + moveDir.Unit * coordSpeedValue * dt
        end
    end)
end

local function stopCoordSpeed()
    if coordSpeedConn then
        coordSpeedConn:Disconnect()
        coordSpeedConn = nil
    end
end

local function setCoordSpeedEnabled(state)
    coordSpeedEnabled = state
    if state then
        startCoordSpeed()
    else
        stopCoordSpeed()
    end
end

local function setCoordSpeedValue(value)
    coordSpeedValue = math.clamp(value, 1, 35)
end

MainTab:Toggle({
    Title = "启用坐标加速",
    Desc = "控制移动",
    Value = false,
    Callback = function(state)
        setCoordSpeedEnabled(state)
    end
})

MainTab:Slider({
    Title = "坐标加速速度",
    Desc = "调整坐标移动速度",
    Value = { Min = 1, Max = 35, Default = 16 },
    Callback = function(value)
        setCoordSpeedValue(value)
    end
})

MainTab:Divider()

-- ==================== 新速度控制模块（循环锁定，关闭恢复默认16） ====================
local speedEnabled = false
local desiredSpeed = 25
local speedHeartbeatConn = nil
local speedHumPropConns = {}

local function safeSetWalk(hum, sp)
    if hum and hum.Parent then pcall(function() hum.WalkSpeed = sp end) end
end

local function onWalkSpeedChanged(hum)
    return hum:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
        if speedEnabled then safeSetWalk(hum, desiredSpeed) end
    end)
end

local function attachToCharacter(char)
    if not char then return end
    local hum = char:FindFirstChildOfClass("Humanoid")
    if hum then
        if speedHumPropConns[hum] then speedHumPropConns[hum]:Disconnect() end
        speedHumPropConns[hum] = onWalkSpeedChanged(hum)
        safeSetWalk(hum, desiredSpeed)
    end
end

local function startSpeedLoop()
    if speedHeartbeatConn then return end
    speedHeartbeatConn = RunService.Heartbeat:Connect(function()
        if not speedEnabled then return end
        local char = lp.Character
        if char then
            local hum = char:FindFirstChildOfClass("Humanoid")
            if hum then
                safeSetWalk(hum, desiredSpeed)
                if not speedHumPropConns[hum] then
                    speedHumPropConns[hum] = onWalkSpeedChanged(hum)
                end
            end
        end
    end)
end

local function stopSpeedLoop()
    if speedHeartbeatConn then
        speedHeartbeatConn:Disconnect()
        speedHeartbeatConn = nil
    end
    for hum, conn in pairs(speedHumPropConns) do
        pcall(function() conn:Disconnect() end)
    end
    speedHumPropConns = {}
    local char = lp.Character
    if char then
        local hum = char:FindFirstChildOfClass("Humanoid")
        if hum then safeSetWalk(hum, 16) end
    end
end

function setWalkSpeedEnabled(state)
    speedEnabled = state
    if state then
        startSpeedLoop()
        if lp.Character then attachToCharacter(lp.Character) end
    else
        stopSpeedLoop()
    end
end

function setWalkSpeedValue(speed)
    desiredSpeed = math.clamp(speed, 16, 45)
    if speedEnabled then
        local char = lp.Character
        if char then
            local hum = char:FindFirstChildOfClass("Humanoid")
            if hum then safeSetWalk(hum, desiredSpeed) end
        end
    end
end

lp.CharacterAdded:Connect(function(char)
    if speedEnabled then
        task.wait(0.1)
        attachToCharacter(char)
    end
end)

-- 原有的无限连跳等变量保留
L.jumpHeight = 60
L.cooldown = 0.6
L.lastJump = 0
L.jumpModEnabled = false

UserInputService.JumpRequest:Connect(function()
    if not L.jumpModEnabled then return end
    local char = lp.Character
    local hum = char and char:FindFirstChildOfClass("Humanoid")
    local root = char and char:FindFirstChild("HumanoidRootPart")
    if hum and root and tick() - L.lastJump >= L.cooldown then
        L.lastJump = tick()
        hum:ChangeState(Enum.HumanoidStateType.Jumping)
        root.Velocity = Vector3.new(root.Velocity.X, L.jumpHeight, root.Velocity.Z)
    end
end)

RunService.RenderStepped:Connect(function()
    if not L.jumpModEnabled then return end
    local char = lp.Character
    local hum = char and char:FindFirstChildOfClass("Humanoid")
    local root = char and char:FindFirstChild("HumanoidRootPart")
    if hum and root then
        local userStates = lp:FindFirstChild("UserStates")
        if userStates then
            for _, s in pairs({"BrokenLegs", "Grabbed", "Pin"}) do
                if userStates:FindFirstChild(s) then userStates[s].Value = false end
            end
        end
        local animate = char:FindFirstChild("Animate")
        if animate then animate.Parent = nil end
        if root.Velocity.Y < -5 and not UserInputService:IsKeyDown(Enum.KeyCode.Space) then
            hum:ChangeState(Enum.HumanoidStateType.Climbing)
        end
    end
end)

L.antiFallEnabled = false
L.antiFallConnection = nil
L.fallStartY = nil
local FALL_DISTANCE_THRESHOLD = 15
local ANTI_FALL_JUMP_HEIGHT = 25

function L.startAntiFall()
    if L.antiFallConnection then L.antiFallConnection:Disconnect() end
    L.antiFallConnection = RunService.Heartbeat:Connect(function()
        if not L.antiFallEnabled then return end
        local char = lp.Character
        if not char then L.fallStartY = nil; return end
        local root = char:FindFirstChild("HumanoidRootPart")
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if not root or not humanoid then return end
        local currentY = root.Position.Y
        local velocityY = root.Velocity.Y
        if velocityY < -0.1 then
            if not L.fallStartY then
                L.fallStartY = currentY
            else
                local fallDistance = L.fallStartY - currentY
                if fallDistance >= FALL_DISTANCE_THRESHOLD then
                    humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
                    root.Velocity = Vector3.new(root.Velocity.X, ANTI_FALL_JUMP_HEIGHT, root.Velocity.Z)
                    L.fallStartY = nil
                end
            end
        else
            L.fallStartY = nil
        end
    end)
end

function L.stopAntiFall()
    if L.antiFallConnection then L.antiFallConnection:Disconnect() end
    L.antiFallConnection = nil
    L.fallStartY = nil
end

lp.CharacterAdded:Connect(function()
    L.stopAntiFall()
    L.fallStartY = nil
end)

-- 速度控制 UI（原有的行走速度调整）
MainTab:Toggle({
    Title = G.ToggleSpeedTitle,
    Desc = G.ToggleSpeedDesc,
    Value = false,
    Callback = function(state)
        setWalkSpeedEnabled(state)
    end
})

MainTab:Slider({
    Title = G.SliderSpeedTitle,
    Desc = G.SliderSpeedDesc,
    Value = { Min = 16, Max = 45, Default = 25 },
    Callback = function(value)
        setWalkSpeedValue(value)
    end
})
MainTab:Divider()

-- 以下为原有自动转向等代码，保持不变
L.autoFaceEnabled = false
L.autoFaceRange = 17
L.skipBarrel = false
L.autoFaceConnection = nil

function L.getNearestZombieInRange()
    local char = lp.Character
    if not char then return nil end
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return nil end
    local playerPos = root.Position

    local nearest = nil
    local nearestDist = math.huge
    local zombiesFolder = workspace:FindFirstChild("Zombies")
    if zombiesFolder then
        for _, zombie in pairs(zombiesFolder:GetChildren()) do
            if zombie:IsA("Model") and zombie:FindFirstChild("HumanoidRootPart") then
                if L.skipBarrel and zombie:GetAttribute("Type") == "Barrel" then
                    continue
                end
                local state = zombie:FindFirstChild("State")
                if state and state.Value == "Spawn" then
                    continue
                end
                local targetRoot = zombie.HumanoidRootPart
                local dist = (targetRoot.Position - playerPos).Magnitude
                if dist <= L.autoFaceRange and dist < nearestDist then
                    nearestDist = dist
                    nearest = zombie
                end
            end
        end
    end
    return nearest
end

function L.faceZombie(zombie)
    if not zombie or not zombie:FindFirstChild("HumanoidRootPart") then return end
    local char = lp.Character
    if not char then return end
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end

    local wasAutoRotate = humanoid.AutoRotate
    humanoid.AutoRotate = false

    local targetPos = zombie.HumanoidRootPart.Position
    local lookAtPos = Vector3.new(targetPos.X, root.Position.Y, targetPos.Z)
    root.CFrame = CFrame.lookAt(root.Position, lookAtPos)

    humanoid.AutoRotate = wasAutoRotate
end

function L.autoFaceLoop()
    while L.autoFaceEnabled do
        local target = L.getNearestZombieInRange()
        if target then
            L.faceZombie(target)
        end
        task.wait(0.1)
    end
end

function L.startAutoFace()
    if L.autoFaceConnection then
        task.cancel(L.autoFaceConnection)
        L.autoFaceConnection = nil
    end
    if L.autoFaceEnabled then
        L.autoFaceConnection = task.spawn(L.autoFaceLoop)
    end
end

function L.stopAutoFace()
    if L.autoFaceConnection then
        task.cancel(L.autoFaceConnection)
        L.autoFaceConnection = nil
    end
end

lp.CharacterAdded:Connect(function()
    if L.autoFaceEnabled then
        L.stopAutoFace()
        L.startAutoFace()
    end
end)

MainTab:Slider({
    Title = G.SliderAutoFaceRangeTitle,
    Desc = G.SliderAutoFaceRangeDesc,
    Value = { Min = 5, Max = 30, Default = 17 },
    Callback = function(value)
        L.autoFaceRange = value
    end
})

MainTab:Toggle({
    Title = G.ToggleAutoFaceTitle,
    Desc = G.ToggleAutoFaceDesc,
    Value = false,
    Callback = function(state)
        L.autoFaceEnabled = state
        if state then
            L.startAutoFace()
        else
            L.stopAutoFace()
        end
    end
})

MainTab:Toggle({
    Title = G.ToggleSkipBarrelTitle,
    Desc = G.ToggleSkipBarrelDesc,
    Value = false,
    Callback = function(state)
        L.skipBarrel = state
    end
})

MainTab:Divider()

L.autoJumpEnabled = false
L.autoJumpHeight = 60
L.autoJumpConn = nil

function L.startAutoJump()
    if L.autoJumpConn then return end
    L.autoJumpConn = RunService.Heartbeat:Connect(function()
        if not L.autoJumpEnabled then return end
        local char = lp.Character
        if not char then return end
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        local root = char:FindFirstChild("HumanoidRootPart")
        if not humanoid or not root then return end
        local onGround = humanoid.FloorMaterial ~= Enum.Material.Air
        if onGround then
            humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
            root.Velocity = Vector3.new(root.Velocity.X, L.autoJumpHeight, root.Velocity.Z)
        end
    end)
end

function L.stopAutoJump()
    if L.autoJumpConn then
        L.autoJumpConn:Disconnect()
        L.autoJumpConn = nil
    end
end

MainTab:Toggle({
    Title = G.ToggleAutoJumpTitle,
    Desc = G.ToggleAutoJumpDesc,
    Value = false,
    Callback = function(state)
        L.autoJumpEnabled = state
        if state then
            L.startAutoJump()
        else
            L.stopAutoJump()
        end
    end
})

MainTab:Slider({
    Title = G.SliderAutoJumpHeightTitle,
    Desc = G.SliderAutoJumpHeightDesc,
    Value = { Min = 30, Max = 60, Default = 60 },
    Callback = function(value)
        L.autoJumpHeight = value
    end
})

MainTab:Divider()

MainTab:Toggle({
    Title = G.ToggleJumpTitle,
    Desc = G.ToggleJumpDesc,
    Value = false,
    Callback = function(state)
        L.jumpModEnabled = state
        L.antiFallEnabled = state
        if state then L.startAntiFall() else L.stopAntiFall() end
        WindUI:Notify({ Title = G.ToggleJumpTitle, Content = state and "已开启（含防骨折）" or "已关闭", Duration = 2 })
    end
})

MainTab:Slider({
    Title = G.SliderJumpHeightTitle,
    Desc = G.SliderJumpHeightDesc,
    Value = { Min = 30, Max = 90, Default = 60 },
    Callback = function(value) L.jumpHeight = value end
})

MainTab:Divider()

L.minorFeatures = {}
L.minorFeatures.noSlow = { active = false, walkSpeedConn = nil, charAddedConn = nil }
function L.setupNoSlow()
    if not lp.Character then return end
    local humanoid = lp.Character:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end
    if L.minorFeatures.noSlow.walkSpeedConn then L.minorFeatures.noSlow.walkSpeedConn:Disconnect() end
    L.minorFeatures.noSlow.walkSpeedConn = humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
        if L.minorFeatures.noSlow.active and humanoid.WalkSpeed < 16 then
            humanoid.WalkSpeed = 16
        end
    end)
    if L.minorFeatures.noSlow.active and humanoid.WalkSpeed < 16 then
        humanoid.WalkSpeed = 16
    end
end
MainTab:Toggle({
    Title = G.ToggleNoSlowTitle,
    Desc = G.ToggleNoSlowDesc,
    Value = false,
    Callback = function(state)
        L.minorFeatures.noSlow.active = state
        if state then
            L.setupNoSlow()
            L.minorFeatures.noSlow.charAddedConn = lp.CharacterAdded:Connect(function()
                task.wait(1); L.setupNoSlow()
            end)
        else
            if L.minorFeatures.noSlow.walkSpeedConn then L.minorFeatures.noSlow.walkSpeedConn:Disconnect() end
            if L.minorFeatures.noSlow.charAddedConn then L.minorFeatures.noSlow.charAddedConn:Disconnect() end
        end
    end
})
L.minorFeatures.noFall = { active = false, connection = nil }
function L.preventFallDamage()
    while L.minorFeatures.noFall.active do
        if not lp.Character then task.wait(1) continue end
        local health = lp.Character:FindFirstChild("Health")
        if health then
            local forceSelfDamage = health:FindFirstChild("ForceSelfDamage")
            if forceSelfDamage then forceSelfDamage:FireServer(0) end
        end
        task.wait(1)
    end
end
MainTab:Toggle({
    Title = G.ToggleNoFallTitle,
    Desc = G.ToggleNoFallDesc,
    Value = false,
    Callback = function(state)
        L.minorFeatures.noFall.active = state
        if state then
            L.minorFeatures.noFall.connection = task.spawn(L.preventFallDamage)
        else
            if L.minorFeatures.noFall.connection then task.cancel(L.minorFeatures.noFall.connection) end
        end
    end
})

L.backpackToggleConn = nil
MainTab:Toggle({
    Title = G.ToggleBackpackTitle,
    Desc = G.ToggleBackpackDesc,
    Value = false,
    Callback = function(state)
        if state then
            local backpackGui = lp:WaitForChild("PlayerGui"):WaitForChild("BackpackGui")
            backpackGui.Enabled = true
            L.backpackToggleConn = backpackGui:GetPropertyChangedSignal("Enabled"):Connect(function()
                if not backpackGui.Enabled then
                    backpackGui.Enabled = true
                end
            end)
        else
            if L.backpackToggleConn then L.backpackToggleConn:Disconnect() end
        end
    end
})

L.originalLighting = nil
L.brightEnabled = false
MainTab:Toggle({
    Title = G.ToggleBrightTitle,
    Desc = G.ToggleBrightDesc,
    Value = false,
    Callback = function(state)
        local lighting = game:GetService("Lighting")
        if state then
            if not L.originalLighting then
                L.originalLighting = {
                    ClockTime = lighting.ClockTime,
                    Ambient = lighting.Ambient,
                    GlobalShadows = lighting.GlobalShadows,
                    OutdoorAmbient = lighting.OutdoorAmbient
                }
            end
            lighting.ClockTime = 14
            lighting.Ambient = Color3.fromRGB(255,255,255)
            lighting.GlobalShadows = false
            lighting.OutdoorAmbient = Color3.fromRGB(255,255,255)
            L.brightEnabled = true
        else
            if L.originalLighting then
                lighting.ClockTime = L.originalLighting.ClockTime
                lighting.Ambient = L.originalLighting.Ambient
                lighting.GlobalShadows = L.originalLighting.GlobalShadows
                lighting.OutdoorAmbient = L.originalLighting.OutdoorAmbient
            end
            L.brightEnabled = false
        end
    end
})

MainTab:Divider()

L.autoDoorEnabled = false
L.processingDoors = {}
L.autoDoorThread = nil
function L.autoDoorLoop()
    while L.autoDoorEnabled do
        local char = lp.Character
        local root = char and char:FindFirstChild("HumanoidRootPart")
        if root then
            for _, item in pairs(Workspace:GetDescendants()) do
                if item.Name == "Main" and item:IsA("Model") then
                    if (root.Position - item:GetModelCFrame().Position).Magnitude <= 23 then
                        local isOpen = item:GetAttribute("Open")
                        if isOpen == nil then pcall(function() isOpen = item.Open end) end
                        if isOpen == false then
                            local mainPart = item:FindFirstChild("Main")
                            local remote = mainPart and mainPart:FindFirstChild("Interact")
                            if remote and remote:IsA("RemoteEvent") and not L.processingDoors[item] then
                                L.processingDoors[item] = true
                                task.spawn(function()
                                    remote:FireServer()
                                    task.wait(0.5)
                                    L.processingDoors[item] = nil
                                end)
                            end
                        end
                    end
                end
            end
        end
        task.wait(0.1)
    end
end

local AutoTab = FeatureSection:Tab({ Title = G.TabAuto, Icon = "zap" })
L.autoFeatures = {}

L.autoFeatures.autoDig = { active = false, connection = nil }
local DIGGABLE_PATHS = {
    "Vardohus Fortress/Modes/Objective/DoorSnow/Diggable",
    "Vardohus Fortress/Modes/Objective/Diggable",
    "OLD Vardohus Fortress/Modes/Objective/DigSnow/Diggable"
}
function L.getDiggingTool()
    local char = lp.Character
    if not char then return nil end
    for _, tool in pairs(char:GetChildren()) do
        if (tool.Name == "Shovel" or tool.Name == "Spade") and tool:FindFirstChild("RemoteEvent") then return tool end
    end
    for _, tool in pairs(lp.Backpack:GetChildren()) do
        if (tool.Name == "Shovel" or tool.Name == "Spade") and tool:FindFirstChild("RemoteEvent") then return tool end
    end
    return nil
end
function L.findValidDiggable()
    for _, path in ipairs(DIGGABLE_PATHS) do
        local parts = path:split("/")
        local current = workspace
        for _, partName in ipairs(parts) do
            current = current:FindFirstChild(partName)
            if not current then break end
        end
        if current then return current end
    end
    return nil
end
function L.executeDig()
    if not L.autoFeatures.autoDig.active then return end
    local diggable = L.findValidDiggable()
    if not diggable then return end
    local tool = L.getDiggingTool()
    if not tool then return end
    if tool.Parent ~= lp.Character then tool.Parent = lp.Character; task.wait(0.2) end
    local remoteEvent = tool:FindFirstChild("RemoteEvent")
    if remoteEvent then remoteEvent:FireServer("Dig", diggable, diggable.Position) end
end
function L.autoDigLoop()
    while L.autoFeatures.autoDig.active do
        L.executeDig()
        task.wait(0.05)
    end
end
AutoTab:Toggle({
    Title = G.ToggleAutoDigTitle,
    Desc = G.ToggleAutoDigDesc,
    Value = false,
    Callback = function(state)
        L.autoFeatures.autoDig.active = state
        if state then L.autoFeatures.autoDig.connection = task.spawn(L.autoDigLoop)
        else if L.autoFeatures.autoDig.connection then task.cancel(L.autoFeatures.autoDig.connection) end end
    end
})

-- 注意：自动拿木头、自动放置木头、自动修桥这三个功能已从AutoTab移除，移动到UnknownTab中
-- 这里保留功能代码（L.autoFeatures.autoLog等），但UI控件已删除，将在UnknownTab中添加

L.autoFeatures.autoCollectKaub = { active = false, connection = nil, prompts = {} }
function L.setupKaubAutoCollect()
    for _, descendant in ipairs(workspace:GetDescendants()) do
        if descendant:IsA("ProximityPrompt") then L.autoFeatures.autoCollectKaub.prompts[descendant] = true end
    end
    local descendantAddedConn = workspace.DescendantAdded:Connect(function(desc)
        if desc:IsA("ProximityPrompt") then L.autoFeatures.autoCollectKaub.prompts[desc] = true end
    end)
    L.autoFeatures.autoCollectKaub.connection = RunService.Heartbeat:Connect(function()
        if not L.autoFeatures.autoCollectKaub.active or not lp.Character then return end
        local hrp = lp.Character:FindFirstChild("HumanoidRootPart")
        if not hrp then return end
        for prompt, _ in pairs(L.autoFeatures.autoCollectKaub.prompts) do
            if prompt and prompt.Parent and prompt:IsA("ProximityPrompt") and prompt.Enabled then
                local part = prompt.Parent
                if part:IsA("BasePart") and (part.Position - hrp.Position).Magnitude <= prompt.MaxActivationDistance then
                    fireproximityprompt(prompt)
                end
            else
                L.autoFeatures.autoCollectKaub.prompts[prompt] = nil
            end
        end
    end)
    return descendantAddedConn
end
AutoTab:Toggle({
    Title = G.ToggleAutoCollectTitle,
    Desc = G.ToggleAutoCollectDesc,
    Value = false,
    Callback = function(state)
        L.autoFeatures.autoCollectKaub.active = state
        if state then
            local conn = L.setupKaubAutoCollect()
            L.autoFeatures.autoCollectKaub.descendantConn = conn
        else
            if L.autoFeatures.autoCollectKaub.connection then L.autoFeatures.autoCollectKaub.connection:Disconnect() end
            if L.autoFeatures.autoCollectKaub.descendantConn then L.autoFeatures.autoCollectKaub.descendantConn:Disconnect() end
            L.autoFeatures.autoCollectKaub.prompts = {}
        end
    end
})

AutoTab:Toggle({
    Title = G.ToggleAutoDoorTitle,
    Desc = G.ToggleAutoDoorDesc,
    Value = false,
    Callback = function(state)
        L.autoDoorEnabled = state
        if state then
            if L.autoDoorThread then task.cancel(L.autoDoorThread) end
            L.autoDoorThread = task.spawn(L.autoDoorLoop)
        else
            if L.autoDoorThread then task.cancel(L.autoDoorThread); L.autoDoorThread = nil end
            L.processingDoors = {}
        end
    end
})

local FlyTab = FeatureSection:Tab({ Title = G.TabFly, Icon = "rocket" })

FlyTab:Button({
    Title = G.ButtonFlyOriginalTitle,
    Icon = "plane",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/wzhxll/stjnr/refs/heads/main/README.md"))()
    end
})

FlyTab:Button({
    Title = G.ButtonFlyNewTitle,
    Icon = "rocket",
    Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/wzhxll/Sha-Bi/refs/heads/main/README.md"))()
    end
})

local BrushTab = FeatureSection:Tab({ Title = G.TabBrush, Icon = "gift" })
function L.getPurchaseEvent()
    local rs = game:GetService("ReplicatedStorage")
    local events = rs:FindFirstChild("Events")
    if not events then return nil end
    local customize = events:FindFirstChild("Customize")
    if not customize then return nil end
    return customize:FindFirstChild("PurchaseEvent")
end
function L.getEquipWeaponEvent()
    local rs = game:GetService("ReplicatedStorage")
    local events = rs:FindFirstChild("Events")
    if not events then return nil end
    return events:FindFirstChild("EquipWeapon")
end
BrushTab:Button({
    Title = G.ButtonGetBaguetteTitle,
    Icon = "gift",
    Callback = function()
        local purchase = L.getPurchaseEvent()
        if purchase then purchase:FireServer("Baguette"); WindUI:Notify({ Title = "获取", Content = "已获取法棍", Duration = 2 }) end
    end
})
BrushTab:Button({
    Title = G.ButtonGetVoivodeTitle,
    Icon = "gift",
    Callback = function()
        local purchase = L.getPurchaseEvent()
        if purchase then purchase:FireServer("Voivode"); WindUI:Notify({ Title = "获取", Content = "已获取吸血鬼刀", Duration = 2 }) end
    end
})
BrushTab:Button({
    Title = G.ButtonGetStakeTitle,
    Icon = "gift",
    Callback = function()
        local purchase = L.getPurchaseEvent()
        if purchase then purchase:FireServer("Iron Stake"); WindUI:Notify({ Title = "获取", Content = "已获取铁桩", Duration = 2 }) end
    end
})
BrushTab:Button({
    Title = G.ButtonGetAllTitle,
    Icon = "star",
    Callback = function()
        local purchase = L.getPurchaseEvent()
        local equip = L.getEquipWeaponEvent()
        if not purchase or not equip then
            WindUI:Notify({ Title = "获取", Content = "出现未知错误", Duration = 2, Type = "error" })
            return
        end
        purchase:FireServer("Baguette")
        purchase:FireServer("Voivode")
        purchase:FireServer("Iron Stake")
        task.wait(0.2)
        local classes = {"LineInfantry", "Officer", "Seaman", "Musician", "Sapper", "Surgeon", "Chaplain"}
        for _, class in ipairs(classes) do
            if class == "Sapper" then equip:FireServer(class, "Baguette", false)
            elseif class == "Chaplain" then equip:FireServer(class, "Iron Stake", false)
            else equip:FireServer(class, "Voivode", false) end
        end
        WindUI:Notify({ Title = "获取", Content = "已获取所有武器并装备", Duration = 3 })
    end
})

-- ==================== 杀戮光环 ====================
KillSection = Window:Section({ Title = G.SectionKill, Opened = false })
KillTab = KillSection:Tab({ Title = G.TabKill, Icon = "https://chaton-images.s3.us-east-2.amazonaws.com/TVqsXZIE7OUmEhRi60F9GVlr7L1TvbpB3ne3ZKrXNd5zz49w2CLTu8vYcfmaSNVz_1009x1180x948388.png" })

-- ==================== 多选下拉框：控制杀戮光环攻击的僵尸类型 ====================
local zombieTypeNames = {
    Barrel   = "自爆",
    Axe      = "斧头僵尸",
    Eye      = "红眼",
    Sword    = "胸甲骑兵",
    FTorso   = "提灯人",
    Normal   = "山伯乐"
}
-- 默认选中除自爆外的所有类型
local defaultSelected = {}
for typeKey, name in pairs(zombieTypeNames) do
    if typeKey ~= "Barrel" then
        table.insert(defaultSelected, name)
    end
end
-- 初始化选中表（Barrel 键未被设置，即为 nil，表示不攻击自爆）
L.selectedZombieTypes = {}
for _, label in ipairs(defaultSelected) do
    for k, v in pairs(zombieTypeNames) do
        if v == label then
            L.selectedZombieTypes[k] = true
            break
        end
    end
end

KillTab:Dropdown({
    Title = "攻击僵尸类型",
    Desc = "选择攻击的僵尸类型",
    Values = {"自爆", "斧头僵尸", "红眼", "胸甲骑兵", "提灯人", "山伯乐"},
    Multi = true,
    Default = defaultSelected,
    Callback = function(selected)
        L.selectedZombieTypes = {}
        for _, label in ipairs(selected) do
            for typeKey, displayName in pairs(zombieTypeNames) do
                if displayName == label then
                    L.selectedZombieTypes[typeKey] = true
                    break
                end
            end
        end
    end
})

KillTab:Divider()

-- ==================== 通用工具函数 ====================
-- 判断僵尸是否为自爆（直接根据部件或属性，最可靠）
function L.isBarrelZombie(zombie)
    if zombie:FindFirstChild("Barrel") then return true end
    if zombie:GetAttribute("Type") == "Barrel" then return true end
    return false
end

-- 判断僵尸类型（用于其他僵尸的识别）
function L.getZombieTypeKey(zombie)
    if zombie:FindFirstChild("Axe") then return "Axe"
    elseif zombie:FindFirstChild("Eye") then return "Eye"
    elseif zombie:FindFirstChild("Sword") then return "Sword"
    elseif zombie:FindFirstChild("FTorso") then return "FTorso"
    else return "Normal" end
end

-- 核心检查：如果僵尸是自爆，则根据 L.selectedZombieTypes["Barrel"] 决定是否攻击；否则根据其他类型
function L.isZombieAttackAllowed(zombie)
    if L.isBarrelZombie(zombie) then
        -- 自爆：只有当下拉框中勾选了“自爆”才允许攻击，否则绝对禁止
        return L.selectedZombieTypes["Barrel"] == true
    else
        local typeKey = L.getZombieTypeKey(zombie)
        return L.selectedZombieTypes[typeKey] == true
    end
end

function L.getHeldMelee()
    local char = lp.Character
    if not char then return nil end
    for _, item in pairs(char:GetChildren()) do
        if item:IsA("Tool") and item:GetAttribute("Melee") then
            return item
        end
    end
    return nil
end

-- ==================== 高频杀戮光环 ====================
L.auraEnabled = false
L.attackThread = nil
L.attackCount = 2
L.displayRange = 45

local function getActualRange()
    return L.displayRange * (25 / 45)
end

function L.attackLoop()
    while L.auraEnabled do
        local weapon = L.getHeldMelee()
        if weapon then
            local char = lp.Character
            if char then
                local myRoot = char:FindFirstChild("HumanoidRootPart")
                if myRoot then
                    local range = getActualRange()
                    local zombies = {}
                    local folder = workspace:FindFirstChild("Zombies")
                    if folder then
                        for _, z in pairs(folder:GetChildren()) do
                            if z:IsA("Model") and z:FindFirstChild("HumanoidRootPart") then
                                -- 严格检查：自爆必须勾选才攻击，其他僵尸按类型
                                if not L.isZombieAttackAllowed(z) then continue end
                                if z:FindFirstChild("State") and z.State.Value == "Spawn" then continue end
                                local dist = (z.HumanoidRootPart.Position - myRoot.Position).Magnitude
                                if dist <= range then
                                    table.insert(zombies, {zombie = z, dist = dist})
                                end
                            end
                        end
                    end
                    table.sort(zombies, function(a,b) return a.dist < b.dist end)
                    local toAttack = math.min(L.attackCount, #zombies)
                    for i = 1, toAttack do
                        local remote = weapon:FindFirstChild("RemoteEvent")
                        if remote then
                            local head = zombies[i].zombie:FindFirstChild("Head")
                            if head then
                                remote:FireServer("Swing", "Side")
                                remote:FireServer("HitZombie", zombies[i].zombie, head.Position, true)
                            end
                        end
                    end
                end
            end
        end
        task.wait(0.05)
    end
end

function L.startAura()
    if L.attackThread then return end
    L.auraEnabled = true
    L.attackThread = task.spawn(L.attackLoop)
end

function L.stopAura()
    L.auraEnabled = false
    if L.attackThread then
        task.cancel(L.attackThread)
        L.attackThread = nil
    end
end

lp.CharacterAdded:Connect(function()
    if L.auraEnabled then
        task.wait(0.5)
        L.stopAura()
        task.wait(0.1)
        L.startAura()
    end
end)

KillTab:Toggle({
    Title = G.ToggleAuraHighFreqTitle,
    Desc = G.ToggleAuraHighFreqDesc,
    Value = false,
    Callback = function(state)
        if state then L.startAura() else L.stopAura() end
    end
})

KillTab:Slider({
    Title = "攻击距离",
    Desc = "杀戮光环攻击距离",
    Value = { Min = 10, Max = 45, Default = 45 },
    Callback = function(v) L.displayRange = v end
})

KillTab:Slider({
    Title = "攻击数量",
    Desc = "攻击僵尸数量",
    Value = { Min = 1, Max = 5, Default = 2 },
    Callback = function(v) L.attackCount = v end
})

KillTab:Divider()

-- ==================== 手动杀戮光环（动画触发） ====================
L.killAnimEnabled = false
L.killAnimConnection = nil
L.auraRangeManual = 45

ANIM_ATTACK_RANGE = 30
ANIMATION_CONFIGS = {
    { AnimationId = "rbxassetid://12591932646", ActivationDelay = 0.2 },
    { AnimationId = "rbxassetid://12591945044", ActivationDelay = 0.27 },
    { AnimationId = "rbxassetid://12591944118", ActivationDelay = 0.4 },
    { AnimationId = "rbxassetid://12591941810", ActivationDelay = 0.2 },
    { AnimationId = "rbxassetid://12638403582", ActivationDelay = 0.65 },
    { AnimationId = "rbxassetid://114385794993502", ActivationDelay = 0.65 },
    { AnimationId = "rbxassetid://12638409326", ActivationDelay = 0.74 }
}

function L.distanceToZombie(zombie)
    local char = lp.Character
    if not char then return math.huge end
    local myRoot = char:FindFirstChild("HumanoidRootPart")
    if not myRoot then return math.huge end
    local zRoot = zombie:FindFirstChild("HumanoidRootPart")
    if not zRoot then return math.huge end
    return (zRoot.Position - myRoot.Position).Magnitude
end

function L.attackZombieOnce(zombie, weapon)
    if not weapon then return end
    local remote = weapon:FindFirstChild("RemoteEvent")
    if not remote then return end
    local head = zombie:FindFirstChild("Head")
    if head then
        remote:FireServer("Swing", "Side")
        remote:FireServer("HitZombie", zombie, head.Position, true)
    end
end

function L.performSingleAnimAttack()
    local character = lp.Character
    if not character then return end
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    if not humanoid or humanoid.Health <= 0 then return end
    local weapon = L.getHeldMelee()
    if not weapon then return end
    local zombiesInRange = {}
    local zombiesFolder = workspace:FindFirstChild("Zombies")
    if zombiesFolder then
        for _, zombie in pairs(zombiesFolder:GetChildren()) do
            if zombie:IsA("Model") and zombie:FindFirstChild("HumanoidRootPart") then
                if not L.isZombieAttackAllowed(zombie) then continue end
                if zombie.State and zombie.State.Value == "Spawn" then continue end
                if L.distanceToZombie(zombie) <= L.auraRangeManual then
                    table.insert(zombiesInRange, zombie)
                end
            end
        end
    end
    for _, zombie in ipairs(zombiesInRange) do
        L.attackZombieOnce(zombie, weapon)
    end
end

function L.onKillAnimationPlayed(animationTrack)
    if not L.killAnimEnabled then return end
    local animId = animationTrack.Animation.AnimationId
    for _, config in ipairs(ANIMATION_CONFIGS) do
        if config.AnimationId == animId then
            task.delay(config.ActivationDelay, function()
                if L.killAnimEnabled then
                    L.performSingleAnimAttack()
                end
            end)
            break
        end
    end
end

function L.updateKillAnimConnection()
    if L.killAnimEnabled then
        if L.killAnimConnection then return end
        local char = lp.Character
        if not char then
            lp.CharacterAdded:Connect(function()
                task.wait(1)
                L.updateKillAnimConnection()
            end)
            return
        end
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if humanoid then
            L.killAnimConnection = humanoid.AnimationPlayed:Connect(L.onKillAnimationPlayed)
        end
    else
        if L.killAnimConnection then
            L.killAnimConnection:Disconnect()
            L.killAnimConnection = nil
        end
    end
end

lp.CharacterAdded:Connect(L.updateKillAnimConnection)

KillTab:Toggle({
    Title = G.ToggleAuraManualTitle,
    Desc = G.ToggleAuraManualDesc,
    Value = false,
    Callback = function(state)
        L.killAnimEnabled = state
        L.updateKillAnimConnection()
    end
})

KillTab:Slider({
    Title = "手动攻击距离",
    Desc = "杀戮光环攻击距离",
    Value = { Min = 10, Max = 45, Default = 45 },
    Callback = function(value) L.auraRangeManual = value end
})

KillTab:Divider()

-- ==================== 刺刀杀戮光环 ====================
L.bayonetAuraEnabled = false
L.bayonetThread = nil
L.bayonetAttackRange = 30
L.bayonetAttackInterval = 0.05
L.bayonetCurrentIndex = 1

function L.getMusket()
    local char = lp.Character
    if not char then return nil end
    for _, tool in pairs(char:GetChildren()) do
        if tool:IsA("Tool") and tool.Name == "Musket" then
            return tool
        end
    end
    for _, tool in pairs(lp.Backpack:GetChildren()) do
        if tool:IsA("Tool") and tool.Name == "Musket" then
            return tool
        end
    end
    return nil
end

function L.attackZombieWithBayonet(zombie, weapon)
    if not weapon then return false end
    if not L.isZombieAttackAllowed(zombie) then return false end
    local remote = weapon:FindFirstChild("RemoteEvent")
    if not remote then return false end
    local head = zombie:FindFirstChild("Head")
    if not head then return false end
    remote:FireServer("ThrustBayonet")
    remote:FireServer("Bayonet_HitZombie", zombie, head.Position, true)
    return true
end

function L.getSortedZombiesInRange()
    local char = lp.Character
    if not char then return {} end
    local myRoot = char:FindFirstChild("HumanoidRootPart")
    if not myRoot then return {} end
    local zombies = {}
    local zombiesFolder = workspace:FindFirstChild("Zombies")
    if zombiesFolder then
        for _, zombie in pairs(zombiesFolder:GetChildren()) do
            if zombie:IsA("Model") and zombie:FindFirstChild("HumanoidRootPart") then
                if not L.isZombieAttackAllowed(zombie) then continue end
                if zombie:FindFirstChild("State") and zombie.State.Value == "Spawn" then continue end
                local targetRoot = zombie:FindFirstChild("HumanoidRootPart")
                if targetRoot then
                    local dist = (targetRoot.Position - myRoot.Position).Magnitude
                    if dist <= L.bayonetAttackRange then
                        table.insert(zombies, {zombie = zombie, dist = dist})
                    end
                end
            end
        end
    end
    table.sort(zombies, function(a, b) return a.dist < b.dist end)
    return zombies
end

function L.bayonetAttackLoop()
    while L.bayonetAuraEnabled do
        local char = lp.Character
        if char then
            local humanoid = char:FindFirstChildOfClass("Humanoid")
            if humanoid and humanoid.Health > 0 then
                local weapon = L.getMusket()
                if weapon then
                    local zombies = L.getSortedZombiesInRange()
                    local count = #zombies
                    if count > 0 then
                        if L.bayonetCurrentIndex > count then L.bayonetCurrentIndex = 1 end
                        local target = zombies[L.bayonetCurrentIndex]
                        if target then
                            L.attackZombieWithBayonet(target.zombie, weapon)
                        end
                        L.bayonetCurrentIndex = L.bayonetCurrentIndex + 1
                        if L.bayonetCurrentIndex > count then L.bayonetCurrentIndex = 1 end
                    end
                end
            end
        end
        task.wait(L.bayonetAttackInterval)
    end
end

function L.startBayonetAura()
    if L.bayonetThread then return end
    L.bayonetAuraEnabled = true
    L.bayonetCurrentIndex = 1
    L.bayonetThread = task.spawn(L.bayonetAttackLoop)
end

function L.stopBayonetAura()
    L.bayonetAuraEnabled = false
    if L.bayonetThread then
        task.cancel(L.bayonetThread)
        L.bayonetThread = nil
    end
    L.bayonetCurrentIndex = 1
end

KillTab:Toggle({
    Title = "杀戮光环-刺刀",
    Desc = "依旧变成刺刀大牛",
    Value = false,
    Callback = function(state)
        if state then L.startBayonetAura() else L.stopBayonetAura() end
    end
})

KillTab:Slider({
    Title = "刺刀攻击距离",
    Desc = "攻击距离调整",
    Value = { Min = 5, Max = 30, Default = 30 },
    Callback = function(value) L.bayonetAttackRange = value end
})

KillTab:Divider()

-- ==================== 攻击墙后自爆（完全独立，不受下拉框控制，原样保留） ====================
L.wallBarrelEnabled = false
L.wallBarrelSearchRange = 15
L.wallBarrelAttackRange = 45
L.wallBarrelAttackSpeed = 2
L.wallBarrelMultiplier = 1
L.wallBarrelDelay = 0.005
L.wallBarrelThread = nil
L.wallBarrelIndex = 1

function L.getBarrelZombies()
    local barrels = {}
    local zombiesFolder = workspace:FindFirstChild("Zombies")
    if not zombiesFolder then return barrels end
    for _, zombie in pairs(zombiesFolder:GetChildren()) do
        if zombie:IsA("Model") and (zombie:GetAttribute("Type") == "Barrel" or zombie:FindFirstChild("Barrel")) then
            table.insert(barrels, zombie)
        end
    end
    return barrels
end

function L.isBarrelHidden(zombie)
    local char = lp.Character
    if not char then return true end
    local head = char:FindFirstChild("Head")
    if not head then return true end
    local targetPart = zombie:FindFirstChild("Head") or zombie:FindFirstChild("HumanoidRootPart")
    if not targetPart then return true end
    
    local origin = head.Position
    local dir = targetPart.Position - origin
    local ray = Ray.new(origin, dir)
    
    local ignoreList = {char}
    for _, pl in ipairs(Players:GetPlayers()) do
        if pl ~= lp and pl.Character then table.insert(ignoreList, pl.Character) end
    end
    local zombiesFolder = workspace:FindFirstChild("Zombies")
    if zombiesFolder then
        for _, z in ipairs(zombiesFolder:GetChildren()) do
            if z:IsA("Model") then table.insert(ignoreList, z) end
        end
    end
    local cameraFolder = workspace:FindFirstChild("Camera")
    if cameraFolder then
        for _, z in ipairs(cameraFolder:GetChildren()) do
            if z:IsA("Model") and z.Name == "m_Zombie" then table.insert(ignoreList, z) end
        end
    end
    
    local hit = workspace:FindPartOnRayWithIgnoreList(ray, ignoreList)
    if hit and not hit:IsDescendantOf(zombie) then return true end
    return false
end

function L.attackHiddenBarrel(zombie, weapon)
    if not weapon then return false end
    -- 此功能不受下拉框控制，始终攻击墙后自爆
    local remote = weapon:FindFirstChild("RemoteEvent")
    if not remote then return false end
    local head = zombie:FindFirstChild("Head")
    if not head then return false end
    local myRoot = lp.Character and lp.Character:FindFirstChild("HumanoidRootPart")
    local targetRoot = zombie:FindFirstChild("HumanoidRootPart")
    if not myRoot or not targetRoot then return false end
    if (targetRoot.Position - myRoot.Position).Magnitude > L.wallBarrelAttackRange then return false end
    remote:FireServer("Swing", "Side")
    remote:FireServer("HitZombie", zombie, head.Position, true)
    return true
end

function L.wallBarrelLoop()
    while L.wallBarrelEnabled do
        local char = lp.Character
        if char then
            local humanoid = char:FindFirstChildOfClass("Humanoid")
            if humanoid and humanoid.Health > 0 then
                local weapon = L.getHeldMelee()
                if weapon then
                    local targets = {}
                    local barrels = L.getBarrelZombies()
                    local myRoot = char:FindFirstChild("HumanoidRootPart")
                    if myRoot then
                        for _, barrel in ipairs(barrels) do
                            local targetRoot = barrel:FindFirstChild("HumanoidRootPart")
                            if targetRoot then
                                local dist = (targetRoot.Position - myRoot.Position).Magnitude
                                if dist <= L.wallBarrelSearchRange then
                                    if L.isBarrelHidden(barrel) then
                                        table.insert(targets, barrel)
                                    end
                                end
                            end
                        end
                    end
                    local count = #targets
                    if count > 0 then
                        if L.wallBarrelIndex > count then L.wallBarrelIndex = 1 end
                        local toAttack = math.min(L.wallBarrelAttackSpeed, count)
                        local attacked = 0
                        local i = L.wallBarrelIndex
                        while attacked < toAttack do
                            local barrel = targets[i]
                            if barrel then
                                for _ = 1, L.wallBarrelMultiplier do
                                    L.attackHiddenBarrel(barrel, weapon)
                                end
                                attacked = attacked + 1
                            end
                            i = i + 1
                            if i > count then i = 1 end
                        end
                        L.wallBarrelIndex = i
                    else
                        L.wallBarrelIndex = 1
                    end
                end
            end
        end
        task.wait(L.wallBarrelDelay)
    end
end

function L.startWallBarrel()
    if L.wallBarrelThread then return end
    L.wallBarrelEnabled = true
    L.wallBarrelIndex = 1
    L.wallBarrelThread = task.spawn(L.wallBarrelLoop)
end

function L.stopWallBarrel()
    L.wallBarrelEnabled = false
    if L.wallBarrelThread then
        task.cancel(L.wallBarrelThread)
        L.wallBarrelThread = nil
    end
    L.wallBarrelIndex = 1
end

KillTab:Toggle({
    Title = "攻击墙后自爆",
    Desc = "自动攻击墙体后的自爆",
    Value = false,
    Callback = function(state)
        if state then L.startWallBarrel() else L.stopWallBarrel() end
    end
})

-- ==================== 强制爆头 ====================
L.headshotEnabled = false
L.bayonetHooked = false
L.meleeHooked = false
L.originalBayonetHitCheck = nil
L.originalMeleeHitCheck = nil

function L.customBayonetHitCheck(self, origin, direction, raycastParams, hitEntities)
    local rayResult = workspace:Raycast(origin, direction, raycastParams)
    if rayResult then
        local hitPart = rayResult.Instance
        local zombieModel = hitPart and hitPart.Parent
        if zombieModel and zombieModel.Name == "m_Zombie" then
            local orig = zombieModel:FindFirstChild("Orig")
            if orig then
                local head = nil
                for _, part in ipairs(zombieModel:GetChildren()) do
                    if part.Name == "Head" and (part:IsA("Part") or part:IsA("MeshPart")) then
                        head = part
                        break
                    end
                end
                if head then
                    local zombieRef = orig.Value
                    local headPos = head.CFrame.Position
                    self.remoteEvent:FireServer("Bayonet_HitZombie", zombieRef, headPos, true, "Head")
                    zombieRef:SetAttribute("WepHitID", tick())
                    zombieRef:SetAttribute("WepHitDirection", direction * 10)
                    zombieRef:SetAttribute("WepHitPos", rayResult.Position)
                    task.delay(0.2, function()
                        if zombieRef:GetAttribute("WepHitID") == tick() then
                            zombieRef:SetAttribute("WepHitDirection", nil)
                            zombieRef:SetAttribute("WepHitPos", nil)
                            zombieRef:SetAttribute("WepHitID", nil)
                        end
                    end)
                    return 1
                end
            end
        end
        if L.originalBayonetHitCheck then
            return L.originalBayonetHitCheck(self, origin, direction, raycastParams, hitEntities)
        end
    end
    return 0
end

function L.customMeleeHitCheck(self, origin, direction, raycastParams, hitEntities, isCharge)
    local rayResult = workspace:Raycast(origin, direction, raycastParams)
    if rayResult then
        local hitPart = rayResult.Instance
        local zombieModel = hitPart and hitPart.Parent
        if zombieModel and zombieModel.Name == "m_Zombie" then
            local orig = zombieModel:FindFirstChild("Orig")
            if orig then
                local head = nil
                for _, part in ipairs(zombieModel:GetChildren()) do
                    if part.Name == "Head" and (part:IsA("Part") or part:IsA("MeshPart")) then
                        head = part
                        break
                    end
                end
                if head then
                    local zombieRef = orig.Value
                    local headPos = head.CFrame.Position
                    if isCharge then
                        self.remoteEvent:FireServer("ThrustCharge", zombieRef, headPos, rayResult.Normal)
                    else
                        local hitDirection = (headPos - origin).Unit * 25
                        self.remoteEvent:FireServer("HitZombie", zombieRef, headPos, true, hitDirection, "Head", rayResult.Normal)
                        if not zombieRef:GetAttribute("WepHitDirection") then
                            local uid = tick()
                            zombieRef:SetAttribute("WepHitID", uid)
                            zombieRef:SetAttribute("WepHitDirection", hitDirection)
                            zombieRef:SetAttribute("WepHitPos", rayResult.Position)
                            task.delay(0.2, function()
                                if zombieRef:GetAttribute("WepHitID") == uid then
                                    zombieRef:SetAttribute("WepHitDirection", nil)
                                    zombieRef:SetAttribute("WepHitPos", nil)
                                    zombieRef:SetAttribute("WepHitID", nil)
                                end
                            end)
                        end
                    end
                    return 1
                end
            end
        end
        if L.originalMeleeHitCheck then
            return L.originalMeleeHitCheck(self, origin, direction, raycastParams, hitEntities, isCharge)
        end
    end
    return 0
end

function L.enableHeadshot()
    if L.headshotEnabled then return end
    
    local rs = game:GetService("ReplicatedStorage")
    local weapons = rs:FindFirstChild("Modules"):FindFirstChild("Weapons")
    if not weapons then
        warn("强制爆头: Weapons 模块未找到")
        return
    end
    
    local flintlockSuccess, FlintLock = pcall(require, weapons:FindFirstChild("Flintlock"))
    if flintlockSuccess and FlintLock and not L.bayonetHooked then
        L.originalBayonetHitCheck = FlintLock.BayonetHitCheck
        FlintLock.BayonetHitCheck = L.customBayonetHitCheck
        L.bayonetHooked = true
    end
    
    local meleeSuccess, MeleeBase = pcall(require, weapons:FindFirstChild("MeleeBase"))
    if meleeSuccess and MeleeBase and not L.meleeHooked then
        L.originalMeleeHitCheck = MeleeBase.MeleeHitCheck
        MeleeBase.MeleeHitCheck = L.customMeleeHitCheck
        L.meleeHooked = true
    end
    
    L.headshotEnabled = true
    print("强制爆头已启用")
end

function L.disableHeadshot()
    if not L.headshotEnabled then return end
    
    local rs = game:GetService("ReplicatedStorage")
    local weapons = rs:FindFirstChild("Modules"):FindFirstChild("Weapons")
    
    if L.bayonetHooked then
        local flintlockSuccess, FlintLock = pcall(require, weapons:FindFirstChild("Flintlock"))
        if flintlockSuccess and FlintLock and L.originalBayonetHitCheck then
            FlintLock.BayonetHitCheck = L.originalBayonetHitCheck
        end
        L.bayonetHooked = false
    end
    
    if L.meleeHooked then
        local meleeSuccess, MeleeBase = pcall(require, weapons:FindFirstChild("MeleeBase"))
        if meleeSuccess and MeleeBase and L.originalMeleeHitCheck then
            MeleeBase.MeleeHitCheck = L.originalMeleeHitCheck
        end
        L.meleeHooked = false
    end
    
    L.headshotEnabled = false
    L.originalBayonetHitCheck = nil
    L.originalMeleeHitCheck = nil
    print("强制爆头已禁用")
end

onCharacterAddedForHeadshot = function()
    if L.headshotEnabled then
        task.wait(1)
        L.disableHeadshot()
        task.wait(0.1)
        L.enableHeadshot()
    end
end
lp.CharacterAdded:Connect(onCharacterAddedForHeadshot)

KillTab:Toggle({
    Title = G.ToggleHeadshotTitle,
    Desc = G.ToggleHeadshotDesc,
    Value = false,
    Callback = function(state)
        if state then L.enableHeadshot() else L.disableHeadshot() end
    end
})

-- ==================== PVP 功能 ====================
PvpTab = KillSection:Tab({ Title = G.TabPVP, Icon = "sword" })

L.pvpBayonetActive = false
L.pvpMeleeActive = false
L.pvpHeartbeatConn = nil
L.attackedBayonetPlayers = {}
L.attackedMeleePlayers = {}

BAYONET_RANGE = 17
MELEE_RANGE_PVP = 45
MELEE_ATTACK_MULTIPLIER_PVP = 1

function L.getPlayerTeam(player)
    if player.Team then return player.Team end
    local teamAttr = player:GetAttribute("Team")
    if teamAttr then return teamAttr end
    local char = player.Character
    if char then
        local teamTag = char:FindFirstChild("TeamTag") or char:FindFirstChild("Team")
        if teamTag then return teamTag.Value end
    end
    return nil
end

function L.pvpIsSameTeam(targetPlayer)
    local myTeam = L.getPlayerTeam(lp)
    local theirTeam = L.getPlayerTeam(targetPlayer)
    if myTeam and theirTeam then
        return myTeam == theirTeam
    end
    return false
end

function L.isPlayerValidPVP(targetPlayer, myRoot, range)
    if not targetPlayer or targetPlayer == lp then return false end
    if L.pvpIsSameTeam(targetPlayer) then return false end
    local char = targetPlayer.Character
    if not char then return false end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not humanoid or humanoid.Health <= 0 then return false end
    local targetRoot = char:FindFirstChild("HumanoidRootPart")
    if not targetRoot then return false end
    local dx = math.abs(targetRoot.Position.X - myRoot.Position.X)
    local dz = math.abs(targetRoot.Position.Z - myRoot.Position.Z)
    return dx <= range and dz <= range
end

function L.getMusket()
    local char = lp.Character
    if not char then return nil end
    for _, tool in pairs(char:GetChildren()) do
        if tool:IsA("Tool") and tool.Name == "Musket" then
            return tool
        end
    end
    return nil
end

function L.getMeleeWeaponPVP()
    local char = lp.Character
    if not char then return nil end
    for _, tool in pairs(char:GetChildren()) do
        if tool:IsA("Tool") and tool:FindFirstChild("RemoteEvent") and tool.Name ~= "Musket" then
            return tool
        end
    end
    for _, tool in pairs(lp.Backpack:GetChildren()) do
        if tool:IsA("Tool") and tool:FindFirstChild("RemoteEvent") and tool.Name ~= "Musket" then
            return tool
        end
    end
    return nil
end

function L.getClosestUnguardedPlayerBayonet(myRoot)
    local closest = nil
    local closestDistSq = math.huge
    for _, targetPlayer in ipairs(Players:GetPlayers()) do
        if L.isPlayerValidPVP(targetPlayer, myRoot, BAYONET_RANGE) and not L.attackedBayonetPlayers[targetPlayer] then
            local char = targetPlayer.Character
            local targetRoot = char and char:FindFirstChild("HumanoidRootPart")
            if targetRoot then
                local dx = targetRoot.Position.X - myRoot.Position.X
                local dz = targetRoot.Position.Z - myRoot.Position.Z
                local distSq = dx*dx + dz*dz
                if distSq < closestDistSq then
                    closestDistSq = distSq
                    closest = targetPlayer
                end
            end
        end
    end
    return closest
end

function L.getClosestUnguardedPlayerMelee(myRoot)
    local closest = nil
    local closestDistSq = math.huge
    for _, targetPlayer in ipairs(Players:GetPlayers()) do
        if L.isPlayerValidPVP(targetPlayer, myRoot, MELEE_RANGE_PVP) and not L.attackedMeleePlayers[targetPlayer] then
            local char = targetPlayer.Character
            local targetRoot = char and char:FindFirstChild("HumanoidRootPart")
            if targetRoot then
                local dx = targetRoot.Position.X - myRoot.Position.X
                local dz = targetRoot.Position.Z - myRoot.Position.Z
                local distSq = dx*dx + dz*dz
                if distSq < closestDistSq then
                    closestDistSq = distSq
                    closest = targetPlayer
                end
            end
        end
    end
    return closest
end

function L.attackWithBayonet(targetPlayer)
    local musket = L.getMusket()
    if not musket then return end
    local remote = musket:FindFirstChild("RemoteEvent")
    if not remote then return end
    local char = targetPlayer.Character
    if not char then return end
    local head = char:FindFirstChild("Head")
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not head or not humanoid then return end
    remote:FireServer("ThrustBayonet")
    remote:FireServer("Bayonet_HitPlayer", humanoid, head.Position)
end

function L.attackWithMeleePVP(targetPlayer)
    local weapon = L.getMeleeWeaponPVP()
    if not weapon then return end
    local remote = weapon:FindFirstChild("RemoteEvent")
    if not remote then return end
    local char = targetPlayer.Character
    if not char then return end
    local head = char:FindFirstChild("Head")
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not head or not humanoid then return end

    if weapon.Name == "Axe" then
        if humanoid and humanoid.Health > 0 then
            remote:FireServer("BraceBlock")
            remote:FireServer("StopBraceBlock")
            remote:FireServer("FeedbackStun", targetPlayer, head.Position)
        end
    end

    for _ = 1, MELEE_ATTACK_MULTIPLIER_PVP do
        remote:FireServer("PrepareSwing")
        remote:FireServer("Swing", "Side")
        remote:FireServer("HitPlayer", humanoid, head.Position)
    end
end

function L.cleanupBayonetList(myRoot)
    for target, _ in pairs(L.attackedBayonetPlayers) do
        if not L.isPlayerValidPVP(target, myRoot, BAYONET_RANGE) then
            L.attackedBayonetPlayers[target] = nil
        end
    end
end

function L.cleanupMeleeList(myRoot)
    for target, _ in pairs(L.attackedMeleePlayers) do
        if not L.isPlayerValidPVP(target, myRoot, MELEE_RANGE_PVP) then
            L.attackedMeleePlayers[target] = nil
        end
    end
end

function L.onPVPHeartbeat()
    local myChar = lp.Character
    if not myChar then return end
    local myHumanoid = myChar:FindFirstChildOfClass("Humanoid")
    if not myHumanoid or myHumanoid.Health <= 0 then return end
    local myRoot = myChar:FindFirstChild("HumanoidRootPart")
    if not myRoot then return end

    if L.pvpBayonetActive then
        L.cleanupBayonetList(myRoot)
        local target = L.getClosestUnguardedPlayerBayonet(myRoot)
        if target then
            L.attackWithBayonet(target)
            L.attackedBayonetPlayers[target] = true
        else
            L.attackedBayonetPlayers = {}
        end
    end

    if L.pvpMeleeActive then
        L.cleanupMeleeList(myRoot)
        local target = L.getClosestUnguardedPlayerMelee(myRoot)
        if target then
            L.attackWithMeleePVP(target)
            L.attackedMeleePlayers[target] = true
        else
            L.attackedMeleePlayers = {}
        end
    end
end

function L.updatePVPHeartbeat()
    if L.pvpBayonetActive or L.pvpMeleeActive then
        if not L.pvpHeartbeatConn then
            L.pvpHeartbeatConn = RunService.Heartbeat:Connect(L.onPVPHeartbeat)
        end
    else
        if L.pvpHeartbeatConn then
            L.pvpHeartbeatConn:Disconnect()
            L.pvpHeartbeatConn = nil
        end
    end
end

onCharacterAddedForPVP = function()
    L.attackedBayonetPlayers = {}
    L.attackedMeleePlayers = {}
end
lp.CharacterAdded:Connect(onCharacterAddedForPVP)

PvpTab:Toggle({
    Title = G.ToggleBayonetPVPTitle,
    Desc = G.ToggleBayonetPVPDesc,
    Value = false,
    Callback = function(state)
        L.pvpBayonetActive = state
        if not state then
            L.attackedBayonetPlayers = {}
        end
        L.updatePVPHeartbeat()
    end
})

PvpTab:Toggle({
    Title = G.ToggleMeleePVPTitle,
    Desc = G.ToggleMeleePVPDesc,
    Value = false,
    Callback = function(state)
        L.pvpMeleeActive = state
        if not state then
            L.attackedMeleePlayers = {}
        end
        L.updatePVPHeartbeat()
    end
})

-- ==================== 自动射击玩家 ====================
L.autoShootPlayerEnabled = false
L.autoShootPlayerThread = nil
L.autoShootRange = 200

getCurrentGun = function()
    local char = lp.Character
    if not char then return nil end
    for _, tool in pairs(char:GetChildren()) do
        if tool:IsA("Tool") then
            local animFolder = tool:FindFirstChild("Animations")
            if animFolder and (animFolder:FindFirstChild("Aim") or animFolder:FindFirstChild("Aiming")) then
                return tool
            end
        end
    end
    return nil
end

isObstructedBetween = function(origin, targetPos, targetPlayer)
    if not origin or not targetPos then return true end
    local dir = targetPos - origin
    local dist = dir.Magnitude
    if dist <= 0 then return false end
    local params = RaycastParams.new()
    params.FilterType = Enum.RaycastFilterType.Blacklist
    local ignoreList = {}
    for _, pl in ipairs(Players:GetPlayers()) do
        if pl.Character then table.insert(ignoreList, pl.Character) end
    end
    if targetPlayer and targetPlayer.Character then
        table.insert(ignoreList, targetPlayer.Character)
    end
    params.FilterDescendantsInstances = ignoreList
    local result = workspace:Raycast(origin, dir, params)
    if result then
        local hit = result.Instance
        if hit then
            return true
        end
    end
    return false
end

getNearestVisibleEnemyPlayer = function()
    local char = lp.Character
    if not char then return nil, nil end
    local head = char:FindFirstChild("Head")
    if not head then return nil, nil end
    local origin = head.Position
    local bestPlayer, bestPart, bestDist = nil, nil, L.autoShootRange + 1
    
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= lp then
            local myTeam = L.getPlayerTeam and L.getPlayerTeam(lp) or nil
            local theirTeam = L.getPlayerTeam and L.getPlayerTeam(player) or nil
            if myTeam and theirTeam and myTeam == theirTeam then
                continue
            end
            local targetChar = player.Character
            if targetChar then
                local humanoid = targetChar:FindFirstChildOfClass("Humanoid")
                if humanoid and humanoid.Health > 0 then
                    local targetPart = targetChar:FindFirstChild("Head") or targetChar:FindFirstChild("HumanoidRootPart") or targetChar:FindFirstChild("Torso")
                    if targetPart and targetPart:IsA("BasePart") then
                        local dist = (targetPart.Position - origin).Magnitude
                        if dist <= L.autoShootRange and dist < bestDist then
                            if not isObstructedBetween(origin, targetPart.Position, player) then
                                bestDist = dist
                                bestPlayer = player
                                bestPart = targetPart
                            end
                        end
                    end
                end
            end
        end
    end
    return bestPlayer, bestPart
end

smoothAimToTarget = function(rootPart, getTargetPosFunc, duration)
    if not rootPart or not getTargetPosFunc then return end
    local startTime = tick()
    local startCF = rootPart.CFrame
    local ok, initPos = pcall(getTargetPosFunc)
    if not ok or not initPos then return end
    while tick() - startTime < duration do
        if not rootPart.Parent then return end
        local curPos = nil
        pcall(function() curPos = getTargetPosFunc() end)
        if not curPos then curPos = initPos end
        local desired = CFrame.new(rootPart.Position, Vector3.new(curPos.X, rootPart.Position.Y, curPos.Z))
        local t = math.clamp((tick() - startTime) / duration, 0, 1)
        local smooth = t * t * (3 - 2 * t)
        local lerped = startCF:Lerp(desired, smooth)
        rootPart.CFrame = CFrame.new(rootPart.Position, rootPart.Position + lerped.LookVector)
        RunService.RenderStepped:Wait()
    end
    local finalPos = nil
    pcall(function() finalPos = getTargetPosFunc() end)
    if finalPos then
        rootPart.CFrame = CFrame.new(rootPart.Position, rootPart.Position + CFrame.new(rootPart.Position, Vector3.new(finalPos.X, rootPart.Position.Y, finalPos.Z)).LookVector)
    end
end

shootAtTarget = function(targetPart, tool)
    if not targetPart or not targetPart.Parent or not tool or not tool.Parent then return end
    local char = lp.Character
    if not char then return end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end
    local animator = humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", humanoid)
    
    local animFolder = tool:FindFirstChild("Animations")
    local aimAnimId, aimingAnimId, fireAnimId
    if animFolder then
        local aim = animFolder:FindFirstChild("Aim")
        local aiming = animFolder:FindFirstChild("Aiming")
        local fire = animFolder:FindFirstChild("Fire")
        if aim and aim:IsA("Animation") then aimAnimId = aim.AnimationId end
        if aiming and aiming:IsA("Animation") then aimingAnimId = aiming.AnimationId end
        if fire and fire:IsA("Animation") then fireAnimId = fire.AnimationId end
    end
    aimAnimId = aimAnimId or "rbxassetid://83511222574103"
    aimingAnimId = aimingAnimId or "rbxassetid://136849639865723"
    
    local trackAim = nil
    if aimAnimId then
        local anim = Instance.new("Animation")
        anim.AnimationId = aimAnimId
        trackAim = animator:LoadAnimation(anim)
        trackAim:Play(0.05, 1, 1)
        task.wait(math.min(trackAim.Length or 0.6, 0.6))
        pcall(function() trackAim:Stop(0.05) end)
    end
    
    local trackAiming = nil
    if aimingAnimId then
        local anim = Instance.new("Animation")
        anim.AnimationId = aimingAnimId
        trackAiming = animator:LoadAnimation(anim)
        trackAiming:Play(0.05, 1, 1)
    end
    task.wait(0.02)
    
    local rootPart = char:FindFirstChild("HumanoidRootPart")
    if rootPart then
        local function getTargetPos() return targetPart.Position end
        smoothAimToTarget(rootPart, getTargetPos, 0.28)
    end
    
    local trackFire = nil
    if fireAnimId then
        local anim = Instance.new("Animation")
        anim.AnimationId = fireAnimId
        trackFire = animator:LoadAnimation(anim)
        trackFire:Play(0.05, 1, 1)
    end
    
    local remote = tool:FindFirstChild("RemoteEvent")
    if not remote then
        local wsPlayers = workspace:FindFirstChild("Players")
        if wsPlayers then
            local playerFolder = wsPlayers:FindFirstChild(lp.Name)
            if playerFolder then
                local toolFolder = playerFolder:FindFirstChild(tool.Name)
                if toolFolder then
                    remote = toolFolder:FindFirstChild("RemoteEvent")
                end
            end
        end
    end
    if remote then
        local modelRef = char:FindFirstChild("Model") or char
        local timestamp = workspace:GetServerTimeNow()
        pcall(function() remote:FireServer("Fire", modelRef, targetPart.Position, timestamp) end)
    end
    
    if trackFire then
        task.delay(0.35, function() pcall(function() trackFire:Stop(0.07) end) end)
    end
    if trackAiming then
        task.wait(0.05)
        pcall(function() trackAiming:Stop(0.1) end)
    end
end

autoShootPlayerLoop = function()
    while L.autoShootPlayerEnabled do
        local char = lp.Character
        if char then
            local humanoid = char:FindFirstChildOfClass("Humanoid")
            if humanoid and humanoid.Health > 0 then
                local gun = getCurrentGun()
                if gun then
                    local _, targetPart = getNearestVisibleEnemyPlayer()
                    if targetPart then
                        shootAtTarget(targetPart, gun)
                    end
                end
            end
        end
        task.wait(0.1)
    end
end

function L.startAutoShootPlayer()
    if L.autoShootPlayerThread then return end
    L.autoShootPlayerEnabled = true
    L.autoShootPlayerThread = task.spawn(autoShootPlayerLoop)
end

function L.stopAutoShootPlayer()
    L.autoShootPlayerEnabled = false
    if L.autoShootPlayerThread then
        task.cancel(L.autoShootPlayerThread)
        L.autoShootPlayerThread = nil
    end
end

PvpTab:Toggle({
    Title = "自动射击玩家",
    Desc = "自动射击玩家",
    Value = false,
    Callback = function(state)
        if state then
            L.startAutoShootPlayer()
        else
            L.stopAutoShootPlayer()
        end
    end
})

PvpTab:Slider({
    Title = "自动射击距离",
    Desc = "调整自动射击的有效范围",
    Value = { Min = 50, Max = 300, Default = 200 },
    Callback = function(value)
        L.autoShootRange = value
    end
})

-- ==================== 独立自瞄系统（完整提取自夜脚本） ====================
-- 不依赖任何外部变量，直接使用局部变量储存

local Aimbot = {
    Enabled = false,
    ShowFOVCircle = true,
    TeamCheck = false,
    WallCheck = true,
    FOV = 100,
    SmoothAim = false,
    Smoothness = 0.18,
    AimPart = "Head",   -- "Head" 或 "HumanoidRootPart"
}

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local LocalPlayer = Players.LocalPlayer
local Camera = Workspace.CurrentCamera

-- 创建 FOV 圈 UI（独立创建，不依赖原脚本）
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "AimbotFOV"
screenGui.ResetOnSpawn = false
screenGui.Parent = game.CoreGui

local fovCircle = Instance.new("Frame")
fovCircle.Name = "FOVCircle"
fovCircle.AnchorPoint = Vector2.new(0.5, 0.5)
fovCircle.Position = UDim2.new(0.5, 0, 0.5, 0)
fovCircle.Size = UDim2.new(0, Aimbot.FOV * 2, 0, Aimbot.FOV * 2)
fovCircle.BackgroundTransparency = 1
fovCircle.Visible = false
fovCircle.Parent = screenGui

local uiStroke = Instance.new("UIStroke")
uiStroke.Thickness = 2
uiStroke.Color = Color3.fromRGB(255, 0, 0)
uiStroke.Parent = fovCircle

local uiCorner = Instance.new("UICorner")
uiCorner.CornerRadius = UDim.new(1, 0)
uiCorner.Parent = fovCircle

-- 辅助函数：获取角色的瞄准部位
local function GetAimPart(character)
    if not character then return nil end
    local part = character:FindFirstChild(Aimbot.AimPart)
    if not part then
        part = character:FindFirstChild("Head") or character:FindFirstChild("HumanoidRootPart")
    end
    return part
end

-- 辅助函数：检查目标是否存活
local function IsAlive(player)
    local char = player.Character
    local hum = char and char:FindFirstChildOfClass("Humanoid")
    return hum and hum.Health > 0
end

-- 墙体检测（带透明度忽略）
local function IsVisible(targetPart)
    if not Aimbot.WallCheck then return true end
    local origin = Camera.CFrame.Position
    local direction = targetPart.Position - origin
    local rayParams = RaycastParams.new()
    rayParams.FilterType = Enum.RaycastFilterType.Blacklist
    rayParams.FilterDescendantsInstances = {LocalPlayer.Character, Camera}
    local result = Workspace:Raycast(origin, direction, rayParams)
    if not result then return true end
    local hit = result.Instance
    if hit:IsDescendantOf(targetPart.Parent) then return true end
    -- 透明物体穿透
    if hit.Transparency and hit.Transparency > 0.4 then return true end
    if hit.CanCollide == false then return true end
    return false
end

-- 获取最佳目标
local function GetBestTarget()
    if not Aimbot.Enabled then return nil end
    local center = Camera.ViewportSize / 2
    local bestTarget = nil
    local bestDist = math.huge

    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and IsAlive(player) then
            if Aimbot.TeamCheck and player.Team == LocalPlayer.Team then
                continue
            end
            local part = GetAimPart(player.Character)
            if part then
                local dist3D = (part.Position - Camera.CFrame.Position).Magnitude
                if dist3D > 1000 then continue end
                if not IsVisible(part) then continue end
                local pos, onScreen = Camera:WorldToViewportPoint(part.Position)
                if not onScreen then continue end
                local dist2D = (Vector2.new(pos.X, pos.Y) - center).Magnitude
                if dist2D <= Aimbot.FOV and dist2D < bestDist then
                    bestDist = dist2D
                    bestTarget = player
                end
            end
        end
    end
    return bestTarget
end

-- 自瞄主循环
local lastTarget = nil
local aimConnection = nil

local function StartAimbot()
    if aimConnection then return end
    aimConnection = RunService.RenderStepped:Connect(function()
        -- 更新 FOV 圈显示
        fovCircle.Size = UDim2.new(0, Aimbot.FOV * 2, 0, Aimbot.FOV * 2)
        fovCircle.Visible = Aimbot.Enabled and Aimbot.ShowFOVCircle

        if not Aimbot.Enabled then return end
        local target = GetBestTarget()
        if target and target.Character then
            local part = GetAimPart(target.Character)
            if part then
                local targetCF = CFrame.new(Camera.CFrame.Position, part.Position)
                if Aimbot.SmoothAim then
                    Camera.CFrame = Camera.CFrame:Lerp(targetCF, Aimbot.Smoothness)
                else
                    Camera.CFrame = targetCF
                end
            end
        end
    end)
end

local function StopAimbot()
    if aimConnection then
        aimConnection:Disconnect()
        aimConnection = nil
    end
end

-- UI 控件（放在 PvpTab 中）
PvpTab:Divider()
PvpTab:Toggle({
    Title = "自瞄开关",
    Value = false,
    Callback = function(state)
        Aimbot.Enabled = state
        if state then StartAimbot() else StopAimbot() end
    end
})
PvpTab:Toggle({
    Title = "显示FOV圈",
    Value = true,
    Callback = function(state)
        Aimbot.ShowFOVCircle = state
        fovCircle.Visible = Aimbot.Enabled and state
    end
})
PvpTab:Toggle({
    Title = "队伍检测",
    Value = false,
    Callback = function(state) Aimbot.TeamCheck = state end
})
PvpTab:Toggle({
    Title = "墙体检测",
    Value = true,
    Callback = function(state) Aimbot.WallCheck = state end
})
PvpTab:Slider({
    Title = "FOV范围)",
    Value = { Min = 10, Max = 700, Default = 120 },
    Increment = 10,
    Callback = function(v)
        Aimbot.FOV = v
        fovCircle.Size = UDim2.new(0, v * 2, 0, v * 2)
    end
})
PvpTab:Toggle({
    Title = "平滑自瞄",
    Value = false,
    Callback = function(state) Aimbot.SmoothAim = state end
})

-- 初始化（确保相机变化时更新）
Workspace:GetPropertyChangedSignal("CurrentCamera"):Connect(function()
    Camera = Workspace.CurrentCamera
end)

print("[自瞄] 已加载，使用独立 FOV 圈，不依赖任何外部储存")

-- ==================== 碰撞箱功能卡 ====================
local HitboxTab = KillSection:Tab({ Title = "碰撞箱", Icon = "cube" })

-- ----- 1. 僵尸碰撞箱扩展 -----
L.zombieHitboxEnabled = false
L.zombieHitboxSize = 10
L.zombieHitboxAddedParts = {}

local function addHitboxesToZombie(zombie)
    if not L.zombieHitboxEnabled then return end
    if L.zombieHitboxAddedParts[zombie] then return end
    local hrp = zombie:FindFirstChild("HumanoidRootPart")
    local head = zombie:FindFirstChild("Head")
    if not hrp or not head then return end

    local outer = Instance.new("Part")
    outer.Name = "ZombieHitbox_Outer"
    outer.Size = Vector3.new(L.zombieHitboxSize, L.zombieHitboxSize, L.zombieHitboxSize)
    outer.Transparency = 1
    outer.CanCollide = false
    outer.CanTouch = true
    outer.Massless = true
    outer.Anchored = false
    outer.CFrame = hrp.CFrame
    outer.Parent = zombie

    local weldOuter = Instance.new("WeldConstraint")
    weldOuter.Part0 = hrp
    weldOuter.Part1 = outer
    weldOuter.Parent = outer

    local headBox = Instance.new("Part")
    headBox.Name = "ZombieHitbox_Head"
    headBox.Size = Vector3.new(L.zombieHitboxSize/2, L.zombieHitboxSize/2, L.zombieHitboxSize/2)
    headBox.Transparency = 1
    headBox.CanCollide = false
    headBox.CanTouch = true
    headBox.Massless = true
    headBox.Anchored = false
    headBox.CFrame = head.CFrame
    headBox.Parent = zombie

    local weldHead = Instance.new("WeldConstraint")
    weldHead.Part0 = head
    weldHead.Part1 = headBox
    weldHead.Parent = headBox

    L.zombieHitboxAddedParts[zombie] = { outer = outer, head = headBox }
end

local function removeHitboxesFromZombie(zombie)
    local parts = L.zombieHitboxAddedParts[zombie]
    if parts then
        if parts.outer then parts.outer:Destroy() end
        if parts.head then parts.head:Destroy() end
        L.zombieHitboxAddedParts[zombie] = nil
    else
        -- 安全清理遗留部件（避免循环调用）
        for _, child in ipairs(zombie:GetChildren()) do
            if child.Name == "ZombieHitbox_Outer" or child.Name == "ZombieHitbox_Head" then
                child:Destroy()
            end
        end
    end
end

local function refreshZombieHitboxes()
    if not L.zombieHitboxEnabled then
        -- 复制表，避免迭代中修改
        local toRemove = {}
        for zombie, _ in pairs(L.zombieHitboxAddedParts) do
            table.insert(toRemove, zombie)
        end
        for _, zombie in ipairs(toRemove) do
            removeHitboxesFromZombie(zombie)
        end
        L.zombieHitboxAddedParts = {}
        return
    end

    local allZombies = {}
    local zombiesFolder = workspace:FindFirstChild("Zombies")
    if zombiesFolder then
        for _, z in ipairs(zombiesFolder:GetChildren()) do
            if z:IsA("Model") and z.Name == "m_Zombie" then
                table.insert(allZombies, z)
            end
        end
    end
    local cameraFolder = workspace:FindFirstChild("Camera")
    if cameraFolder then
        for _, z in ipairs(cameraFolder:GetChildren()) do
            if z:IsA("Model") and z.Name == "m_Zombie" then
                table.insert(allZombies, z)
            end
        end
    end

    -- 移除已不存在的僵尸（同样复制表）
    local toRemove = {}
    for zombie, _ in pairs(L.zombieHitboxAddedParts) do
        local stillExists = false
        for _, z in ipairs(allZombies) do
            if z == zombie then stillExists = true; break end
        end
        if not stillExists then
            table.insert(toRemove, zombie)
        end
    end
    for _, zombie in ipairs(toRemove) do
        removeHitboxesFromZombie(zombie)
    end

    for _, z in ipairs(allZombies) do
        if not L.zombieHitboxAddedParts[zombie] then
            addHitboxesToZombie(z)
        end
    end
end

local function updateAllZombieHitboxSizes()
    if not L.zombieHitboxEnabled then return end
    for zombie, parts in pairs(L.zombieHitboxAddedParts) do
        if parts.outer and parts.outer.Parent then
            parts.outer.Size = Vector3.new(L.zombieHitboxSize, L.zombieHitboxSize, L.zombieHitboxSize)
        end
        if parts.head and parts.head.Parent then
            parts.head.Size = Vector3.new(L.zombieHitboxSize/2, L.zombieHitboxSize/2, L.zombieHitboxSize/2)
        end
    end
end

local function onZombieAdded(zombie)
    if L.zombieHitboxEnabled and zombie:IsA("Model") and zombie.Name == "m_Zombie" then
        task.wait(0.1)
        addHitboxesToZombie(zombie)
    end
end

local zombiesFolder = workspace:FindFirstChild("Zombies")
if zombiesFolder then
    zombiesFolder.ChildAdded:Connect(onZombieAdded)
end
local cameraFolder = workspace:FindFirstChild("Camera")
if cameraFolder then
    cameraFolder.ChildAdded:Connect(onZombieAdded)
end

task.spawn(function()
    while true do
        task.wait(2)
        if L.zombieHitboxEnabled then
            refreshZombieHitboxes()
        end
    end
end)

HitboxTab:Toggle({
    Title = "启用碰撞箱扩展",
    Desc = "为僵尸添加更大的命中箱",
    Value = false,
    Callback = function(state)
        L.zombieHitboxEnabled = state
        if state then
            refreshZombieHitboxes()
        else
            local toRemove = {}
            for zombie, _ in pairs(L.zombieHitboxAddedParts) do
                table.insert(toRemove, zombie)
            end
            for _, zombie in ipairs(toRemove) do
                removeHitboxesFromZombie(zombie)
            end
            L.zombieHitboxAddedParts = {}
        end
    end
})

HitboxTab:Slider({
    Title = "僵尸碰撞箱大小",
    Desc = "调整命中箱大小",
    Value = { Min = 1, Max = 30, Default = 10 },
    Callback = function(value)
        L.zombieHitboxSize = math.clamp(value, 1, 30)
        if L.zombieHitboxEnabled then
            updateAllZombieHitboxSizes()
            refreshZombieHitboxes()
        end
    end
})

-- ----- 2. 玩家碰撞箱扩展 -----
L.playerHitboxEnabled = false
L.playerHitboxSize = 10
L.playerHitboxAddedParts = {}

local function getPlayerTeamHitbox(plr)
    if plr.Team then return plr.Team end
    local teamAttr = plr:GetAttribute("Team")
    if teamAttr then return teamAttr end
    local char = plr.Character
    if char then
        local teamTag = char:FindFirstChild("TeamTag") or char:FindFirstChild("Team")
        if teamTag then return teamTag.Value end
    end
    return nil
end

local function isEnemyPlayer(plr)
    if plr == lp then return false end
    local myTeam = getPlayerTeamHitbox(lp)
    local theirTeam = getPlayerTeamHitbox(plr)
    if myTeam and theirTeam then
        return myTeam ~= theirTeam
    end
    return true
end

local function addHitboxesToPlayer(player)
    if not L.playerHitboxEnabled then return end
    if L.playerHitboxAddedParts[player] then return end
    if not isEnemyPlayer(player) then return end

    local char = player.Character
    if not char or not char.Parent then return end

    local hrp = char:FindFirstChild("HumanoidRootPart")
    local head = char:FindFirstChild("Head")
    if not hrp or not head then return end

    local outer = Instance.new("Part")
    outer.Name = "PlayerHitbox_Outer"
    outer.Size = Vector3.new(L.playerHitboxSize, L.playerHitboxSize, L.playerHitboxSize)
    outer.Transparency = 1
    outer.CanCollide = false
    outer.CanTouch = true
    outer.Massless = true
    outer.Anchored = false
    outer.CFrame = hrp.CFrame
    outer.Parent = char

    local weldOuter = Instance.new("WeldConstraint")
    weldOuter.Part0 = hrp
    weldOuter.Part1 = outer
    weldOuter.Parent = outer

    local headBox = Instance.new("Part")
    headBox.Name = "PlayerHitbox_Head"
    headBox.Size = Vector3.new(L.playerHitboxSize/2, L.playerHitboxSize/2, L.playerHitboxSize/2)
    headBox.Transparency = 1
    headBox.CanCollide = false
    headBox.CanTouch = true
    headBox.Massless = true
    headBox.Anchored = false
    headBox.CFrame = head.CFrame
    headBox.Parent = char

    local weldHead = Instance.new("WeldConstraint")
    weldHead.Part0 = head
    weldHead.Part1 = headBox
    weldHead.Parent = headBox

    L.playerHitboxAddedParts[player] = { outer = outer, head = headBox }
end

local function removeHitboxesFromPlayer(player)
    local parts = L.playerHitboxAddedParts[player]
    if parts then
        if parts.outer then parts.outer:Destroy() end
        if parts.head then parts.head:Destroy() end
        L.playerHitboxAddedParts[player] = nil
    else
        local char = player.Character
        if char then
            for _, child in ipairs(char:GetChildren()) do
                if child.Name == "PlayerHitbox_Outer" or child.Name == "PlayerHitbox_Head" then
                    child:Destroy()
                end
            end
        end
    end
end

local function refreshPlayerHitboxes()
    if not L.playerHitboxEnabled then
        local toRemove = {}
        for plr, _ in pairs(L.playerHitboxAddedParts) do
            table.insert(toRemove, plr)
        end
        for _, plr in ipairs(toRemove) do
            removeHitboxesFromPlayer(plr)
        end
        L.playerHitboxAddedParts = {}
        return
    end
    for _, plr in ipairs(Players:GetPlayers()) do
        if isEnemyPlayer(plr) then
            addHitboxesToPlayer(plr)
        else
            if L.playerHitboxAddedParts[plr] then removeHitboxesFromPlayer(plr) end
        end
    end
end

local function updateAllPlayerHitboxSizes()
    if not L.playerHitboxEnabled then return end
    for plr, parts in pairs(L.playerHitboxAddedParts) do
        if parts.outer and parts.outer.Parent then
            parts.outer.Size = Vector3.new(L.playerHitboxSize, L.playerHitboxSize, L.playerHitboxSize)
        end
        if parts.head and parts.head.Parent then
            parts.head.Size = Vector3.new(L.playerHitboxSize/2, L.playerHitboxSize/2, L.playerHitboxSize/2)
        end
    end
end

local function onPlayerAddedHitbox(plr)
    plr.CharacterAdded:Connect(function()
        task.wait(0.2)
        if L.playerHitboxEnabled and isEnemyPlayer(plr) then addHitboxesToPlayer(plr) end
    end)
    if L.playerHitboxEnabled and isEnemyPlayer(plr) and plr.Character then
        task.wait(0.2)
        addHitboxesToPlayer(plr)
    end
end

local function onPlayerRemovingHitbox(plr)
    if L.playerHitboxAddedParts[plr] then removeHitboxesFromPlayer(plr) end
end

task.spawn(function()
    while true do
        task.wait(2)
        if L.playerHitboxEnabled then
            for _, plr in ipairs(Players:GetPlayers()) do
                if plr == lp then continue end
                local enemy = isEnemyPlayer(plr)
                local has = L.playerHitboxAddedParts[plr] ~= nil
                if enemy and not has then
                    addHitboxesToPlayer(plr)
                elseif not enemy and has then
                    removeHitboxesFromPlayer(plr)
                end
            end
        end
    end
end)

for _, plr in ipairs(Players:GetPlayers()) do onPlayerAddedHitbox(plr) end
Players.PlayerAdded:Connect(onPlayerAddedHitbox)
Players.PlayerRemoving:Connect(onPlayerRemovingHitbox)

HitboxTab:Toggle({
    Title = "启用玩家碰撞箱扩展",
    Desc = "扩大对敌方玩家的命中箱",
    Value = false,
    Callback = function(state)
        L.playerHitboxEnabled = state
        refreshPlayerHitboxes()
    end
})

HitboxTab:Slider({
    Title = "玩家碰撞箱大小",
    Desc = "调整敌方玩家命中箱",
    Value = { Min = 3, Max = 30, Default = 10 },
    Callback = function(value)
        L.playerHitboxSize = math.clamp(value, 3, 30)
        if L.playerHitboxEnabled then
            updateAllPlayerHitboxSizes()
            for _, plr in ipairs(Players:GetPlayers()) do
                if isEnemyPlayer(plr) and not L.playerHitboxAddedParts[plr] then
                    addHitboxesToPlayer(plr)
                end
            end
        end
    end
})

-- ==================== 透视 ====================
local ESP_Section = Window:Section({ Title = "透视", Opened = false })
local ZombieESPTab = ESP_Section:Tab({ Title = "僵尸透视", Icon = "eye" })

L.ZOMBIE_ESP_RANGE = 200

function L.lightenColor(color, factor)
    factor = factor or 0.5
    return Color3.new(
        color.R + (1 - color.R) * factor,
        color.G + (1 - color.G) * factor,
        color.B + (1 - color.B) * factor
    )
end

L.ZOMBIE_TYPES = {
    Axe    = { name = "斧头僵尸", color = Color3.fromRGB(180, 0, 250), highlightColor = L.lightenColor(Color3.fromRGB(180, 0, 250)), part = "Axe" },
    Eye    = { name = "红眼",      color = Color3.fromRGB(255, 50, 50),  highlightColor = L.lightenColor(Color3.fromRGB(255, 50, 50)),  part = "Eye" },
    Sword  = { name = "胸甲骑兵",  color = Color3.fromRGB(255, 0, 255),  highlightColor = L.lightenColor(Color3.fromRGB(255, 0, 255)),  part = "Sword" },
    Barrel = { name = "自爆",      color = Color3.fromRGB(250, 250, 0),  highlightColor = L.lightenColor(Color3.fromRGB(250, 250, 0)),  part = "Barrel" },
    FTorso = { name = "提灯人",    color = Color3.fromRGB(255, 120, 0),  highlightColor = L.lightenColor(Color3.fromRGB(255, 120, 0)),  part = "FTorso" },
    Normal = { name = "山伯乐",    color = Color3.fromRGB(144, 238, 144), highlightColor = Color3.fromRGB(144, 238, 144), part = nil }
}

L.zombieEspEnabled = {
    Axe = false, Eye = false, Sword = false, Barrel = false, FTorso = false, Normal = false
}

L.zombieEffects = {}

function L.getZombieTypeKey(zombie)
    for typeKey, config in pairs(L.ZOMBIE_TYPES) do
        if config.part and zombie:FindFirstChild(config.part) then
            return typeKey
        end
    end
    return "Normal"
end

function L.createTag(zombie, typeKey)
    local config = L.ZOMBIE_TYPES[typeKey]
    if not config then return nil end
    local attachPart = zombie.PrimaryPart or zombie:FindFirstChild("Head") or zombie:FindFirstChild("HumanoidRootPart")
    if not attachPart then return nil end
    local tag = Instance.new("BillboardGui")
    tag.Size = UDim2.new(0, 120, 0, 30)
    tag.StudsOffset = Vector3.new(0, 2.5, 0)
    tag.AlwaysOnTop = true
    tag.Adornee = attachPart
    tag.Parent = zombie
    local label = Instance.new("TextLabel")
    label.Text = config.name
    label.Size = UDim2.new(1, 0, 1, 0)
    label.BackgroundTransparency = 1
    label.TextColor3 = config.highlightColor
    label.TextTransparency = 0.3
    label.Font = Enum.Font.GothamBold
    label.TextSize = 14
    label.TextStrokeTransparency = 0.5
    label.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    label.Parent = tag
    return tag
end

function L.createHighlight(zombie, color)
    local hl = Instance.new("Highlight")
    hl.FillColor = color
    hl.FillTransparency = 0.7
    hl.OutlineColor = color
    hl.OutlineTransparency = 0.7
    hl.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
    hl.Adornee = zombie
    hl.Parent = zombie
    return hl
end

function L.removeZombieEffects(zombie)
    local effects = L.zombieEffects[zombie]
    if effects then
        if effects.tag then effects.tag:Destroy() end
        if effects.highlight then effects.highlight:Destroy() end
        L.zombieEffects[zombie] = nil
    end
end

function L.clearAllZombieEffects()
    for zombie, _ in pairs(L.zombieEffects) do
        L.removeZombieEffects(zombie)
    end
end

function L.updateZombieESP()
    local anyEnabled = false
    for _, v in pairs(L.zombieEspEnabled) do
        if v then anyEnabled = true; break end
    end
    if not anyEnabled then
        L.clearAllZombieEffects()
        return
    end

    local char = lp.Character
    local rootPart = char and char:FindFirstChild("HumanoidRootPart")
    local playerPos = rootPart and rootPart.Position
    if not playerPos then
        L.clearAllZombieEffects()
        return
    end

    for zombie, _ in pairs(L.zombieEffects) do
        if not zombie.Parent then
            L.removeZombieEffects(zombie)
        end
    end

    local cameraFolder = workspace:FindFirstChild("Camera")
    if not cameraFolder then return end

    local zombies = cameraFolder:GetDescendants()
    for i = 1, #zombies do
        local zombie = zombies[i]
        if zombie:IsA("Model") and zombie.Name:find("Zombie") then
            local root = zombie:FindFirstChild("HumanoidRootPart") or zombie:FindFirstChild("Head") or zombie:FindFirstChild("Torso")
            if root then
                local dist = (root.Position - playerPos).Magnitude
                local typeKey = L.getZombieTypeKey(zombie)
                local enabled = L.zombieEspEnabled[typeKey]

                if enabled and dist <= L.ZOMBIE_ESP_RANGE then
                    if not L.zombieEffects[zombie] then
                        local config = L.ZOMBIE_TYPES[typeKey]
                        local tag = L.createTag(zombie, typeKey)
                        local highlight = L.createHighlight(zombie, config.highlightColor)
                        L.zombieEffects[zombie] = { tag = tag, highlight = highlight, typeKey = typeKey }
                    end
                else
                    if L.zombieEffects[zombie] then
                        L.removeZombieEffects(zombie)
                    end
                end
            end
        end
    end
end

L.lastZombieESPUpdate = 0
L.zombieESPHeartbeatConn = RunService.Heartbeat:Connect(function()
    local now = tick()
    if now - L.lastZombieESPUpdate >= 0.2 then
        L.lastZombieESPUpdate = now
        L.updateZombieESP()
    end
end)

lp.CharacterAdded:Connect(function()
    task.wait(0.5)
    L.updateZombieESP()
end)

-- 僵尸透视 UI 控件
ZombieESPTab:Toggle({
    Title = G.ToggleESPAxeTitle,
    Value = false,
    Callback = function(state)
        L.zombieEspEnabled.Axe = state
        L.updateZombieESP()
    end
})
ZombieESPTab:Toggle({
    Title = G.ToggleESPEyeTitle,
    Value = false,
    Callback = function(state)
        L.zombieEspEnabled.Eye = state
        L.updateZombieESP()
    end
})
ZombieESPTab:Toggle({
    Title = G.ToggleESPSwordTitle,
    Value = false,
    Callback = function(state)
        L.zombieEspEnabled.Sword = state
        L.updateZombieESP()
    end
})

-- 胸甲骑兵冲锋提醒（仅弹窗，无高亮）
local CuirassierChargeNotify = false
local LastChargeState = false

local function CheckCuirassierCharge()
    local zFolder = workspace:FindFirstChild("Zombies")
    if not zFolder then return end
    local slim = zFolder:FindFirstChild("Slim")
    if not slim then return end
    local stateVal = slim:FindFirstChild("State")
    if not stateVal or not stateVal:IsA("StringValue") then return end
    local charging = (stateVal.Value == "BeginCharge" or stateVal.Value == "Charge")
    if charging and not LastChargeState and CuirassierChargeNotify then
        WindUI:Notify({
            Title = "胸甲骑兵冲锋",
            Content = "胸甲骑兵冲锋中",
            Duration = 3,
            Icon = "bell"
        })
    end
    LastChargeState = charging
end

local chargeCheckThread = nil
local function startChargeCheck()
    if chargeCheckThread then return end
    chargeCheckThread = task.spawn(function()
        while CuirassierChargeNotify do
            CheckCuirassierCharge()
            task.wait(0.5)
        end
        chargeCheckThread = nil
    end)
end

ZombieESPTab:Toggle({
    Title = "冲锋提醒",        -- 只有标题，没有描述，与其他透视开关完全一致
    Value = false,
    Callback = function(state)
        CuirassierChargeNotify = state
        if state then
            LastChargeState = false
            startChargeCheck()
        else
            if chargeCheckThread then
                task.cancel(chargeCheckThread)
                chargeCheckThread = nil
            end
        end
    end
})

ZombieESPTab:Toggle({
    Title = G.ToggleESPBarrelTitle,
    Value = false,
    Callback = function(state)
        L.zombieEspEnabled.Barrel = state
        L.updateZombieESP()
    end
})
ZombieESPTab:Toggle({
    Title = G.ToggleESPFTorsoTitle,
    Value = false,
    Callback = function(state)
        L.zombieEspEnabled.FTorso = state
        L.updateZombieESP()
    end
})
ZombieESPTab:Toggle({
    Title = G.ToggleESPNormalTitle,
    Value = false,
    Callback = function(state)
        L.zombieEspEnabled.Normal = state
        L.updateZombieESP()
    end
})

-- ==================== 玩家透视（复活自动重建 + 更深圆点） ====================
local PlayerESPTab = ESP_Section:Tab({ Title = "玩家透视", Icon = "users" })

L.playerHighlights = {}
L.playerNameTags = {}
L.playerDots = {}
L.espPlayerEnabled = false
L.espShowNames = false
L.espTeamCheckPlayer = false

local refreshThread = nil
local REFRESH_INTERVAL = 0.2
local MAX_DIST = 300

-- ---------- 辅助函数 ----------
function L.getPlayerTeam(player)
    if player.Team then return player.Team end
    local teamAttr = player:GetAttribute("Team")
    if teamAttr then return teamAttr end
    local char = player.Character
    if char then
        local teamTag = char:FindFirstChild("TeamTag") or char:FindFirstChild("Team")
        if teamTag then return teamTag.Value end
    end
    return nil
end

function L.isSameTeam(player)
    if not L.espTeamCheckPlayer then return false end
    local myTeam = L.getPlayerTeam(lp)
    local theirTeam = L.getPlayerTeam(player)
    if myTeam and theirTeam then
        return myTeam == theirTeam
    end
    return false
end

function L.getColorsForPlayer(player)
    if not L.espTeamCheckPlayer then
        return {
            highlight = Color3.fromRGB(255, 255, 255),
            dot       = Color3.fromRGB(160, 160, 160),   -- 灰白点
            name      = Color3.fromRGB(255, 255, 255)
        }
    end
    if L.isSameTeam(player) then
        return {
            highlight = Color3.fromRGB(100, 150, 255),
            dot       = Color3.fromRGB(0, 30, 180),      -- 深蓝
            name      = Color3.fromRGB(100, 150, 255)
        }
    else
        return {
            highlight = Color3.fromRGB(255, 100, 100),
            dot       = Color3.fromRGB(180, 0, 0),       -- 深红
            name      = Color3.fromRGB(255, 100, 100)
        }
    end
end

-- 销毁玩家所有组件
function L.destroyPlayerComponents(player)
    if L.playerHighlights[player] then
        L.playerHighlights[player]:Destroy()
        L.playerHighlights[player] = nil
    end
    if L.playerNameTags[player] then
        L.playerNameTags[player]:Destroy()
        L.playerNameTags[player] = nil
    end
    if L.playerDots[player] then
        L.playerDots[player]:Destroy()
        L.playerDots[player] = nil
    end
end

-- 更新单个玩家的所有组件（支持角色重生后重新创建）
function L.updatePlayerESP(player)
    if not L.espPlayerEnabled then
        L.destroyPlayerComponents(player)
        return
    end

    local char = player.Character
    if not char or char == lp.Character then
        L.destroyPlayerComponents(player)
        return
    end

    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    local colors = L.getColorsForPlayer(player)

    -- 1. 高亮（距离限制）
    local myChar = lp.Character
    local myPos = myChar and myChar:FindFirstChild("HumanoidRootPart") and myChar.HumanoidRootPart.Position or Vector3.new()
    local dist = (hrp.Position - myPos).Magnitude
    local near = dist <= MAX_DIST

    if near then
        if not L.playerHighlights[player] then
            local hl = Instance.new("Highlight")
            hl.Adornee = char
            hl.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
            hl.FillTransparency = 0.3
            hl.OutlineTransparency = 0.3
            hl.Parent = char
            L.playerHighlights[player] = hl
        end
        L.playerHighlights[player].FillColor = colors.highlight
        L.playerHighlights[player].OutlineColor = colors.highlight
    else
        if L.playerHighlights[player] then
            L.playerHighlights[player]:Destroy()
            L.playerHighlights[player] = nil
        end
    end

    -- 2. 圆点（身体中心，永远显示，更深颜色）
    if not L.playerDots[player] then
        local dotGui = Instance.new("BillboardGui")
        dotGui.Name = "PlayerDot"
        dotGui.Size = UDim2.new(0, 5, 0, 5)       -- 稍微大一点更明显（原4改5）
        dotGui.StudsOffset = Vector3.new(0, 0, 0)
        dotGui.AlwaysOnTop = true
        dotGui.Adornee = hrp
        dotGui.Parent = char

        local dotFrame = Instance.new("Frame")
        dotFrame.Size = UDim2.new(1, 0, 1, 0)
        dotFrame.BackgroundColor3 = colors.dot
        dotFrame.BackgroundTransparency = 0
        dotFrame.BorderSizePixel = 0
        dotFrame.Parent = dotGui

        local corner = Instance.new("UICorner")
        corner.CornerRadius = UDim.new(1, 0)
        corner.Parent = dotFrame

        L.playerDots[player] = dotGui
    else
        -- 更新颜色和位置（如果角色重生，Adornee 可能已经失效，需要重新绑定）
        local dotGui = L.playerDots[player]
        if dotGui.Adornee ~= hrp then
            dotGui.Adornee = hrp
        end
        local dotFrame = dotGui:FindFirstChildWhichIsA("Frame")
        if dotFrame then
            dotFrame.BackgroundColor3 = colors.dot
        end
        -- 如果圆点所在的角色已销毁但对象还在，则重新设置父级
        if not dotGui.Parent or not dotGui.Parent:IsDescendantOf(char) then
            dotGui.Parent = char
        end
    end

    -- 3. 用户名（脚下，受开关控制）
    if L.espShowNames then
        if not L.playerNameTags[player] then
            local nameGui = Instance.new("BillboardGui")
            nameGui.Name = "PlayerNameTag"
            nameGui.Size = UDim2.new(0, 150, 0, 30)
            nameGui.StudsOffset = Vector3.new(0, -2.5, 0)
            nameGui.AlwaysOnTop = true
            nameGui.Adornee = hrp
            nameGui.Parent = char

            local label = Instance.new("TextLabel")
            label.Size = UDim2.new(1, 0, 1, 0)
            label.BackgroundTransparency = 1
            label.Text = player.Name
            label.TextColor3 = colors.name
            label.TextSize = 11
            label.Font = Enum.Font.GothamBold
            label.TextStrokeTransparency = 0
            label.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
            label.Parent = nameGui

            L.playerNameTags[player] = nameGui
        else
            local nameGui = L.playerNameTags[player]
            if nameGui.Adornee ~= hrp then
                nameGui.Adornee = hrp
            end
            if not nameGui.Parent or not nameGui.Parent:IsDescendantOf(char) then
                nameGui.Parent = char
            end
            local label = nameGui:FindFirstChildOfClass("TextLabel")
            if label then
                label.Text = player.Name
                label.TextColor3 = colors.name
            end
        end
    else
        if L.playerNameTags[player] then
            L.playerNameTags[player]:Destroy()
            L.playerNameTags[player] = nil
        end
    end
end

function L.refreshAllPlayers()
    for _, player in ipairs(Players:GetPlayers()) do
        L.updatePlayerESP(player)
    end
end

-- 自动刷新高亮的线程
local function startRefreshLoop()
    if refreshThread then return end
    refreshThread = task.spawn(function()
        while L.espPlayerEnabled do
            task.wait(REFRESH_INTERVAL)
            if L.espPlayerEnabled then
                for _, player in ipairs(Players:GetPlayers()) do
                    L.updatePlayerESP(player)
                end
            end
        end
        refreshThread = nil
    end)
end

local function stopRefreshLoop()
    if refreshThread then
        task.cancel(refreshThread)
        refreshThread = nil
    end
end

-- ---------- 事件绑定（确保角色重生后自动重建） ----------
local function setupEvents()
    -- 玩家加入时
    Players.PlayerAdded:Connect(function(player)
        -- 角色重生时重建
        player.CharacterAdded:Connect(function()
            task.wait(0.2)
            if L.espPlayerEnabled then
                L.updatePlayerESP(player)
            end
        end)
        player.CharacterRemoving:Connect(function()
            L.destroyPlayerComponents(player)
        end)
        if L.espPlayerEnabled then
            L.updatePlayerESP(player)
        end
    end)

    -- 玩家离开时清理
    Players.PlayerRemoving:Connect(function(player)
        L.destroyPlayerComponents(player)
    end)

    -- 本地玩家重生时，所有其他玩家的组件可能因为角色变化需要重新绑定
    lp.CharacterAdded:Connect(function()
        task.wait(0.5)
        if L.espPlayerEnabled then
            L.refreshAllPlayers()
        end
    end)
end

setupEvents()

-- ---------- UI 控件 ----------
PlayerESPTab:Toggle({
    Title = G.TogglePlayerESPEnableTitle,
    Desc = G.TogglePlayerESPEnableDesc,
    Value = false,
    Callback = function(state)
        L.espPlayerEnabled = state
        if state then
            L.refreshAllPlayers()
            startRefreshLoop()
        else
            stopRefreshLoop()
            for _, player in ipairs(Players:GetPlayers()) do
                L.destroyPlayerComponents(player)
            end
        end
    end
})

PlayerESPTab:Toggle({
    Title = G.TogglePlayerESPNameTitle,
    Desc = G.TogglePlayerESPNameDesc,
    Value = false,
    Callback = function(state)
        L.espShowNames = state
        L.refreshAllPlayers()
    end
})

PlayerESPTab:Toggle({
    Title = G.TogglePlayerESPTeamTitle,
    Desc = G.TogglePlayerESPTeamDesc,
    Value = false,
    Callback = function(state)
        L.espTeamCheckPlayer = state
        L.refreshAllPlayers()
    end
})

-- ==================== 防护功能栏 ====================
local ProtectSection = Window:Section({ Title = "防护", Opened = false })
local ProtectTab = ProtectSection:Tab({ Title = "防护", Icon = "shield" })

-- 防红眼功能（保持不变）
L.redEyePushEnabled = false
L.redEyePushActive = false
L.redEyeCurrentTarget = nil
L.redEyeDetectionConn = nil
L.redEyeMoveThread = nil

local REDEYE_PART = "Eye"
local REDEYE_RANGE = 8
local FORCE_MULTIPLIER = 15

local function isRedEyeZombie(model)
    if not model or not model:IsA("Model") then return false end
    if not model:FindFirstChild("HumanoidRootPart") then return false end
    return model:FindFirstChild(REDEYE_PART) ~= nil
end

local function getNearestRedEye()
    local char = lp.Character
    if not char then return nil end
    local myHRP = char:FindFirstChild("HumanoidRootPart")
    if not myHRP then return nil end
    local myPos = myHRP.Position
    local nearest, nearestDist = nil, REDEYE_RANGE + 1
    for _, obj in ipairs(workspace:GetDescendants()) do
        if obj:IsA("Model") and isRedEyeZombie(obj) then
            local hrp = obj:FindFirstChild("HumanoidRootPart")
            if hrp then
                local dist = (hrp.Position - myPos).Magnitude
                if dist <= REDEYE_RANGE and dist < nearestDist then
                    nearestDist = dist
                    nearest = obj
                end
            end
        end
    end
    return nearest
end

local function setBackToTarget(target)
    if not target then return end
    local targetHRP = target:FindFirstChild("HumanoidRootPart")
    local myChar = lp.Character
    if not targetHRP or not myChar then return end
    local myHRP = myChar:FindFirstChild("HumanoidRootPart")
    if not myHRP then return end
    local dirAway = (myHRP.Position - targetHRP.Position).Unit
    if dirAway.Magnitude > 0 then
        myHRP.CFrame = CFrame.lookAt(myHRP.Position, myHRP.Position + dirAway)
    end
end

local function moveLoop()
    while L.redEyePushEnabled do
        if L.redEyePushActive then
            local hum = lp.Character and lp.Character:FindFirstChildOfClass("Humanoid")
            if hum then
                hum:Move(Vector3.one * 1e31 * FORCE_MULTIPLIER)
            end
        end
        task.wait()
    end
end

local function detectionLoop()
    while L.redEyePushEnabled do
        if not L.redEyePushEnabled then break end
        local target = getNearestRedEye()
        if target then
            if not L.redEyePushActive then
                L.redEyePushActive = true
                L.redEyeCurrentTarget = target
            elseif L.redEyeCurrentTarget ~= target then
                L.redEyeCurrentTarget = target
            end
            setBackToTarget(L.redEyeCurrentTarget)
        else
            if L.redEyePushActive then
                L.redEyePushActive = false
                L.redEyeCurrentTarget = nil
            end
        end
        task.wait(0.03)
    end
end

local function startRedEyePush()
    if L.redEyeDetectionConn then return end
    L.redEyePushActive = false
    L.redEyeCurrentTarget = nil
    L.redEyeDetectionConn = task.spawn(detectionLoop)
    L.redEyeMoveThread = task.spawn(moveLoop)
end

local function stopRedEyePush()
    if L.redEyeDetectionConn then
        task.cancel(L.redEyeDetectionConn)
        L.redEyeDetectionConn = nil
    end
    if L.redEyeMoveThread then
        task.cancel(L.redEyeMoveThread)
        L.redEyeMoveThread = nil
    end
    L.redEyePushActive = false
    L.redEyeCurrentTarget = nil
end

ProtectTab:Toggle({
    Title = "防红眼",
    Desc = "红眼靠近玩家自动开启碰飞",
    Value = false,
    Callback = function(state)
        L.redEyePushEnabled = state
        if state then
            startRedEyePush()
        else
            stopRedEyePush()
        end
    end
})

-- ==================== 防骨折（新：纯攀爬循环） ====================
L.fallClimbProtectionEnabled = false
local fallProtectionActiveLoop = false
local fallProtectionSteppedConn = nil

-- 纯攀爬循环（无站立，高频设置）
local function fallProtectionClimbingLoop()
    while fallProtectionActiveLoop and L.fallClimbProtectionEnabled do
        local char = lp.Character
        if char then
            local hum = char:FindFirstChildOfClass("Humanoid")
            if hum then
                hum:ChangeState(Enum.HumanoidStateType.Climbing)
            end
        end
        task.wait(0.000001)   -- 极高频率，实际受引擎最小间隔限制
    end
end

local function fallProtectionStartLoop()
    if fallProtectionActiveLoop then return end
    fallProtectionActiveLoop = true
    task.spawn(fallProtectionClimbingLoop)
end

local function fallProtectionStopLoop()
    fallProtectionActiveLoop = false
end

-- Stepped 监听：当下落速度 < -5 且未按空格时启动循环，否则停止
local function onFallProtectionStepped()
    if not L.fallClimbProtectionEnabled then
        if fallProtectionActiveLoop then fallProtectionStopLoop() end
        return
    end

    local char = lp.Character
    if not char then
        if fallProtectionActiveLoop then fallProtectionStopLoop() end
        return
    end
    local hum = char:FindFirstChildOfClass("Humanoid")
    local root = char:FindFirstChild("HumanoidRootPart")
    if not hum or not root then
        if fallProtectionActiveLoop then fallProtectionStopLoop() end
        return
    end

    local shouldLoop = root.Velocity.Y < -5 and not UserInputService:IsKeyDown(Enum.KeyCode.Space)

    if shouldLoop and not fallProtectionActiveLoop then
        fallProtectionStartLoop()
    elseif not shouldLoop and fallProtectionActiveLoop then
        fallProtectionStopLoop()
    end
end

local function fallProtectionStart()
    if fallProtectionSteppedConn then return end
    fallProtectionSteppedConn = RunService.Stepped:Connect(onFallProtectionStepped)
end

local function fallProtectionStop()
    if fallProtectionSteppedConn then
        fallProtectionSteppedConn:Disconnect()
        fallProtectionSteppedConn = nil
    end
    fallProtectionStopLoop()
end

ProtectTab:Toggle({
    Title = "防骨折",
    Desc = "防止玩家从高处坠落骨折",
    Value = false,
    Callback = function(state)
        L.fallClimbProtectionEnabled = state
        if state then
            fallProtectionStart()
        else
            fallProtectionStop()
        end
    end
})

-- 显示受伤伤害（队列平滑版）
do
    local DamageDisplayEnabled = false
    local damageQueue = {}
    local isPlaying = false
    local billboard, textLabel, fadeTween = nil, nil, nil
    local lastHealth = nil
    local healthConn, charConn = nil, nil

    local function ensureBillboard()
        if billboard and billboard.Parent then return end
        local char = lp.Character
        if not char then return end
        local head = char:FindFirstChild("Head")
        if not head then return end
        billboard = Instance.new("BillboardGui")
        billboard.Size = UDim2.new(0, 100, 0, 50)
        billboard.StudsOffset = Vector3.new(0, 2.5, 0)
        billboard.AlwaysOnTop = true
        billboard.Adornee = head
        billboard.Parent = char
        textLabel = Instance.new("TextLabel")
        textLabel.Size = UDim2.new(1, 0, 1, 0)
        textLabel.BackgroundTransparency = 1
        textLabel.Text = ""
        textLabel.TextSize = 30
        textLabel.Font = Enum.Font.GothamBold
        textLabel.TextStrokeTransparency = 0.2
        textLabel.TextStrokeColor3 = Color3.fromRGB(0,0,0)
        textLabel.Parent = billboard
        billboard.Enabled = false
    end

    local function destroyBillboard()
        if billboard then billboard:Destroy() end
        billboard, textLabel = nil, nil
        if fadeTween then fadeTween:Cancel() end
        fadeTween = nil
    end

    local function showDamage(damage)
        if not DamageDisplayEnabled then return end
        ensureBillboard()
        if not billboard then return end
        local color = damage < 20 and Color3.fromRGB(0,255,0) or (damage < 50 and Color3.fromRGB(255,255,0) or Color3.fromRGB(255,0,0))
        textLabel.Text = tostring(math.floor(damage))
        textLabel.TextColor3 = color
        billboard.Enabled = true
        textLabel.TextTransparency = 0
        if fadeTween then fadeTween:Cancel() end
        fadeTween = TweenService:Create(textLabel, TweenInfo.new(0.15, Enum.EasingStyle.Quad), {TextTransparency = 0})
        fadeTween:Play()
        task.delay(1.0, function()
            if textLabel then
                local fadeOut = TweenService:Create(textLabel, TweenInfo.new(0.25, Enum.EasingStyle.Quad), {TextTransparency = 1})
                fadeOut:Play()
                fadeOut.Completed:Wait()
                if billboard then billboard.Enabled = false end
            end
            isPlaying = false
            if #damageQueue > 0 then
                local next = table.remove(damageQueue, 1)
                isPlaying = true
                showDamage(next)
            end
            fadeTween = nil
        end)
    end

    local function queueDamage(dmg)
        if not DamageDisplayEnabled then return end
        table.insert(damageQueue, dmg)
        if not isPlaying then
            isPlaying = true
            local next = table.remove(damageQueue, 1)
            showDamage(next)
        end
    end

    local function onHealthChanged()
        local char = lp.Character
        if not char then return end
        local hum = char:FindFirstChildOfClass("Humanoid")
        if not hum then return end
        local cur = hum.Health
        if lastHealth == nil then lastHealth = cur return end
        local dmg = lastHealth - cur
        if dmg > 0 then queueDamage(dmg) end
        lastHealth = cur
    end

    local function start()
        if healthConn then healthConn:Disconnect() end
        if charConn then charConn:Disconnect() end
        local char = lp.Character
        if char then
            local hum = char:FindFirstChildOfClass("Humanoid")
            if hum then
                lastHealth = hum.Health
                healthConn = hum:GetPropertyChangedSignal("Health"):Connect(onHealthChanged)
            end
        end
        charConn = lp.CharacterAdded:Connect(function(ch)
            task.wait(0.2)
            local hum = ch:FindFirstChildOfClass("Humanoid")
            if hum then
                if healthConn then healthConn:Disconnect() end
                lastHealth = hum.Health
                healthConn = hum:GetPropertyChangedSignal("Health"):Connect(onHealthChanged)
            end
            destroyBillboard()
            ensureBillboard()
            damageQueue = {}
            isPlaying = false
        end)
        ensureBillboard()
    end

    local function stop()
        if healthConn then healthConn:Disconnect() end
        if charConn then charConn:Disconnect() end
        destroyBillboard()
        damageQueue = {}
        isPlaying = false
        lastHealth = nil
        if fadeTween then fadeTween:Cancel() end
    end

    ProtectTab:Toggle({
        Title = "显示受伤伤害",
        Desc = "显示伤害数字",
        Value = false,
        Callback = function(state)
            DamageDisplayEnabled = state
            if state then start() else stop() end
        end
    })
end

-- ==================== 职业功能 ====================
local CareerSection = Window:Section({ Title = G.SectionCareer, Opened = false })
local EngineerTab = CareerSection:Tab({ Title = G.TabEngineer, Icon = "tool" })
local OfficerTab = CareerSection:Tab({ Title = G.TabOfficer, Icon = "shield" })
local AutoShootTab = CareerSection:Tab({ Title = G.TabAutoShoot, Icon = "target" })
local DoctorTab = CareerSection:Tab({ Title = G.TabDoctor, Icon = "heart" })
local ChaplainTab = CareerSection:Tab({ Title = G.TabChaplain, Icon = "cross" })
local CustomOfficerTab = CareerSection:Tab({ Title = "自定义", Icon = "settings" })

-- ========== 工兵 - 自动修复 ==========
L.engineerAutoRepairEnabled = false
L.autoRepairLoop = nil
L.repairCooldown = 0.1

function L.getLookedStructure()
    local char = lp.Character
    if not char then return nil end
    local hrp = char:FindFirstChild("HumanoidRootPart")
    if not hrp then return nil end
    local cam = workspace.CurrentCamera
    local origin = cam.CFrame.Position
    local direction = cam.CFrame.LookVector * 50
    local params = RaycastParams.new()
    params.FilterDescendantsInstances = {char}
    params.FilterType = Enum.RaycastFilterType.Blacklist
    local result = workspace:Raycast(origin, direction, params)
    if not result then return nil end
    local hit = result.Instance
    local model = hit:FindFirstAncestorOfClass("Model")
    if not model then return nil end
    local buildHealth = model:FindFirstChild("BuildingHealth") or (model.Parent and model.Parent:FindFirstChild("BuildingHealth"))
    return buildHealth
end

function L.fireRepair(buildHealth)
    local char = lp.Character
    if not char or not buildHealth then return end
    local hammer = char:FindFirstChild("Hammer")
    if not hammer or not hammer:FindFirstChild("RemoteEvent") then return end
    pcall(function() hammer.RemoteEvent:FireServer("Repair", buildHealth) end)
end

function L.autoRepairLoopFunc()
    while L.engineerAutoRepairEnabled do
        local buildHealth = L.getLookedStructure()
        if buildHealth then
            local currentHealth = buildHealth.Value
            local maxHealth = buildHealth:GetAttribute("MaxHealth")
            if maxHealth and currentHealth < maxHealth then
                L.fireRepair(buildHealth)
            end
        end
        task.wait(L.repairCooldown)
    end
end

function L.toggleEngineerAutoRepair(state)
    L.engineerAutoRepairEnabled = state
    if state then
        if L.autoRepairLoop then task.cancel(L.autoRepairLoop) end
        L.autoRepairLoop = task.spawn(L.autoRepairLoopFunc)
        WindUI:Notify({ Title = "工兵", Content = "自动修复已开启", Duration = 2 })
    else
        if L.autoRepairLoop then task.cancel(L.autoRepairLoop); L.autoRepairLoop = nil end
        WindUI:Notify({ Title = "工兵", Content = "自动修复已关闭", Duration = 2 })
    end
end

EngineerTab:Toggle({
    Title = G.ToggleEngineerAutoRepairTitle,
    Desc = G.ToggleEngineerAutoRepairDesc,
    Value = false,
    Callback = L.toggleEngineerAutoRepair
})

-- 工兵其他功能
L.engineerRecycleEnabled = false
L.engineerElbowEnabled = false
L.engineerAnimConnection = nil
local AXE_KEYWORDS = {"axe", "斧"}
local RECYCLE_ANIMATIONS = {"rbxassetid://114385794993502","rbxassetid://12638403582","rbxassetid://12638409326","rbxassetid://15345113937"}
local ELBOW_TRIGGER_ANIMATIONS = {"rbxassetid://15345113937"}
local STUN_RANGE = 50
function L.hasAxe()
    local char = lp.Character
    if not char then return false, nil end
    local tool = char:FindFirstChildOfClass("Tool")
    if not tool then return false, nil end
    local toolName = tool.Name:lower()
    for _, kw in ipairs(AXE_KEYWORDS) do
        if toolName:find(kw:lower()) then return true, tool end
    end
    return false, nil
end
function L.recycleAxe()
    if not L.engineerRecycleEnabled then return end
    local char = lp.Character
    if not char then return end
    local tool = char:FindFirstChildOfClass("Tool")
    if not tool then return end
    local toolName = tool.Name:lower()
    for _, kw in ipairs(AXE_KEYWORDS) do
        if toolName:find(kw:lower()) then
            tool.Parent = lp:FindFirstChild("Backpack")
            task.wait(0.1)
            if L.engineerRecycleEnabled and char.Parent and tool and tool.Parent == lp:FindFirstChild("Backpack") then
                tool.Parent = char
            end
            break
        end
    end
end
function L.stunAroundPlayer()
    if not L.engineerElbowEnabled then return end
    local char = lp.Character
    if not char then return end
    local has, tool = L.hasAxe()
    if not has then return end
    local remote = tool:FindFirstChild("RemoteEvent")
    if not remote then return end
    local rootPart = char:FindFirstChild("HumanoidRootPart")
    if not rootPart then return end
    local playerPos = rootPart.Position
    local zombiesFolder = workspace:FindFirstChild("Zombies")
    if not zombiesFolder then return end
    for _, zombie in pairs(zombiesFolder:GetChildren()) do
        if zombie:IsA("Model") and zombie:FindFirstChild("HumanoidRootPart") then
            if zombie:GetAttribute("Type") == "Barrel" then continue end
            local state = zombie:FindFirstChild("State")
            if state and state.Value == "Spawn" then continue end
            local zombieRoot = zombie:FindFirstChild("HumanoidRootPart")
            if not zombieRoot then continue end
            if (zombieRoot.Position - playerPos).Magnitude <= STUN_RANGE then
                if zombie:FindFirstChild("State") and zombie.State.Value ~= "Stunned" then
                    remote:FireServer("BraceBlock")
                    remote:FireServer("StopBraceBlock")
                    remote:FireServer("FeedbackStun", zombie, zombieRoot.Position)
                end
            end
        end
    end
end
function L.onEngineerAnimationPlayed(animationTrack)
    if L.engineerRecycleEnabled then
        local animId = animationTrack.Animation.AnimationId
        for _, targetId in ipairs(RECYCLE_ANIMATIONS) do
            if animId == targetId then
                local delayTime = (animId == "rbxassetid://15345113937" and 0.2) or (animId == "rbxassetid://12638409326" and 0.9) or 0.85
                task.delay(delayTime, L.recycleAxe)
                break
            end
        end
    end
    if L.engineerElbowEnabled then
        local animId = animationTrack.Animation.AnimationId
        for _, targetId in ipairs(ELBOW_TRIGGER_ANIMATIONS) do
            if animId == targetId then L.stunAroundPlayer(); break end
        end
    end
end
function L.updateEngineerAnimConnection()
    if L.engineerRecycleEnabled or L.engineerElbowEnabled then
        if L.engineerAnimConnection then return end
        local char = lp.Character
        if not char then
            lp.CharacterAdded:Connect(function() task.wait(1); L.updateEngineerAnimConnection() end)
            return
        end
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if humanoid then L.engineerAnimConnection = humanoid.AnimationPlayed:Connect(L.onEngineerAnimationPlayed) end
    else
        if L.engineerAnimConnection then L.engineerAnimConnection:Disconnect(); L.engineerAnimConnection = nil end
    end
end
lp.CharacterAdded:Connect(L.updateEngineerAnimConnection)
EngineerTab:Toggle({
    Title = G.ToggleEngineerRecycleTitle,
    Desc = G.ToggleEngineerRecycleDesc,
    Value = false,
    Callback = function(state) L.engineerRecycleEnabled = state; L.updateEngineerAnimConnection() end
})
EngineerTab:Toggle({
    Title = G.ToggleEngineerElbowRangeTitle,
    Desc = G.ToggleEngineerElbowRangeDesc,
    Value = false,
    Callback = function(state) L.engineerElbowEnabled = state; L.updateEngineerAnimConnection() end
})

L.elbowActive = false
L.elbowConnection = nil
L.lastElbowTime = 0
function L.getMelee()
    if not lp.Character then return nil end
    for _, item in pairs(lp.Character:GetChildren()) do
        if item:GetAttribute("Melee") then return item end
    end
    for _, item in pairs(lp.Backpack:GetChildren()) do
        if item:GetAttribute("Melee") then return item end
    end
    return nil
end
function L.executeElbowStun(zombie)
    local weapon = L.getMelee()
    if not weapon or weapon.Name ~= "Axe" then return end
    if zombie.State.Value == "Stunned" then return end
    weapon.RemoteEvent:FireServer("BraceBlock")
    weapon.RemoteEvent:FireServer("StopBraceBlock")
    weapon.RemoteEvent:FireServer("FeedbackStun", zombie, zombie.HumanoidRootPart.Position)
end
EngineerTab:Toggle({
    Title = G.ToggleEngineerElbowTitle,
    Desc = G.ToggleEngineerElbowDesc,
    Value = false,
    Callback = function(state)
        L.elbowActive = state
        if state then
            L.elbowConnection = RunService.Heartbeat:Connect(function()
                if not L.elbowActive or not lp.Character then return end
                local now = tick()
                if now - L.lastElbowTime < 0.2 then return end
                L.lastElbowTime = now
                local humanoid = lp.Character:FindFirstChildOfClass("Humanoid")
                if not humanoid or humanoid.Health <= 0 then return end
                for _, zombie in pairs(workspace.Zombies:GetChildren()) do
                    if zombie:IsA("Model") and zombie:FindFirstChild("HumanoidRootPart") then
                        local distance = (zombie.HumanoidRootPart.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                        if distance <= 45 then L.executeElbowStun(zombie) end
                    end
                end
            end)
        else
            if L.elbowConnection then L.elbowConnection:Disconnect(); L.elbowConnection = nil end
        end
    end
})

-- ==================== 自动黑枪（原版，无滑块，仅开关） ====================
L.autoBlackGunEnabled = false
L.officerAutoJumpEnabled = false
L.autoShootBomber = false
L.autoShootCuirassier = false
L.autoShootRunner = false
L.autoShootElectrocutioner = false

L.wallCheckEnabled = true
L.maxTargetRange = 200

function L.isGun(tool)
    if not tool or not tool:IsA("Tool") then return false end
    local animFolder = tool:FindFirstChild("Animations")
    if not animFolder then return false end
    if animFolder:FindFirstChild("Aim") then return true end
    if animFolder:FindFirstChild("Aiming") then return true end
    return false
end

function L.getShotsLoadedForTool(tool)
    if not tool then return 0 end
    local s = tool:FindFirstChild("ShotsLoaded")
    if s and (s:IsA("IntValue") or s:IsA("NumberValue")) then return s.Value end
    local wsPlayersFolder = Workspace:FindFirstChild("Players")
    if wsPlayersFolder then
        local playerFolder = wsPlayersFolder:FindFirstChild(lp.Name)
        if playerFolder then
            local toolFolder = playerFolder:FindFirstChild(tool.Name)
            if toolFolder then
                local shots = toolFolder:FindFirstChild("ShotsLoaded")
                if shots and (shots:IsA("IntValue") or shots:IsA("NumberValue")) then return shots.Value end
            end
        end
    end
    return 0
end

function L.findRemoteForTool(tool)
    if not tool then return nil end
    local remote = tool:FindFirstChild("RemoteEvent")
    if remote then return remote end
    local wsPlayersFolder = Workspace:FindFirstChild("Players")
    if wsPlayersFolder then
        local playerFolder = wsPlayersFolder:FindFirstChild(lp.Name)
        if playerFolder then
            local toolFolder = playerFolder:FindFirstChild(tool.Name)
            if toolFolder then
                return toolFolder:FindFirstChild("RemoteEvent")
            end
        end
    end
    return nil
end

function L.isObstructedBetween(origin, targetPos, targetModel)
    if not L.wallCheckEnabled then return false end
    if not origin or not targetPos then return false end
    local dir = targetPos - origin
    local dist = dir.Magnitude
    if dist <= 0 then return false end
    local function buildBaseIgnoreList()
        local ignoreList = {}
        local camFolder = Workspace:FindFirstChild("Camera")
        if camFolder then
            for _, desc in ipairs(camFolder:GetDescendants()) do
                if desc and desc:IsA("Model") and desc.Name == "m_Zombie" then table.insert(ignoreList, desc) end
            end
        end
        local zombiesFolder = Workspace:FindFirstChild("Zombies")
        if zombiesFolder then table.insert(ignoreList, zombiesFolder) end
        for _, pl in ipairs(Players:GetPlayers()) do
            if pl and pl.Character and pl.Character:IsA("Model") then table.insert(ignoreList, pl.Character) end
        end
        if targetModel then table.insert(ignoreList, targetModel) end
        return ignoreList
    end
    local params = RaycastParams.new()
    params.FilterType = Enum.RaycastFilterType.Blacklist
    params.FilterDescendantsInstances = buildBaseIgnoreList()
    local maxIterations = 12
    local remainingDistance = dist
    local originPos = origin
    local dirUnit = dir.Unit
    local epsilon = 0.2
    for i = 1, maxIterations do
        local ok, result = pcall(function() return Workspace:Raycast(originPos, dirUnit * remainingDistance, params) end)
        if not ok or not result then return false end
        local hitInst = result.Instance
        if not hitInst then return false end
        if targetModel and hitInst:IsDescendantOf(targetModel) then return false end
        local isBasePart = hitInst:IsA("BasePart")
        local canCollide = isBasePart and hitInst.CanCollide
        local transparency = isBasePart and hitInst.Transparency or 0
        local isEffectivelyInvisible = (isBasePart and transparency >= 0.95)
        if (not canCollide) or isEffectivelyInvisible then
            local advancePos = result.Position + dirUnit * epsilon
            local passed = (advancePos - origin).Magnitude
            if passed >= dist - 1e-4 then return false end
            originPos = advancePos
            remainingDistance = (targetPos - originPos).Magnitude
            local newFilter = params.FilterDescendantsInstances
            table.insert(newFilter, hitInst)
            params.FilterDescendantsInstances = newFilter
        else
            return true
        end
    end
    return true
end

L.ZombieTypeMatchers = {
    Bomber = function(model) return model:FindFirstChild("Barrel") ~= nil end,
    Cuirassier = function(model) return model:FindFirstChild("Sword") ~= nil end,
    Runner = function(model) return model:FindFirstChild("Eye") and not model:FindFirstChild("Axe") and model:FindFirstChild("Head") end,
    Electrocutioner = function(model) return model:FindFirstChild("Axe") and model:FindFirstChild("Head") end,
}

function L.getNearestTargetHeadByMatcher(range, matcherFunc)
    local camFolder = Workspace:FindFirstChild("Camera")
    local cam = workspace.CurrentCamera
    local originPos = nil
    if lp.Character and lp.Character.Parent then
        local head = lp.Character:FindFirstChild("Head")
        if head and head:IsA("BasePart") then originPos = head.Position end
    end
    if not originPos and cam then originPos = cam.CFrame.Position end
    if not originPos then return nil, nil end
    local bestPart, bestDist, bestModel = nil, range + 1e-4, nil
    if not camFolder then return nil, nil end
    for _, model in ipairs(camFolder:GetChildren()) do
        if model:IsA("Model") and model.Name == "m_Zombie" then
            if not matcherFunc(model) then continue end
            local head = model:FindFirstChild("Head")
            local barrel = model:FindFirstChild("Barrel")
            local torso = model:FindFirstChild("Torso") or model:FindFirstChild("UpperTorso") or model:FindFirstChild("HumanoidRootPart")
            local measurePart = barrel or head or torso
            if measurePart and measurePart:IsA("BasePart") then
                local okDist, d = pcall(function() return (measurePart.Position - originPos).Magnitude end)
                if okDist and d and d <= range + 1e-4 and d < bestDist then
                    local barrelVisible, headVisible, torsoVisible = false, false, false
                    if barrel and barrel:IsA("BasePart") then
                        local okVis, res = pcall(function() return not L.isObstructedBetween(originPos, barrel.Position, model) end)
                        if okVis and res then barrelVisible = true end
                    end
                    if head and head:IsA("BasePart") then
                        local okVis, res = pcall(function() return not L.isObstructedBetween(originPos, head.Position, model) end)
                        if okVis and res then headVisible = true end
                    end
                    if torso and torso:IsA("BasePart") then
                        local okVis, res = pcall(function() return not L.isObstructedBetween(originPos, torso.Position, model) end)
                        if okVis and res then torsoVisible = true end
                    end
                    local chosenPart = nil
                    if barrelVisible then chosenPart = barrel
                    elseif headVisible then chosenPart = head
                    elseif torsoVisible then chosenPart = torso end
                    if chosenPart and chosenPart:IsA("BasePart") then bestPart, bestDist, bestModel = chosenPart, d, model end
                end
            end
        end
    end
    return bestPart, bestModel
end

function L.smoothLookAtDynamic(rootPart, getPosFunc, duration)
    if not rootPart or not getPosFunc then return end
    local start = tick()
    local startCFrame = rootPart.CFrame
    local ok, initTarget = pcall(getPosFunc)
    if not ok or not initTarget then return end
    while tick() - start < duration do
        if not rootPart.Parent then return end
        local curPos = nil
        pcall(function() curPos = getPosFunc() end)
        if not curPos then curPos = initTarget end
        local desired = CFrame.new(rootPart.Position, Vector3.new(curPos.X, rootPart.Position.Y, curPos.Z))
        local t = math.clamp((tick() - start) / duration, 0, 1)
        local smoothT = t * t * (3 - 2 * t)
        local lerped = startCFrame:Lerp(desired, smoothT)
        local safeCFrame = CFrame.new(rootPart.Position, rootPart.Position + lerped.LookVector)
        pcall(function() rootPart.CFrame = safeCFrame end)
        RunService.RenderStepped:Wait()
    end
    local finalPos = nil
    pcall(function() finalPos = getPosFunc() end)
    if finalPos then
        pcall(function() rootPart.CFrame = CFrame.new(rootPart.Position, rootPart.Position + CFrame.new(rootPart.Position, Vector3.new(finalPos.X, rootPart.Position.Y, finalPos.Z)).LookVector) end)
    end
end

function L.playAnimation(animId, animator)
    if not animId or not animator then return nil end
    local ok, track = pcall(function()
        local anim = Instance.new("Animation")
        anim.AnimationId = animId
        return animator:LoadAnimation(anim)
    end)
    if not ok or not track then return nil end
    track.Priority = Enum.AnimationPriority.Action
    track:Play(0.05, 1, 1)
    return track
end

function L.aimThenShootGun(targetModel, initialPart, tool)
    if not targetModel or not targetModel.Parent then return end
    if not initialPart or not initialPart.Parent or not initialPart:IsA("BasePart") then return end
    if not tool or not tool.Parent or not tool:IsDescendantOf(lp.Character) then return end
    if not L.isGun(tool) then return end
    local char = lp.Character
    if not char then return end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end
    local animator = humanoid:FindFirstChildOfClass("Animator") or Instance.new("Animator", humanoid)
    local remote = tool:FindFirstChild("RemoteEvent") or nil
    local animFolder = tool:FindFirstChild("Animations")
    local animAId, animBId
    if animFolder then
        local aim = animFolder:FindFirstChild("Aim")
        local aiming = animFolder:FindFirstChild("Aiming")
        if aim and aim:IsA("Animation") then animAId = aim.AnimationId end
        if aiming and aiming:IsA("Animation") then animBId = aiming.AnimationId end
    end
    animAId = animAId or "rbxassetid://83511222574103"
    animBId = animBId or "rbxassetid://136849639865723"
    local fireAnimId = nil
    if animFolder then
        local fire = animFolder:FindFirstChild("Fire")
        if fire and fire:IsA("Animation") then fireAnimId = fire.AnimationId end
    end
    local trackA = L.playAnimation(animAId, animator)
    if trackA then
        task.wait(math.min(trackA.Length or 0.6, 0.6))
        pcall(function() trackA:Stop(0.05) end)
    end
    local trackB = L.playAnimation(animBId, animator)
    task.wait(0.02)
    local function getAimOrigin()
        if lp.Character and lp.Character.Parent then
            local head = lp.Character:FindFirstChild("Head")
            if head and head:IsA("BasePart") then return head.Position end
        end
        local cam = workspace.CurrentCamera
        if cam then return cam.CFrame.Position end
        return nil
    end
    local currentTargetPart = initialPart
    local function isPartVisible(part)
        if not part or not part.Parent or not part:IsA("BasePart") then return false end
        local origin = getAimOrigin()
        if not origin then return false end
        local ok, res = pcall(function() return not L.isObstructedBetween(origin, part.Position, targetModel) end)
        return ok and res
    end
    local root = char:FindFirstChild("HumanoidRootPart")
    if root and targetModel and targetModel.Parent then
        local function getPosFunc()
            if not currentTargetPart or not currentTargetPart.Parent then
                local barrel = targetModel:FindFirstChild("Barrel")
                local head = targetModel:FindFirstChild("Head")
                local torso = targetModel:FindFirstChild("Torso") or targetModel:FindFirstChild("UpperTorso") or targetModel:FindFirstChild("HumanoidRootPart")
                if barrel and isPartVisible(barrel) then currentTargetPart = barrel; return barrel.Position end
                if head and isPartVisible(head) then currentTargetPart = head; return head.Position end
                if torso and isPartVisible(torso) then currentTargetPart = torso; return torso.Position end
                return nil
            end
            if currentTargetPart and currentTargetPart.Parent then return currentTargetPart.Position end
            return nil
        end
        pcall(function() L.smoothLookAtDynamic(root, getPosFunc, L.autoBlackGunSmoothTime) end)
    else
        if trackB then pcall(function() trackB:Stop(0.1) end) end
        return
    end
    local WAIT_TIMEOUT = 3.0
    local waited = 0
    local POLL_INTERVAL = 0.05
    local shotsNow = L.getShotsLoadedForTool(tool)
    while (not shotsNow or shotsNow < 1) and waited < WAIT_TIMEOUT do
        if not tool or not tool.Parent or not tool:IsDescendantOf(lp.Character) then
            if trackB then pcall(function() trackB:Stop(0.1) end) end
            return
        end
        if not L.autoBlackGunEnabled then
            if trackB then pcall(function() trackB:Stop(0.1) end) end
            return
        end
        if currentTargetPart and (not isPartVisible(currentTargetPart)) then
            local barrel = targetModel:FindFirstChild("Barrel")
            local head = targetModel:FindFirstChild("Head")
            local torso = targetModel:FindFirstChild("Torso") or targetModel:FindFirstChild("UpperTorso") or targetModel:FindFirstChild("HumanoidRootPart")
            local switched = false
            if barrel and barrel ~= currentTargetPart and isPartVisible(barrel) then currentTargetPart = barrel; switched = true
            elseif head and head ~= currentTargetPart and isPartVisible(head) then currentTargetPart = head; switched = true
            elseif torso and torso ~= currentTargetPart and isPartVisible(torso) then currentTargetPart = torso; switched = true end
            if not switched then
                if trackB then pcall(function() trackB:Stop(0.1) end) end
                return
            end
        end
        task.wait(POLL_INTERVAL)
        waited = waited + POLL_INTERVAL
        shotsNow = L.getShotsLoadedForTool(tool)
    end
    if not shotsNow or shotsNow < 1 then
        if trackB then pcall(function() trackB:Stop(0.1) end) end
        return
    end
    task.wait(0.03)
    if not currentTargetPart or not currentTargetPart.Parent or (not isPartVisible(currentTargetPart)) then
        local barrel = targetModel:FindFirstChild("Barrel")
        local head = targetModel:FindFirstChild("Head")
        local torso = targetModel:FindFirstChild("Torso") or targetModel:FindFirstChild("UpperTorso") or targetModel:FindFirstChild("HumanoidRootPart")
        if barrel and isPartVisible(barrel) then currentTargetPart = barrel
        elseif head and isPartVisible(head) then currentTargetPart = head
        elseif torso and isPartVisible(torso) then currentTargetPart = torso
        else
            if trackB then pcall(function() trackB:Stop(0.1) end) end
            return
        end
    end
    local fireTrack = nil
    if fireAnimId then pcall(function() fireTrack = L.playAnimation(fireAnimId, animator) end) end
    pcall(function()
        local modelRef = char:FindFirstChild("Model") or char
        local t = workspace:GetServerTimeNow()
        remote = remote or tool:FindFirstChild("RemoteEvent")
        if remote and currentTargetPart and currentTargetPart.Parent then
            remote:FireServer("Fire", modelRef, currentTargetPart.Position, t)
        end
    end)
    if fireTrack then task.delay(0.35, function() pcall(function() fireTrack:Stop(0.07) end) end) end
    if trackB then task.wait(0.05); pcall(function() trackB:Stop(0.1) end) end
end

function L.isAnyOtherPlayerNearZombie(zombie, range)
    if not zombie or not zombie:FindFirstChild("HumanoidRootPart") then return false end
    local zombiePos = zombie.HumanoidRootPart.Position
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= lp and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local playerPos = player.Character.HumanoidRootPart.Position
            if (playerPos - zombiePos).Magnitude <= range then
                return true
            end
        end
    end
    return false
end

function L.processBlackGunShoot()
    if not L.autoBlackGunEnabled then return end
    
    local tool = lp.Character and lp.Character:FindFirstChildOfClass("Tool")
    if not tool or not L.isGun(tool) then return end
    
    local shots = L.getShotsLoadedForTool(tool)
    if shots < 1 then return end
    
    local targetPart, targetModel = L.getNearestTargetHeadByMatcher(L.maxTargetRange, L.ZombieTypeMatchers.Bomber)
    if not targetPart or not targetModel then return end
    
    if not L.isAnyOtherPlayerNearZombie(targetModel, L.autoBlackGunBarrelDistance) then
        return
    end
    
    if L.autoBlackGunEquipDelay > 0 then
        task.wait(L.autoBlackGunEquipDelay)
    end
    
    if not tool.Parent or L.getShotsLoadedForTool(tool) < 1 then return end
    
    L.aimThenShootGun(targetModel, targetPart, tool)
end

function L.processAutoShootForType(isEnabled, matcherFunc)
    if not isEnabled then return end
    local equippedTool = lp.Character and lp.Character:FindFirstChildOfClass("Tool")
    local equippedIsGun = equippedTool and L.isGun(equippedTool)
    local shotsForEquipped = (equippedTool and equippedIsGun) and L.getShotsLoadedForTool(equippedTool) or 0
    local effectiveAutoShoot = isEnabled and (equippedTool ~= nil) and equippedIsGun and (shotsForEquipped >= 1)
    if effectiveAutoShoot then
        local part, model = L.getNearestTargetHeadByMatcher(L.maxTargetRange, matcherFunc)
        if part and model then
            task.wait(0.5)
            if equippedTool and equippedTool.Parent and model and model.Parent and L.isGun(equippedTool) then
                local currentTool = lp.Character and lp.Character:FindFirstChildOfClass("Tool")
                if currentTool and currentTool == equippedTool then
                    L.aimThenShootGun(model, part, currentTool)
                end
            end
        end
    end
end

L.shootingLoopRunning = false
L.shootingThread = nil

function L.shootingLoop()
    while L.shootingLoopRunning do
        if L.autoShootBomber then L.processAutoShootForType(L.autoShootBomber, L.ZombieTypeMatchers.Bomber) end
        if L.autoShootCuirassier then L.processAutoShootForType(L.autoShootCuirassier, L.ZombieTypeMatchers.Cuirassier) end
        if L.autoShootRunner then L.processAutoShootForType(L.autoShootRunner, L.ZombieTypeMatchers.Runner) end
        if L.autoShootElectrocutioner then L.processAutoShootForType(L.autoShootElectrocutioner, L.ZombieTypeMatchers.Electrocutioner) end
        if L.autoBlackGunEnabled then L.processBlackGunShoot() end
        task.wait(L.autoBlackGunCooldown)
    end
end

function L.startShooting()
    if L.shootingThread then return end
    L.shootingLoopRunning = true
    L.shootingThread = task.spawn(L.shootingLoop)
end

function L.stopShooting()
    L.shootingLoopRunning = false
    if L.shootingThread then task.cancel(L.shootingThread); L.shootingThread = nil end
end

function L.updateShootingState()
    if L.autoShootBomber or L.autoShootCuirassier or L.autoShootRunner or L.autoShootElectrocutioner or L.autoBlackGunEnabled then
        L.startShooting()
    else
        L.stopShooting()
    end
end

-- ==================== 新自动跳刀 ====================
L.autoJumpAnimEnabled = false
L.autoJumpAnimMonitoring = false
L.autoJumpAnimHumanoid = nil
L.autoJumpAnimator = nil
L.autoJumpPlayedTracks = {}

local TARGET_ANIM_IDS = {
    "rbxassetid://17406577733",
    "rbxassetid://15669224658",
    "rbxassetid://12591948314",
    "rbxassetid://12333491302",
}
local TARGETS = {}
for _, id in ipairs(TARGET_ANIM_IDS) do
    local normId = id:match("^%d+$") and ("rbxassetid://" .. id) or id
    TARGETS[normId] = true
end

local function normalizeAnimId(id)
    if not id then return nil end
    local s = tostring(id)
    if s:match("^%d+$") then return "rbxassetid://" .. s end
    return s
end

local function trackIsTarget(track)
    if not track or not track.IsPlaying then return false end
    local anim = track.Animation
    if not anim or not anim.AnimationId then return false end
    return TARGETS[normalizeAnimId(anim.AnimationId)]
end

local function doJumpAnim()
    if not L.autoJumpAnimHumanoid or not L.autoJumpAnimHumanoid.Parent then return end
    task.spawn(function()
        pcall(function()
            local start = os.clock()
            while os.clock() - start < 1 do
                local state = L.autoJumpAnimHumanoid:GetState()
                if state == Enum.HumanoidStateType.Running or
                   state == Enum.HumanoidStateType.Landed or
                   state == Enum.HumanoidStateType.RunningNoPhysics or
                   state == Enum.HumanoidStateType.Climbing then
                    break
                end
                task.wait(0.05)
            end
            local root = L.autoJumpAnimHumanoid.RootPart or L.autoJumpAnimHumanoid.Parent:FindFirstChild("HumanoidRootPart")
            if root then
                local gravity = workspace.Gravity
                local jumpVelocity = math.sqrt(2 * gravity * 7.2)
                root.Velocity = Vector3.new(root.Velocity.X, jumpVelocity, root.Velocity.Z)
            end
        end)
    end)
end

local function startAnimMonitoring()
    if L.autoJumpAnimMonitoring then return end
    L.autoJumpAnimMonitoring = true
    task.spawn(function()
        while L.autoJumpAnimMonitoring do
            if L.autoJumpAnimator and L.autoJumpAnimEnabled then
                local tracks = pcall(L.autoJumpAnimator.GetPlayingAnimationTracks, L.autoJumpAnimator)
                if tracks then
                    for _, track in ipairs(tracks) do
                        if trackIsTarget(track) and not L.autoJumpPlayedTracks[track] then
                            L.autoJumpPlayedTracks[track] = true
                            doJumpAnim()
                            track.Stopped:Connect(function()
                                L.autoJumpPlayedTracks[track] = nil
                            end)
                        end
                    end
                end
            end
            task.wait(0.08)
        end
    end)
end

local function stopAnimMonitoring()
    L.autoJumpAnimMonitoring = false
    L.autoJumpPlayedTracks = {}
end

local function refreshAnimCharacter(char)
    L.autoJumpAnimHumanoid = char and char:FindFirstChildOfClass("Humanoid")
    L.autoJumpAnimator = nil
    if L.autoJumpAnimHumanoid then
        L.autoJumpAnimator = L.autoJumpAnimHumanoid:FindFirstChildOfClass("Animator")
        if not L.autoJumpAnimator then
            L.autoJumpAnimator = Instance.new("Animator")
            L.autoJumpAnimator.Name = "AutoJumpAnimator"
            L.autoJumpAnimator.Parent = L.autoJumpAnimHumanoid
        end
    end
    L.autoJumpPlayedTracks = {}
end

function setAutoJumpAnimEnabled(state)
    L.autoJumpAnimEnabled = state
    if state then
        if not L.autoJumpAnimHumanoid then refreshAnimCharacter(lp.Character) end
        startAnimMonitoring()
    else
        stopAnimMonitoring()
    end
end

refreshAnimCharacter(lp.Character)
lp.CharacterAdded:Connect(function(char)
    task.wait(0.2)
    refreshAnimCharacter(char)
    if L.autoJumpAnimEnabled then startAnimMonitoring() end
end)

-- ==================== 军官卡 UI ====================
-- 自动装填模块（修复版：武器收起再装备后自动换弹，新增换弹后快速收枪再装备）
local AutoReload = (function()
    local Players = game:GetService("Players")
    local Workspace = game:GetService("Workspace")
    local StarterGui = game:GetService("StarterGui")
    local LocalPlayer = Players.LocalPlayer

    local ENABLED = false
    local NOTIFY_COOLDOWN = 4
    local lastNotifyTime = 0
    local monitoredTools = {}
    local AUTO_HOLSTER = false        -- 新增：换弹后自动收枪再装备
    local isHolstering = false        -- 防重入标志

    local function isGun(tool)
        if not tool or not tool:IsA("Tool") then return false end
        local animFolder = tool:FindFirstChild("Animations")
        if not animFolder then return false end
        return animFolder:FindFirstChild("Aim") ~= nil or animFolder:FindFirstChild("Aiming") ~= nil
    end

    local function getShotsLoaded(tool)
        if not tool then return 0 end
        local s = tool:FindFirstChild("ShotsLoaded")
        if s and (s:IsA("IntValue") or s:IsA("NumberValue")) then return s.Value end
        local wsPlayers = Workspace:FindFirstChild("Players")
        if wsPlayers then
            local playerFolder = wsPlayers:FindFirstChild(LocalPlayer.Name)
            if playerFolder then
                local toolFolder = playerFolder:FindFirstChild(tool.Name)
                if toolFolder then
                    local shots = toolFolder:FindFirstChild("ShotsLoaded")
                    if shots and (shots:IsA("IntValue") or shots:IsA("NumberValue")) then return shots.Value end
                end
            end
        end
        return 0
    end

    local function getRemote(tool)
        if not tool then return nil end
        local remote = tool:FindFirstChild("RemoteEvent")
        if remote then return remote end
        local wsPlayers = Workspace:FindFirstChild("Players")
        if wsPlayers then
            local playerFolder = wsPlayers:FindFirstChild(LocalPlayer.Name)
            if playerFolder then
                local toolFolder = playerFolder:FindFirstChild(tool.Name)
                if toolFolder then
                    return toolFolder:FindFirstChild("RemoteEvent")
                end
            end
        end
        return nil
    end

    local function notifyReload()
        local now = tick()
        if now - lastNotifyTime < NOTIFY_COOLDOWN then return end
        lastNotifyTime = now
        pcall(function()
            if type(WindUI) == "table" and type(WindUI.Notify) == "function" then
                WindUI:Notify({
                    Title = "自动装填",
                    Content = "已装填一发子弹。",
                    Duration = 3,
                    Icon = "refresh-cw",
                })
            elseif type(Window) == "table" and type(Window.Notify) == "function" then
                Window:Notify({
                    Title = "自动装填",
                    Content = "已装填一发子弹。",
                    Duration = 3,
                    Icon = "refresh-cw",
                })
            else
                StarterGui:SetCore("SendNotification", {
                    Title = "自动装填",
                    Text = "已装填一发子弹。",
                    Duration = 3,
                })
            end
        end)

        -- 新增：如果开启了自动收枪再装备，执行快速收回再装备
        if AUTO_HOLSTER and not isHolstering then
            isHolstering = true
            task.spawn(function()
                local char = LocalPlayer.Character
                if not char then isHolstering = false; return end
                local tool = char:FindFirstChildOfClass("Tool")
                if tool and isGun(tool) then
                    -- 收回背包
                    tool.Parent = LocalPlayer.Backpack
                    task.wait(0.05)  -- 等待收回完成
                    -- 重新装备
                    if tool and tool.Parent == LocalPlayer.Backpack then
                        tool.Parent = char
                    end
                end
                task.wait(0.05)  -- 总时间约0.1秒
                isHolstering = false
            end)
        end
    end

    local function tryReload(tool)
        if not ENABLED then return end
        if not tool or not tool.Parent then return end
        if not isGun(tool) then return end
        local shots = getShotsLoaded(tool)
        if shots == 0 then
            local remote = getRemote(tool)
            if remote then
                pcall(function() remote:FireServer("Reload") end)
            end
        end
    end

    local function watchShotsForTool(tool)
        if not tool or not isGun(tool) then return end
        if monitoredTools[tool] then return end

        local shotsObj = tool:FindFirstChild("ShotsLoaded")
        if not shotsObj or not (shotsObj:IsA("IntValue") or shotsObj:IsA("NumberValue")) then
            local wsPlayers = Workspace:FindFirstChild("Players")
            if wsPlayers then
                local playerFolder = wsPlayers:FindFirstChild(LocalPlayer.Name)
                if playerFolder then
                    local toolFolder = playerFolder:FindFirstChild(tool.Name)
                    if toolFolder then
                        shotsObj = toolFolder:FindFirstChild("ShotsLoaded")
                    end
                end
            end
        end
        if not shotsObj then return end

        local remote = getRemote(tool)
        local prevVal = shotsObj.Value or 0

        if ENABLED and prevVal == 0 and remote then
            pcall(function() remote:FireServer("Reload") end)
        end

        local reloadDebounce = false
        local conn
        conn = shotsObj.Changed:Connect(function()
            local v = shotsObj.Value
            if ENABLED and type(v) == "number" and type(prevVal) == "number" and v > prevVal then
                for i = prevVal + 1, v do
                    task.spawn(notifyReload)
                end
            end
            if ENABLED and v == 0 and remote and not reloadDebounce then
                reloadDebounce = true
                pcall(function() remote:FireServer("Reload") end)
                task.delay(1.2, function() reloadDebounce = false end)
            end
            prevVal = v
        end)

        local function onEquipped()
            if ENABLED and tool.Parent == LocalPlayer.Character then
                task.wait(0.1)
                tryReload(tool)
            end
        end

        local ancestryConn
        ancestryConn = tool.AncestryChanged:Connect(function()
            if tool.Parent == LocalPlayer.Character then
                onEquipped()
            end
        end)

        local function cleanup()
            if conn then conn:Disconnect() end
            if ancestryConn then ancestryConn:Disconnect() end
            monitoredTools[tool] = nil
        end
        tool.AncestryChanged:Connect(function(_, parent)
            if not parent then cleanup() end
        end)

        monitoredTools[tool] = true
    end

    local function scanAllTools()
        for _, tool in ipairs(LocalPlayer.Backpack:GetChildren()) do
            if tool:IsA("Tool") and isGun(tool) then watchShotsForTool(tool) end
        end
        local char = LocalPlayer.Character
        if char then
            for _, tool in ipairs(char:GetChildren()) do
                if tool:IsA("Tool") and isGun(tool) then watchShotsForTool(tool) end
            end
        end
    end

    LocalPlayer.Backpack.ChildAdded:Connect(function(child)
        if child:IsA("Tool") and isGun(child) then
            task.wait(0.1)
            watchShotsForTool(child)
        end
    end)

    LocalPlayer.CharacterAdded:Connect(function(char)
        task.wait(0.5)
        for _, tool in ipairs(char:GetChildren()) do
            if tool:IsA("Tool") and isGun(tool) then
                watchShotsForTool(tool)
                if ENABLED then tryReload(tool) end
            end
        end
    end)

    if LocalPlayer.Character then
        LocalPlayer.Character.ChildAdded:Connect(function(child)
            if child:IsA("Tool") and isGun(child) then
                task.wait(0.1)
                watchShotsForTool(child)
                if ENABLED then tryReload(child) end
            end
        end)
    end

    scanAllTools()

    return {
        enable = function()
            ENABLED = true
            scanAllTools()
            local char = LocalPlayer.Character
            if char then
                for _, tool in ipairs(char:GetChildren()) do
                    if tool:IsA("Tool") and isGun(tool) then tryReload(tool) end
                end
            end
        end,
        disable = function()
            ENABLED = false
        end,
        isEnabled = function() return ENABLED end,
        setAutoHolster = function(state) AUTO_HOLSTER = state end,
    }
end)()

-- 1. 自动换弹（修复版）
OfficerTab:Toggle({
    Title = G.ToggleOfficerReloadTitle,
    Desc = G.ToggleOfficerReloadDesc,
    Value = false,
    Callback = function(state)
        if state then
            AutoReload.enable()
        else
            AutoReload.disable()
        end
    end
})

-- 2. 新增：换弹后自动收枪再装备（0.1秒）
OfficerTab:Toggle({
    Title = "换弹完成后自动重新装备武器",
    Desc = "每装填一发子弹后自动收回枪械再装备",
    Value = false,
    Callback = function(state)
        AutoReload.setAutoHolster(state)
    end
})

-- 3. 自动黑枪（原样保留）
OfficerTab:Toggle({
    Title = G.ToggleOfficerBlackGunTitle,
    Desc = G.ToggleOfficerBlackGunDesc,
    Value = false,
    Callback = function(state)
        L.autoBlackGunEnabled = state
        L.updateShootingState()
    end
})

-- 4. 自动跳刀（原样保留）
OfficerTab:Toggle({
    Title = G.ToggleOfficerJumpTitle,
    Desc = G.ToggleOfficerJumpDesc,
    Value = false,
    Callback = function(state)
        setAutoJumpAnimEnabled(state)
    end
})

-- ==================== 自定义自动黑枪（储存方式同高频杀戮光环，性能优化版） ====================
L.customBlackGunEnabled = false
L.customBlackGunSmoothTime = 0.28
L.customBlackGunCooldown = 0.3
L.customBlackGunEquipDelay = 0.2
L.customBlackGunBarrelDistance = 14
L.customMaxTargetRange = 200
L.customWallCheckEnabled = true
L.customAimAnimDelay = 0.5
L.customShootingThread = nil

-- 节流缓存变量
L.customBlackGunLastScanTime = 0
L.customBlackGunCachedTarget = nil
L.customBlackGunCachedModel = nil
L.customBlackGunCacheValid = false

-- 清理缓存（L表函数）
function L.invalidateCustomCache()
    L.customBlackGunCacheValid = false
    L.customBlackGunCachedTarget = nil
    L.customBlackGunCachedModel = nil
end

-- 节流获取目标
function L.customGetTargetThrottled()
    local now = tick()
    if L.customBlackGunCacheValid and now - L.customBlackGunLastScanTime < 0.2 then
        return L.customBlackGunCachedTarget, L.customBlackGunCachedModel
    end
    L.customBlackGunLastScanTime = now
    local targetPart, targetModel = L.getNearestTargetHeadByMatcher(L.customMaxTargetRange, L.ZombieTypeMatchers.Bomber)
    L.customBlackGunCachedTarget = targetPart
    L.customBlackGunCachedModel = targetModel
    L.customBlackGunCacheValid = true
    return targetPart, targetModel
end

-- 核心射击执行（优化版，无耗时动画）
function L.customProcessBlackGunShoot()
    if not L.customBlackGunEnabled then return end
    
    local tool = lp.Character and lp.Character:FindFirstChildOfClass("Tool")
    if not tool or not L.isGun(tool) then return end
    
    local shots = L.getShotsLoadedForTool(tool)
    if shots < 1 then return end
    
    local targetPart, targetModel = L.customGetTargetThrottled()
    if not targetPart or not targetModel then return end
    
    if not L.isAnyOtherPlayerNearZombie(targetModel, L.customBlackGunBarrelDistance) then
        return
    end
    
    if L.customBlackGunEquipDelay > 0 then
        task.wait(L.customBlackGunEquipDelay)
    end
    
    if not tool.Parent or L.getShotsLoadedForTool(tool) < 1 then return end
    
    -- 简化转向与射击（不播放动画）
    local char = lp.Character
    if not char then return end
    local root = char:FindFirstChild("HumanoidRootPart")
    if root and targetPart then
        if L.customBlackGunSmoothTime <= 0.05 then
            root.CFrame = CFrame.new(root.Position, Vector3.new(targetPart.Position.X, root.Position.Y, targetPart.Position.Z))
        else
            local startCF = root.CFrame
            local endCF = CFrame.new(root.Position, Vector3.new(targetPart.Position.X, root.Position.Y, targetPart.Position.Z))
            local duration = math.min(L.customBlackGunSmoothTime, 0.1)
            local startTime = tick()
            while tick() - startTime < duration do
                local t = (tick() - startTime) / duration
                root.CFrame = startCF:Lerp(endCF, t)
                task.wait()
            end
            root.CFrame = endCF
        end
    end
    
    local remote = tool:FindFirstChild("RemoteEvent")
    if remote then
        local modelRef = char:FindFirstChild("Model") or char
        local timestamp = workspace:GetServerTimeNow()
        pcall(function() remote:FireServer("Fire", modelRef, targetPart.Position, timestamp) end)
    end
end

-- 主循环（强制最小间隔0.2秒）
function L.customShootingLoop()
    local minWait = 0.2
    while L.customBlackGunEnabled do
        local start = tick()
        L.customProcessBlackGunShoot()
        local elapsed = tick() - start
        local waitTime = math.max(minWait, L.customBlackGunCooldown - elapsed)
        if waitTime > 0 then task.wait(waitTime) end
        L.invalidateCustomCache()
    end
end

function L.startCustomShooting()
    if L.customShootingThread then return end
    L.customShootingThread = task.spawn(L.customShootingLoop)
end

function L.stopCustomShooting()
    if L.customShootingThread then
        task.cancel(L.customShootingThread)
        L.customShootingThread = nil
    end
    L.invalidateCustomCache()
end

-- UI 控件
CustomOfficerTab:Toggle({
    Title = "自动黑枪",
    Desc = "可调参数自动黑枪（性能优化版）",
    Value = false,
    Callback = function(state)
        L.customBlackGunEnabled = state
        if state then
            L.startCustomShooting()
        else
            L.stopCustomShooting()
        end
    end
})

CustomOfficerTab:Slider({
    Title = "转向时间(秒)",
    Desc = "0 = 瞬瞄，数值越低越快",
    Value = { Min = 0, Max = 50, Default = 0.28, Decimal = 2 },
    Callback = function(v) L.customBlackGunSmoothTime = v end
})

CustomOfficerTab:Slider({
    Title = "射击间隔(秒)",
    Desc = "最小0.2秒，防止卡顿",
    Value = { Min = 0.2, Max = 50, Default = 0.3, Decimal = 2 },
    Callback = function(v) L.customBlackGunCooldown = v end
})

CustomOfficerTab:Slider({
    Title = "装备速度(秒)",
    Desc = "数值越低越快",
    Value = { Min = 0, Max = 50, Default = 0.2, Decimal = 2 },
    Callback = function(v) L.customBlackGunEquipDelay = v end
})

CustomOfficerTab:Slider({
    Title = "自爆检测距离",
    Desc = "检测自爆离玩家的距离",
    Value = { Min = 1, Max = 50, Default = 14 },
    Callback = function(v) L.customBlackGunBarrelDistance = v end
})

CustomOfficerTab:Slider({
    Title = "最大瞄准距离",
    Desc = "自动瞄准的最远距离",
    Value = { Min = 10, Max = 200, Default = 200 },
    Callback = function(v) L.customMaxTargetRange = v end
})

CustomOfficerTab:Toggle({
    Title = "墙体检测",
    Desc = "不会射击被墙体遮挡住的",
    Value = true,
    Callback = function(state) L.customWallCheckEnabled = state end
})

-- 其他自动射击开关（原版，保留）
AutoShootTab:Toggle({
    Title = G.ToggleAutoShootBomberTitle,
    Desc = G.ToggleAutoShootBomberDesc,
    Value = false,
    Callback = function(state)
        L.autoShootBomber = state
        L.updateShootingState()
    end
})

AutoShootTab:Toggle({
    Title = G.ToggleAutoShootCuirassierTitle,
    Desc = G.ToggleAutoShootCuirassierDesc,
    Value = false,
    Callback = function(state)
        L.autoShootCuirassier = state
        L.updateShootingState()
    end
})

AutoShootTab:Toggle({
    Title = G.ToggleAutoShootRunnerTitle,
    Desc = G.ToggleAutoShootRunnerDesc,
    Value = false,
    Callback = function(state)
        L.autoShootRunner = state
        L.updateShootingState()
    end
})

AutoShootTab:Toggle({
    Title = G.ToggleAutoShootElectrocutionerTitle,
    Desc = G.ToggleAutoShootElectrocutionerDesc,
    Value = false,
    Callback = function(state)
        L.autoShootElectrocutioner = state
        L.updateShootingState()
    end
})

-- ==================== 医生功能 ====================
L.doctorEnabled = false
L.doctorThreshold = 25
L.doctorRange = 10
L.doctorCooldown = 2
L.doctorLastRequest = {}
L.doctorThread = nil

local function doctorRequestHealForPlayer(player, humanoid)
    if not player or not humanoid then return end
    local healthPercent = (humanoid.Health / humanoid.MaxHealth) * 100
    if healthPercent > L.doctorThreshold then return end
    local now = tick()
    if (L.doctorLastRequest[player] or 0) + L.doctorCooldown > now then return end
    L.doctorLastRequest[player] = now
    local localChar = lp.Character
    if not localChar then return end
    local localRoot = localChar:FindFirstChild("HumanoidRootPart")
    if not localRoot then return end
    local targetRoot = humanoid.Parent:FindFirstChild("HumanoidRootPart") or humanoid.Parent:FindFirstChild("Torso")
    if not targetRoot then return end
    if (localRoot.Position - targetRoot.Position).Magnitude > L.doctorRange then return end
    local medSupplies = localChar:FindFirstChild("Medical Supplies")
    if not medSupplies then return end
    local remote = medSupplies:FindFirstChild("RemoteEvent")
    if not remote then return end
    pcall(function()
        remote:FireServer("SendRequest", humanoid)
    end)
end

local function doctorLoop()
    while L.doctorEnabled do
        for _, player in ipairs(Players:GetPlayers()) do
            if player ~= lp and player.Character then
                local humanoid = player.Character:FindFirstChildOfClass("Humanoid")
                if humanoid and humanoid.Health > 0 then
                    pcall(doctorRequestHealForPlayer, player, humanoid)
                end
            end
        end
        task.wait(0.5)
    end
end

DoctorTab:Toggle({
    Title = G.ToggleDoctorTitle,
    Desc = G.ToggleDoctorDesc,
    Value = false,
    Callback = function(state)
        L.doctorEnabled = state
        if state then
            if L.doctorThread then task.cancel(L.doctorThread) end
            L.doctorThread = task.spawn(doctorLoop)
            WindUI:Notify({ Title = "医生", Content = "自动治疗已开启", Duration = 2 })
        else
            if L.doctorThread then task.cancel(L.doctorThread); L.doctorThread = nil end
            L.doctorLastRequest = {}
            WindUI:Notify({ Title = "医生", Content = "自动治疗已关闭", Duration = 2 })
        end
    end
})

DoctorTab:Slider({
    Title = G.SliderDoctorThresholdTitle,
    Desc = G.SliderDoctorThresholdDesc,
    Value = { Min = 1, Max = 100, Default = 25 },
    Callback = function(value) L.doctorThreshold = value end
})

-- ==================== 牧师功能 ====================
L.chaplainEnabled = false
L.chaplainThreshold = 50
L.chaplainCooldown = 2
L.chaplainRange = 15
L.chaplainLastRequest = {}
L.chaplainThread = nil

local function getPlayerInfectionValue(player)
    local infection = 0
    pcall(function()
        local wsPlayers = workspace:FindFirstChild("Players")
        if wsPlayers then
            local folder = wsPlayers:FindFirstChild(player.Name)
            if folder and folder:FindFirstChild("UserStates") then
                local val = folder.UserStates:FindFirstChild("Infected")
                if val then infection = tonumber(val.Value) or 0 return end
            end
        end
        if player:FindFirstChild("UserStates") then
            local val = player.UserStates:FindFirstChild("Infected")
            if val then infection = tonumber(val.Value) or 0 end
        end
    end)
    return infection
end

local function getBlessRemote()
    local char = lp.Character
    if not char then return nil end
    local tool = char:FindFirstChild("Blessing")
    if tool and tool:FindFirstChild("RemoteEvent") then return tool.RemoteEvent end
    for _, child in ipairs(char:GetChildren()) do
        if child:IsA("Tool") and child.Name:lower():find("bless") and child:FindFirstChild("RemoteEvent") then
            return child.RemoteEvent
        end
    end
    return nil
end

local function inBlessRange(player)
    local localChar = lp.Character
    if not localChar then return false end
    local localRoot = localChar:FindFirstChild("HumanoidRootPart")
    if not localRoot then return false end
    if not player.Character then return false end
    local targetRoot = player.Character:FindFirstChild("HumanoidRootPart") or player.Character:FindFirstChild("Torso")
    if not targetRoot then return false end
    return (localRoot.Position - targetRoot.Position).Magnitude <= L.chaplainRange
end

local function sendBless(player, humanoid)
    if not player or not humanoid then return end
    local infection = getPlayerInfectionValue(player)
    if infection < L.chaplainThreshold then return end
    local now = tick()
    if (L.chaplainLastRequest[player] or 0) + L.chaplainCooldown > now then return end
    if not inBlessRange(player) then return end
    local remote = getBlessRemote()
    if not remote then return end
    pcall(function()
        remote:FireServer("SendRequest", humanoid)
        L.chaplainLastRequest[player] = now
    end)
end

local function chaplainLoop()
    while L.chaplainEnabled do
        for _, player in ipairs(Players:GetPlayers()) do
            if player ~= lp and player.Character then
                local humanoid = player.Character:FindFirstChildOfClass("Humanoid")
                if humanoid and humanoid.Health > 0 then
                    pcall(sendBless, player, humanoid)
                end
            end
        end
        task.wait(0.5)
    end
end

ChaplainTab:Toggle({
    Title = G.ToggleChaplainTitle,
    Desc = G.ToggleChaplainDesc,
    Value = false,
    Callback = function(state)
        L.chaplainEnabled = state
        if state then
            if L.chaplainThread then task.cancel(L.chaplainThread) end
            L.chaplainThread = task.spawn(chaplainLoop)
            WindUI:Notify({ Title = "牧师", Content = "自动祝福已开启", Duration = 2 })
        else
            if L.chaplainThread then task.cancel(L.chaplainThread); L.chaplainThread = nil end
            L.chaplainLastRequest = {}
            WindUI:Notify({ Title = "牧师", Content = "自动祝福已关闭", Duration = 2 })
        end
    end
})

ChaplainTab:Slider({
    Title = G.SliderChaplainThresholdTitle,
    Desc = G.SliderChaplainThresholdDesc,
    Value = { Min = 1, Max = 100, Default = 50 },
    Callback = function(value) L.chaplainThreshold = value end
})

-- ==================== 其他 ====================
local OtherSection = Window:Section({ Title = G.SectionOther, Opened = false })
local OtherTab = OtherSection:Tab({ Title = G.TabOther, Icon = "square" })

local EntertainmentTab = OtherSection:Tab({ Title = "娱乐", Icon = "gamepad" })

L.rollTiltEnabled = false
L.rollTiltSpeed = 3
L.rollTiltConn = nil
L.rollTiltHrp = nil
L.rollTiltRx = 0
L.rollTiltRz = 0
L.rollTiltLastUpdate = 0

function L.rollTiltStop()
    if L.rollTiltConn then
        L.rollTiltConn:Disconnect()
        L.rollTiltConn = nil
    end
    L.rollTiltEnabled = false
end

function L.rollTiltStart()
    if L.rollTiltEnabled then return end
    local char = lp.Character
    if not char then return end
    L.rollTiltHrp = char:FindFirstChild("HumanoidRootPart")
    if not L.rollTiltHrp then return end
    L.rollTiltEnabled = true
    L.rollTiltLastUpdate = 0
    L.rollTiltRx = 0
    L.rollTiltRz = 0
    L.rollTiltConn = RunService.RenderStepped:Connect(function()
        if not L.rollTiltEnabled or not L.rollTiltHrp or not L.rollTiltHrp.Parent then
            L.rollTiltStop()
            return
        end
        if tick() - L.rollTiltLastUpdate > 0.05 then
            L.rollTiltLastUpdate = tick()
            L.rollTiltRx = (math.random() - 0.5) * L.rollTiltSpeed * 0.15
            L.rollTiltRz = (math.random() - 0.5) * L.rollTiltSpeed * 0.15
        end
        L.rollTiltHrp.CFrame = L.rollTiltHrp.CFrame * CFrame.Angles(L.rollTiltRx, 0, L.rollTiltRz)
    end)
end

local function onCharacterAddedForRollTilt()
    if L.rollTiltEnabled then
        task.wait(0.2)
        local char = lp.Character
        if char then
            L.rollTiltHrp = char:FindFirstChild("HumanoidRootPart")
            if L.rollTiltConn then
                L.rollTiltConn:Disconnect()
                L.rollTiltConn = nil
            end
            L.rollTiltStart()
        end
    end
end
lp.CharacterAdded:Connect(onCharacterAddedForRollTilt)

task.spawn(function()
    while true do
        task.wait(5)
        if L.rollTiltEnabled and L.rollTiltConn and (not L.rollTiltHrp or not L.rollTiltHrp.Parent) then
            L.rollTiltStop()
            onCharacterAddedForRollTilt()
        end
    end
end)

-- ========== UI 控件 ==========
EntertainmentTab:Toggle({
    Title = "我好像有点卡顿",
    Desc = "让人物看起来卡卡的",
    Value = false,
    Callback = function(state)
        if state then L.rollTiltStart() else L.rollTiltStop() end
    end
})

EntertainmentTab:Slider({
    Title = "卡顿程度",
    Desc = "调整卡顿频率",
    Value = { Min = 1, Max = 10, Default = 3 },
    Callback = function(value)
        L.rollTiltSpeed = value
    end
})

-- ==================== 人物旋转功能（快速版） ====================
L.spin = {
    enabled = false,
    speed = 5,              -- 滑块值 1~10，实际速度 = speed * 350
    connection = nil,
    animLockThread = nil,
}

local function applySpinAnimationLock(char)
    if not char then return end
    local hum = char:FindFirstChildOfClass("Humanoid")
    if hum then
        hum.AutoRotate = false
    end
    if L.spin.animLockThread then
        task.cancel(L.spin.animLockThread)
        L.spin.animLockThread = nil
    end
    L.spin.animLockThread = task.spawn(function()
        local animate = char:WaitForChild("Animate", 3)
        while L.spin.enabled and animate and animate.Parent do
            animate.Disabled = true
            task.wait(0.2)
        end
    end)
end

local function removeSpinAnimationLock(char)
    if not char then return end
    local hum = char:FindFirstChildOfClass("Humanoid")
    if hum then
        hum.AutoRotate = true
    end
    if L.spin.animLockThread then
        task.cancel(L.spin.animLockThread)
        L.spin.animLockThread = nil
    end
    local animate = char:FindFirstChild("Animate")
    if animate then
        animate.Disabled = false
    end
end

local function startSpin()
    if L.spin.connection then return end
    L.spin.connection = RunService.RenderStepped:Connect(function(dt)
        if not L.spin.enabled then return end
        local char = lp.Character
        if not char then return end
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if not hrp then return end
        local realSpeed = L.spin.speed * 350
        local angularSpeedRad = math.rad(realSpeed)
        hrp.CFrame = hrp.CFrame * CFrame.Angles(0, angularSpeedRad * dt, 0)
    end)
    applySpinAnimationLock(lp.Character)
end

local function stopSpin()
    L.spin.enabled = false
    if L.spin.connection then
        L.spin.connection:Disconnect()
        L.spin.connection = nil
    end
    removeSpinAnimationLock(lp.Character)
end

lp.CharacterAdded:Connect(function(char)
    if L.spin.enabled then
        task.wait(0.5)
        applySpinAnimationLock(char)
        if not L.spin.connection then
            startSpin()
        end
    end
end)

EntertainmentTab:Toggle({
    Title = "旋转",
    Desc = "开机后让人物旋转",
    Value = false,
    Callback = function(state)
        L.spin.enabled = state
        if state then startSpin() else stopSpin() end
    end
})

EntertainmentTab:Slider({
    Title = "旋转速度",
    Desc = "开局后让人物旋转",
    Value = { Min = 1, Max = 10, Default = 5 },
    Increment = 1,
    Callback = function(value)
        L.spin.speed = value
    end
})

-- ==================== 强制第三人称功能（缩放上限200） ====================
L.thirdPerson = {
    enabled = false,
    connection = nil,
}

local function applyThirdPerson()
    pcall(function()
        if lp.CameraMode ~= Enum.CameraMode.Classic then
            lp.CameraMode = Enum.CameraMode.Classic
        end
        lp.CameraMinZoomDistance = 0.5
        lp.CameraMaxZoomDistance = 200   -- 修改为200
    end)
end

local function enableThirdPerson()
    if L.thirdPerson.connection then return end
    L.thirdPerson.enabled = true
    applyThirdPerson()
    L.thirdPerson.connection = RunService.RenderStepped:Connect(function()
        if not L.thirdPerson.enabled then return end
        applyThirdPerson()
    end)
end

local function disableThirdPerson()
    L.thirdPerson.enabled = false
    if L.thirdPerson.connection then
        L.thirdPerson.connection:Disconnect()
        L.thirdPerson.connection = nil
    end
end

lp.CharacterAdded:Connect(function()
    task.wait(0.5)
    if L.thirdPerson.enabled then
        applyThirdPerson()
    end
end)

EntertainmentTab:Toggle({
    Title = "解除视角限制",
    Desc = "开学后解除玩家视角上限",
    Value = false,
    Callback = function(state)
        if state then
            enableThirdPerson()
        else
            disableThirdPerson()
        end
    end
})

-- 跳跃高度30（直接锁定，无额外UI）
do
    local enabled = false
    local conn = nil
    local function lock()
        local hum = lp.Character and lp.Character:FindFirstChildOfClass("Humanoid")
        if hum then
            hum.JumpPower = 30
            if conn then conn:Disconnect() end
            conn = hum:GetPropertyChangedSignal("JumpPower"):Connect(function()
                if hum.JumpPower ~= 30 then hum.JumpPower = 30 end
            end)
        end
    end
    local function unlock()
        if conn then conn:Disconnect(); conn = nil end
        local hum = lp.Character and lp.Character:FindFirstChildOfClass("Humanoid")
        if hum then hum.JumpPower = 16 end
    end
    EntertainmentTab:Toggle({ Title = "移除跳跃限制", Value = false, Callback = function(s)
        enabled = s
        if s then lock() else unlock() end
    end })
    lp.CharacterAdded:Connect(function()
        if enabled then task.wait(0.2); lock() end
    end)
end

-- ==================== 全自动（莱比锡 + 修桥） ====================
local AutoAllSection = Window:Section({ Title = "全自动", Opened = false })

-- ==================== 莱比锡全自动（替换版，无杀戮光环） ====================
local LeipzigTab = AutoAllSection:Tab({ Title = "莱比锡", Icon = "rocket" })

-- 全局状态与配置（新脚本逻辑）
_G.Leipzig_Active = false
_G.forceBarrelApproach = false
_G.barrelApproachNoAxe = false
flySpeed = 37
currentNode = 1
doorMonitorActive = false      -- 默认关闭
bellMonitorActive = false      -- 默认关闭
showPathVisuals = false        -- 默认关闭

barPresent = false
burnPresent = false
gate1Present = false
gate2Present = false

bv, bg = nil, nil
_G.animCache = nil
_G.barrierBreakTime = nil
_G.Visuals = { Nodes = {}, Lines = {}, Folder = nil }

-- 路径数据（完整195个点，从用户原脚本中完整复制）
local rawPathData = {
    {pos = Vector3.new(112.608, 4.000, 7.510), name = "出生点"},
    {pos = Vector3.new(113.784, 4.000, 17.289), name = "未命名"},
    {pos = Vector3.new(109.569, 4.000, 30.568), name = "未命名"},
    {pos = Vector3.new(105.724, 4.000, 30.905), name = "未命名"},
    {pos = Vector3.new(105.371, 4.000, 40.672), name = "未命名"},
    {pos = Vector3.new(106.708, 10.483, 48.850), name = "未命名"},
    {pos = Vector3.new(73.481, 11.619, 51.646), name = "未命名"},
    {pos = Vector3.new(54.861, 11.757, 51.472), name = "未命名"},
    {pos = Vector3.new(17.236, 9.647, 6.967), name = "未命名"},
    {pos = Vector3.new(17.684, 2.962, 7.586), name = "未命名"},
    {pos = Vector3.new(17.759, 9.120, 6.582), name = "未命名"},
    {pos = Vector3.new(-0.412, 11.695, -21.690), name = "未命名"},
    {pos = Vector3.new(-79.715, 14.436, -30.243), name = "未命名"},
    {pos = Vector3.new(-106.164, 13.394, -31.947), name = "未命名"},
    {pos = Vector3.new(-106.666, 0.904, -30.485), name = "未命名"},
    {pos = Vector3.new(-114.202, 7.428, -32.034), name = "未命名"},
    {pos = Vector3.new(-119.024, -7.370, -32.756), name = "未命名"},
    {pos = Vector3.new(-118.312, 0.769, -33.250), name = "未命名"},
    {pos = Vector3.new(-144.415, -0.300, -84.711), name = "未命名"},
    {pos = Vector3.new(-149.080, -8.257, -92.784), name = "未命名"},
    {pos = Vector3.new(-150.454, -0.430, -96.291), name = "这是第一个地方，然后添加检测检测僵尸有没有没有把这个木板给弄到懂吧，然后没有的话就一直在这个地方等待着"},
    {pos = Vector3.new(-144.862, -0.241, -85.979), name = "移到这个坐标的话，就是怎么说这个地方就是假如说已经监听完成就继续嘛，继续的话就是从这边绕一波"},
    {pos = Vector3.new(-144.862, -0.241, -85.979), name = "未命名"},
    {pos = Vector3.new(-117.018, -0.5, -33.135), name = "未命名"},
    {pos = Vector3.new(-144.862, -0.241, -85.979), name = "未命名"},
    {pos = Vector3.new(-144.862, -0.241, -85.979), name = "未命名"},
    {pos = Vector3.new(-144.862, -0.241, -85.979), name = "未命名"},
    {pos = Vector3.new(-144.862, -0.241, -85.979), name = "未命名"},
    {pos = Vector3.new(-145.980, -0.508, -87.459), name = "未命名"},
    {pos = Vector3.new(-150.588, -7.863, -96.189), name = "未命名"},
    {pos = Vector3.new(-160.543, -4.607, -130.898), name = "未命名"},
    {pos = Vector3.new(-160.170, -4.162, -150.685), name = "未命名"},
    {pos = Vector3.new(-181.314, 5.673, -144.855), name = "未命名"},
    {pos = Vector3.new(-171.939, 5.091, -128.464), name = "未命名"},
    {pos = Vector3.new(-156.076, 5.058, -130.822), name = "未命名"},
    {pos = Vector3.new(-154.573, 5.835, -125.907), name = "未命名"},
    {pos = Vector3.new(-157.914, 5.861, -124.465), name = "未命名"},
    {pos = Vector3.new(-151.238, 5.426, -104.429), name = "未命名"},
    {pos = Vector3.new(-168.680, 5.549, -99.606), name = "这边开始推车"},
    {pos = Vector3.new(-170.959, 5.759, -98.769), name = "未命名"},
    {pos = Vector3.new(-171.093, 5.918, -98.728), name = "未命名"},
    {pos = Vector3.new(-172.278, 5.752, -98.810), name = "未命名"},
    {pos = Vector3.new(-174.644, 5.857, -98.107), name = "未命名"},
    {pos = Vector3.new(-177.038, 5.714, -97.541), name = "未命名"},
    {pos = Vector3.new(-178.857, 5.608, -96.529), name = "未命名"},
    {pos = Vector3.new(-180.744, 5.746, -96.334), name = "未命名"},
    {pos = Vector3.new(-183.637, 5.767, -95.837), name = "未命名"},
    {pos = Vector3.new(-186.658, 5.814, -95.098), name = "未命名"},
    {pos = Vector3.new(-189.801, 5.649, -94.268), name = "未命名"},
    {pos = Vector3.new(-192.921, 5.689, -93.533), name = "未命名"},
    {pos = Vector3.new(-196.140, 5.733, -92.836), name = "未命名"},
    {pos = Vector3.new(-199.207, 5.944, -91.963), name = "未命名"},
    {pos = Vector3.new(-202.395, 5.812, -91.268), name = "未命名"},
    {pos = Vector3.new(-205.217, 5.789, -90.721), name = "未命名"},
    {pos = Vector3.new(-208.499, 5.770, -90.169), name = "未命名"},
    {pos = Vector3.new(-210.708, 5.485, -89.951), name = "未命名"},
    {pos = Vector3.new(-213.395, 5.826, -89.390), name = "未命名"},
    {pos = Vector3.new(-216.455, 5.768, -88.920), name = "未命名"},
    {pos = Vector3.new(-219.212, 5.781, -88.471), name = "未命名"},
    {pos = Vector3.new(-222.481, 5.500, -87.724), name = "未命名"},
    {pos = Vector3.new(-225.423, 5.748, -87.162), name = "未命名"},
    {pos = Vector3.new(-228.579, 5.909, -86.429), name = "未命名"},
    {pos = Vector3.new(-231.864, 5.716, -85.960), name = "未命名"},
    {pos = Vector3.new(-234.817, 5.725, -85.706), name = "未命名"},
    {pos = Vector3.new(-237.430, 5.731, -85.143), name = "未命名"},
    {pos = Vector3.new(-240.502, 5.625, -85.084), name = "未命名"},
    {pos = Vector3.new(-243.297, 5.736, -85.074), name = "未命名"},
    {pos = Vector3.new(-246.522, 5.725, -85.040), name = "未命名"},
    {pos = Vector3.new(-249.445, 5.727, -84.612), name = "未命名"},
    {pos = Vector3.new(-252.427, 5.647, -84.140), name = "未命名"},
    {pos = Vector3.new(-252.639, 5.953, -84.003), name = "推车完毕，现在去拿火把"},
    {pos = Vector3.new(-253.298, 5.520, -72.179), name = "这个地方拿火把，然后全自动的"},
    {pos = Vector3.new(-253.125, 14.924, 2.861), name = "这个地方把火聚起来，然后循环重复，这是开始"},
    {pos = Vector3.new(-255.845, 10.759, -21.661), name = "继续"},
    {pos = Vector3.new(-265.845, 10.759, -53.000), name = "这里结束，然后这边的话就是循环重复监听火堆到底有没有销毁？如果说销毁的话就继续没有的话就重复"},
    {pos = Vector3.new(-244.725, 13.111, 4.166), name = "未命名"},
    {pos = Vector3.new(-252.514, 5.520, -83.536), name = "然后这边就开始推车"},
    {pos = Vector3.new(-256.918, 5.752, -83.287), name = "未命名"},
    {pos = Vector3.new(-259.607, 5.501, -82.997), name = "未命名"},
    {pos = Vector3.new(-262.058, 5.692, -81.538), name = "未命名"},
    {pos = Vector3.new(-264.885, 5.747, -81.301), name = "未命名"},
    {pos = Vector3.new(-267.714, 5.739, -80.620), name = "未命名"},
    {pos = Vector3.new(-270.100, 5.843, -80.527), name = "未命名"},
    {pos = Vector3.new(-273.462, 5.955, -79.456), name = "未命名"},
    {pos = Vector3.new(-276.173, 5.744, -78.616), name = "未命名"},
    {pos = Vector3.new(-278.221, 5.505, -78.470), name = "未命名"},
    {pos = Vector3.new(-281.647, 5.769, -77.454), name = "未命名"},
    {pos = Vector3.new(-285.371, 5.857, -76.524), name = "未命名"},
    {pos = Vector3.new(-289.299, 5.672, -75.490), name = "未命名"},
    {pos = Vector3.new(-292.674, 5.965, -74.732), name = "未命名"},
    {pos = Vector3.new(-296.171, 6.058, -73.854), name = "未命名"},
    {pos = Vector3.new(-299.429, 6.104, -73.159), name = "未命名"},
    {pos = Vector3.new(-303.217, 5.948, -71.885), name = "未命名"},
    {pos = Vector3.new(-306.442, 6.068, -71.585), name = "未命名"},
    {pos = Vector3.new(-309.409, 6.171, -70.320), name = "未命名"},
    {pos = Vector3.new(-312.679, 6.363, -69.606), name = "未命名"},
    {pos = Vector3.new(-316.051, 6.375, -68.481), name = "未命名"},
    {pos = Vector3.new(-318.827, 6.588, -67.451), name = "未命名"},
    {pos = Vector3.new(-322.090, 6.751, -66.507), name = "未命名"},
    {pos = Vector3.new(-324.709, 6.812, -65.588), name = "未命名"},
    {pos = Vector3.new(-327.758, 7.057, -64.280), name = "未命名"},
    {pos = Vector3.new(-330.711, 7.294, -62.893), name = "未命名"},
    {pos = Vector3.new(-333.701, 7.389, -61.594), name = "未命名"},
    {pos = Vector3.new(-336.217, 7.502, -61.006), name = "未命名"},
    {pos = Vector3.new(-338.043, 8.109, -60.399), name = "未命名"},
    {pos = Vector3.new(-340.952, 8.211, -58.815), name = "未命名"},
    {pos = Vector3.new(-343.892, 8.115, -57.157), name = "未命名"},
    {pos = Vector3.new(-346.813, 8.498, -55.699), name = "未命名"},
    {pos = Vector3.new(-349.736, 8.712, -54.695), name = "未命名"},
    {pos = Vector3.new(-353.261, 8.778, -53.519), name = "未命名"},
    {pos = Vector3.new(-355.801, 8.897, -53.126), name = "未命名"},
    {pos = Vector3.new(-358.594, 8.979, -51.620), name = "未命名"},
    {pos = Vector3.new(-360.804, 9.033, -51.067), name = "未命名"},
    {pos = Vector3.new(-363.373, 9.123, -49.750), name = "未命名"},
    {pos = Vector3.new(-366.251, 9.086, -49.084), name = "未命名"},
    {pos = Vector3.new(-368.332, 9.534, -48.207), name = "未命名"},
    {pos = Vector3.new(-372.037, 9.433, -47.214), name = "未命名"},
    {pos = Vector3.new(-374.601, 9.308, -46.055), name = "未命名"},
    {pos = Vector3.new(-377.486, 9.128, -44.847), name = "未命名"},
    {pos = Vector3.new(-379.371, 9.219, -44.845), name = "未命名"},
    {pos = Vector3.new(-382.507, 9.308, -44.290), name = "未命名"},
    {pos = Vector3.new(-384.352, 9.124, -43.873), name = "未命名"},
    {pos = Vector3.new(-387.433, 9.152, -43.663), name = "未命名"},
    {pos = Vector3.new(-390.110, 9.126, -42.967), name = "未命名"},
    {pos = Vector3.new(-392.959, 9.128, -42.746), name = "未命名"},
    {pos = Vector3.new(-395.268, 9.128, -43.114), name = "未命名"},
    {pos = Vector3.new(-397.196, 9.127, -43.340), name = "未命名"},
    {pos = Vector3.new(-399.023, 9.121, -43.427), name = "未命名"},
    {pos = Vector3.new(-401.824, 9.126, -44.577), name = "未命名"},
    {pos = Vector3.new(-403.100, 9.130, -44.734), name = "未命名"},
    {pos = Vector3.new(-404.350, 9.143, -45.311), name = "未命名"},
    {pos = Vector3.new(-405.688, 9.131, -46.635), name = "未命名"},
    {pos = Vector3.new(-407.186, 9.108, -47.111), name = "未命名"},
    {pos = Vector3.new(-409.040, 9.105, -48.005), name = "未命名"},
    {pos = Vector3.new(-410.431, 9.088, -49.019), name = "未命名"},
    {pos = Vector3.new(-412.107, 9.096, -49.887), name = "未命名"},
    {pos = Vector3.new(-413.852, 9.076, -50.368), name = "未命名"},
    {pos = Vector3.new(-415.579, 9.085, -51.210), name = "未命名"},
    {pos = Vector3.new(-417.600, 9.442, -53.360), name = "未命名"},
    {pos = Vector3.new(-419.525, 9.863, -56.109), name = "未命名"},
    {pos = Vector3.new(-420.006, 10.192, -56.196), name = "未命名"},
    {pos = Vector3.new(-420.886, 10.197, -57.036), name = "未命名"},
    {pos = Vector3.new(-421.868, 10.522, -59.157), name = "未命名"},
    {pos = Vector3.new(-423.721, 10.849, -60.736), name = "未命名"},
    {pos = Vector3.new(-425.334, 11.161, -62.684), name = "未命名"},
    {pos = Vector3.new(-426.980, 11.523, -64.363), name = "未命名"},
    {pos = Vector3.new(-429.045, 11.801, -65.701), name = "未命名"},
    {pos = Vector3.new(-430.340, 12.160, -67.621), name = "未命名"},
    {pos = Vector3.new(-431.825, 12.274, -69.213), name = "未命名"},
    {pos = Vector3.new(-432.919, 12.287, -70.459), name = "未命名"},
    {pos = Vector3.new(-434.435, 12.313, -71.981), name = "未命名"},
    {pos = Vector3.new(-436.053, 12.124, -73.474), name = "未命名"},
    {pos = Vector3.new(-437.369, 12.132, -75.049), name = "未命名"},
    {pos = Vector3.new(-438.699, 12.127, -76.443), name = "未命名"},
    {pos = Vector3.new(-440.178, 12.127, -77.519), name = "未命名"},
    {pos = Vector3.new(-441.871, 12.137, -78.840), name = "未命名"},
    {pos = Vector3.new(-443.438, 12.132, -80.038), name = "未命名"},
    {pos = Vector3.new(-445.134, 12.136, -81.134), name = "未命名"},
    {pos = Vector3.new(-446.787, 12.134, -82.019), name = "未命名"},
    {pos = Vector3.new(-448.170, 12.124, -82.865), name = "未命名"},
    {pos = Vector3.new(-449.750, 12.126, -83.856), name = "未命名"},
    {pos = Vector3.new(-451.652, 12.133, -85.020), name = "未命名"},
    {pos = Vector3.new(-452.592, 12.108, -85.799), name = "未命名"},
    {pos = Vector3.new(-455.804, 12.136, -87.218), name = "未命名"},
    {pos = Vector3.new(-457.543, 12.123, -88.249), name = "未命名"},
    {pos = Vector3.new(-458.874, 12.092, -89.345), name = "未命名"},
    {pos = Vector3.new(-461.736, 12.132, -90.762), name = "未命名"},
    {pos = Vector3.new(-462.695, 12.104, -91.597), name = "未命名"},
    {pos = Vector3.new(-463.723, 12.122, -92.448), name = "未命名"},
    {pos = Vector3.new(-465.200, 12.135, -93.215), name = "未命名"},
    {pos = Vector3.new(-467.233, 12.120, -93.955), name = "未命名"},
    {pos = Vector3.new(-468.914, 12.122, -94.491), name = "未命名"},
    {pos = Vector3.new(-470.876, 12.129, -95.391), name = "未命名"},
    {pos = Vector3.new(-472.753, 12.355, -96.774), name = "未命名"},
    {pos = Vector3.new(-475.252, 12.631, -97.828), name = "到了这个的地方的话，就要拿火把"},
    {pos = Vector3.new(-496.046, 25.789, -79.268), name = "来完之后来这个地方，然后监听大门是否被销毁，或者大门一"},
    {pos = Vector3.new(-455.092, 22.360, -207.741), name = "未命名"},
    {pos = Vector3.new(-411.704, 27.936, -220.358), name = "未命名"},
    {pos = Vector3.new(-432.517, 29.192, -248.808), name = "未命名"},
    {pos = Vector3.new(-441.985, 25.365, -256.952), name = "未命名"},
    {pos = Vector3.new(-445.323, 25.735, -265.871), name = "未命名"},
    {pos = Vector3.new(-451.181, 25.817, -262.703), name = "未命名"},
    {pos = Vector3.new(-457.225, 24.922, -242.069), name = "然后到这个地方来自动拉铃铛，不用管"},
    {pos = Vector3.new(-451.254, 26.000, -261.491), name = "未命名"},
    {pos = Vector3.new(-444.658, 25.582, -265.542), name = "未命名"},
    {pos = Vector3.new(-442.324, 25.083, -254.689), name = "未命名"},
    {pos = Vector3.new(-432.496, 29.635, -248.949), name = "未命名"},
    {pos = Vector3.new(-412.162, 28.227, -220.879), name = "未命名"},
    {pos = Vector3.new(-455.053, 23.123, -207.364), name = "未命名"},
    {pos = Vector3.new(-538.271, 23.048, -202.133), name = "拉完铃铛之后，就在这个地方开始重复，直到监听到大门二被销毁"},
    {pos = Vector3.new(-538.707, 24.301, -227.237), name = "未命名"},
    {pos = Vector3.new(-557.775, 23.239, -223.573), name = "未命名"},
    {pos = Vector3.new(-552.224, 21.478, -198.853), name = "未命名"},
    {pos = Vector3.new(-537.974, 23.179, -201.909), name = "这边就重复这样，然后这是终点，然后等到大门二销毁，然后就继续结束，然后就继续行走"},
    {pos = Vector3.new(-523.146, 12.490, -129.481), name = "未命名"},
    {pos = Vector3.new(-558.333, 19.813, -120.550), name = "未命名"},
    {pos = Vector3.new(-616.322, 15.516, -102.790), name = "未命名"},
    {pos = Vector3.new(-624.839, 13.364, -98.975), name = "未命名"},
    {pos = Vector3.new(-640.742, 23.166, -92.965), name = "未命名"},
    {pos = Vector3.new(-651.036, 27.296, -126.735), name = "未命名"},
    {pos = Vector3.new(-672.055, 27.263, -123.549), name = "未命名"},
    {pos = Vector3.new(-640.983, 20.738, 3.615), name = "未命名"},
    {pos = Vector3.new(-760.795, 24.030, 39.349), name = "然后这边到终点结束"},
}
PathData = {}
for i, point in ipairs(rawPathData) do
    local newPoint = {pos = point.pos, name = point.name}
    if i ~= 190 and i ~= 194 then
        local nameLower = point.name:lower()
        if nameLower:find("木板") or nameLower:find("僵尸") then
            newPoint.waitFor = "noBarricade"
        elseif nameLower:find("火堆") and nameLower:find("销毁") then
            newPoint.waitFor = "noBurn"
        elseif nameLower:find("大门一") or nameLower:find("大门1") or (nameLower:find("大门") and nameLower:find("被销毁") and not nameLower:find("二")) then
            newPoint.waitFor = "noGate1"
        elseif nameLower:find("大门二") or nameLower:find("大门2") then
            newPoint.waitFor = "noGate2"
        end
    end
    table.insert(PathData, newPoint)
end

-- 辅助函数
local function getNearestNode(myPos)
    local closest = 1; local dist = math.huge
    for i, v in ipairs(PathData) do
        local d = (myPos - v.pos).Magnitude
        if d < dist then dist = d; closest = i end
    end
    return closest
end

local function ensurePhysics(hrp, hum)
    if hrp:FindFirstChild("LeipzigBV") then hrp.LeipzigBV:Destroy() end
    if hrp:FindFirstChild("LeipzigBG") then hrp.LeipzigBG:Destroy() end
    bv = Instance.new("BodyVelocity", hrp)
    bv.Name = "LeipzigBV"
    bv.MaxForce = Vector3.new(1e6, 1e6, 1e6)
    bg = Instance.new("BodyGyro", hrp)
    bg.Name = "LeipzigBG"
    bg.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
    bg.P = 10000
    bg.D = 50
    local char = hrp.Parent
    local animate = char:FindFirstChild("Animate")
    if animate then
        _G.animCache = animate
        animate.Parent = nil
    end
end

local function cleanupPhysics()
    local char = lp.Character
    if char then
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if hrp then
            if hrp:FindFirstChild("LeipzigBV") then hrp.LeipzigBV:Destroy() end
            if hrp:FindFirstChild("LeipzigBG") then hrp.LeipzigBG:Destroy() end
        end
        if _G.animCache and _G.animCache.Parent == nil then
            _G.animCache.Parent = char
        end
    end
    bv, bg, _G.animCache = nil, nil, nil
end

local function checkCondition(condition)
    if condition == "noBarricade" then return not barPresent
    elseif condition == "noBurn" then return not burnPresent
    elseif condition == "noGate1" then return not gate1Present
    elseif condition == "noGate2" then return not gate2Present end
    return true
end

-- 可视化
local function createPathVisuals()
    if _G.Visuals.Folder then _G.Visuals.Folder:Destroy() end
    _G.Visuals.Folder = Instance.new("Folder", Workspace)
    _G.Visuals.Folder.Name = "LeipzigPathVisuals"
    for i, point in ipairs(PathData) do
        local node = Instance.new("Part", _G.Visuals.Folder)
        node.Size = Vector3.new(0.8, 0.8, 0.8)
        node.Position = point.pos
        node.Anchored = true
        node.CanCollide = false
        node.Material = Enum.Material.Neon
        node.Color = (i == currentNode) and Color3.new(0,1,0) or Color3.new(1,1,0)
        node.Name = "Node_"..i
        table.insert(_G.Visuals.Nodes, node)
        if i > 1 then
            local prevPos = PathData[i-1].pos
            local mid = (prevPos + point.pos)/2
            local dist = (prevPos - point.pos).Magnitude
            local line = Instance.new("Part", _G.Visuals.Folder)
            line.Size = Vector3.new(0.15,0.15,dist)
            line.CFrame = CFrame.new(mid, point.pos)
            line.Anchored = true
            line.CanCollide = false
            line.Material = Enum.Material.Neon
            line.Color = Color3.new(1,0,0)
            line.Name = "Line_"..i
            table.insert(_G.Visuals.Lines, line)
        end
    end
end

local function destroyPathVisuals()
    if _G.Visuals.Folder then
        _G.Visuals.Folder:Destroy()
        _G.Visuals.Folder = nil
        _G.Visuals.Nodes = {}
        _G.Visuals.Lines = {}
    end
end

local function updateNodeColors()
    for i, node in ipairs(_G.Visuals.Nodes) do
        if node and node.Parent then
            node.Color = (i == currentNode) and Color3.new(0,1,0) or Color3.new(1,1,0)
        end
    end
end

-- 武器管理模块（仅用于拿火把/斧头，无攻击）
local function findTool(names)
    if type(names) == "string" then names = {names} end
    local char = lp.Character
    local backpack = lp.Backpack
    for _, name in ipairs(names) do
        local tool = backpack:FindFirstChild(name) or (char and char:FindFirstChild(name))
        if tool then return tool end
    end
    return nil
end

local function equipTool(tool)
    if not tool then return end
    local char = lp.Character
    local hum = char and char:FindFirstChildOfClass("Humanoid")
    local rightArm = char and char:FindFirstChild("Right Arm")
    if hum and rightArm then
        hum:EquipTool(tool)
        local remote = tool:FindFirstChild("RemoteEvent")
        if remote then remote:FireServer("Equip", rightArm) end
    end
end

local function unequipTool(tool)
    if not tool then return end
    if tool.Parent == lp.Character then tool.Parent = lp.Backpack end
end

local function ensureWeapon(weaponName, shouldEquip)
    local names = weaponName == "Torch" and {"Torch"} or {"Sapper Axe", "Axe"}
    local tool = findTool(names)
    if shouldEquip then
        if tool and tool.Parent ~= lp.Character then equipTool(tool) end
    else
        if tool and tool.Parent == lp.Character then unequipTool(tool) end
    end
end

weaponActions = {
    [21] = function()
        task.spawn(function()
            ensureWeapon("Axe", false)
            ensureWeapon("Sapper Axe", false)
            ensureWeapon("Torch", false)
        end)
    end,
    [72] = function() task.spawn(function() task.wait(0.8) ensureWeapon("Torch", true) end) end,
    [73] = function() task.spawn(function() task.wait(0.3) ensureWeapon("Torch", true) end) end,
    [74] = function() task.spawn(function() task.wait(0.4) ensureWeapon("Torch", true) end) end,
    [75] = function() task.spawn(function() task.wait(0.3) ensureWeapon("Torch", true) end) end,    
    [76] = function() task.spawn(function()  ensureWeapon("Axe", true) end) end,
    [174] = function() task.spawn(function() ensureWeapon("Torch", true) end) end,
    [175] = function() task.spawn(function() ensureWeapon("Torch", true) end) end,
    [176] = function() task.spawn(function() ensureWeapon("Torch", false); ensureWeapon("Axe", true) end) end,
}

-- 僵尸相关（仅用于识别，无攻击）
ZOMBIE_FOLDERS = {"Zombies"}
local function getAllZombies()
    local list = {}
    for _, fname in ipairs(ZOMBIE_FOLDERS) do
        local f = Workspace:FindFirstChild(fname)
        if f then
            for _, z in ipairs(f:GetChildren()) do
                if z:IsA("Model") and z:FindFirstChildOfClass("Humanoid", true) then
                    table.insert(list, z)
                end
            end
        end
    end
    return list
end

local function getZombieType(z)
    if z:FindFirstChild("Barrel") then return "Barrel" end
    local attr = z:GetAttribute("Type")
    if attr then return attr end
    local name = z.Name
    if name:find("Barrel") then return "Barrel"
    elseif name:find("Fast") then return "Fast"
    elseif name:find("Igniter") then return "Igniter"
    elseif name:find("Sapper") then return "Sapper"
    else return "Normal" end
end

local function isAttackable(z) return true end

local function getNearestZombiePart()
    local char = lp.Character
    local root = char and char:FindFirstChild("HumanoidRootPart")
    if not root then return nil end
    local zombies = getAllZombies()
    local nearest = nil
    local minDist = math.huge
    for _, z in ipairs(zombies) do
        if not isAttackable(z) then continue end
        local hrp = z:FindFirstChild("HumanoidRootPart", true)
        if hrp then
            local dist = (root.Position - hrp.Position).Magnitude
            if dist <= 45 and dist < minDist then
                minDist = dist
                nearest = z
            end
        end
    end
    if not nearest then return nil end
    return nearest:FindFirstChild("HumanoidRootPart", true) or nearest:FindFirstChild("Head", true)
end

local function getAllBarrels(radius)
    local barrels = {}
    local char = lp.Character
    local root = char and char:FindFirstChild("HumanoidRootPart")
    if not root then return barrels end
    for _, z in ipairs(getAllZombies()) do
        if getZombieType(z) == "Barrel" then
            local hrp = z:FindFirstChild("HumanoidRootPart", true)
            if hrp and (root.Position - hrp.Position).Magnitude <= radius then
                table.insert(barrels, {zombie = z, hrp = hrp})
            end
        end
    end
    return barrels
end

-- 自动飞行核心线程（无攻击）
barrelState = {}
cleaningNode174 = false
wobbleOffset = 0
prevNode = 0
returnMode = false
returnPos = nil
lastTriggerNode = nil
lastTeleportTime = 0
lastRecordedPos = nil
stuckStart = nil

local function isTeleportDisabled(node)
    return node == 24 or (node >= 73 and node <= 75) or (node >= 190 and node <= 194)
end

flyThread = task.spawn(function()
    while true do
        if _G.Leipzig_Active then
            local char = lp.Character
            local hrp = char and char:FindFirstChild("HumanoidRootPart")
            local hum = char and char:FindFirstChild("Humanoid")
            if hrp and hum then
                ensurePhysics(hrp, hum)
                if not lastRecordedPos then lastRecordedPos = hrp.Position end

                local target = PathData[currentNode]
                if target then
                    local baseSpeed = flySpeed
                    if currentNode == 24 then
                        local count = 0
                        for _, z in ipairs(getAllZombies()) do
                            if isAttackable(z) then
                                local hrpz = z:FindFirstChild("HumanoidRootPart", true)
                                if hrpz and (hrp.Position - hrpz.Position).Magnitude <= 20 then
                                    count = count + 1
                                end
                            end
                        end
                        if count == 0 then baseSpeed = 21 else baseSpeed = math.max(1, 6 - count) end
                    elseif currentNode == 109 or currentNode == 104 then
                        baseSpeed = 21
                    elseif currentNode == 201 or currentNode == 202 then
                        baseSpeed = 25
                    end
                    if currentNode >= 72 and currentNode <= 76 then
                        baseSpeed = burnPresent and 50 or flySpeed
                    end
                    if currentNode >= 190 and currentNode <= 194 and gate2Present then
                        baseSpeed = 15
                    end
                    local currentFlySpeed = baseSpeed

                    local isPushingCart = (currentNode >= 39 and currentNode <= 71) or (currentNode >= 78 and currentNode <= 172)
                    local isListeningStage = (currentNode == 21 or currentNode == 22)

                    for z, t in pairs(barrelState) do
                        if not z or z.Parent == nil or (z:FindFirstChild("Humanoid") and z.Humanoid.Health <= 0) then
                            barrelState[z] = nil
                        end
                    end

                    local shouldCheckBarrel = false
                    local barrelRadius = 0
                    if isListeningStage then
                        shouldCheckBarrel = true
                        barrelRadius = 8
                    elseif isPushingCart then
                        shouldCheckBarrel = true
                        barrelRadius = 25
                    end

                    local barrels = {}
                    if shouldCheckBarrel then
                        barrels = getAllBarrels(barrelRadius)
                    end

                    local untriggered = {}
                    local triggered = {}
                    for _, b in ipairs(barrels) do
                        if barrelState[b.zombie] then
                            table.insert(triggered, b)
                        else
                            table.insert(untriggered, b)
                        end
                    end

                    local skip = false

                    if not skip and #untriggered > 0 and (isListeningStage or isPushingCart or _G.forceBarrelApproach) then
                        local chosen = nil
                        local minDist = math.huge
                        for _, b in ipairs(untriggered) do
                            local d = (hrp.Position - b.hrp.Position).Magnitude
                            if d < minDist then
                                minDist = d
                                chosen = b
                            end
                        end
                        if chosen then
                            local distToBarrel = (hrp.Position - chosen.hrp.Position).Magnitude
                            task.spawn(function() ensureWeapon("Axe", true) end)
                            if distToBarrel > 0.5 then
                                bv.Velocity = (chosen.hrp.Position - hrp.Position).Unit * 60
                                bg.CFrame = CFrame.lookAt(hrp.Position, chosen.hrp.Position)
                                hum:ChangeState(Enum.HumanoidStateType.Climbing)
                                skip = true
                            else
                                returnPos = hrp.Position
                                lastTriggerNode = currentNode
                                barrelState[chosen.zombie] = tick()
                                _G.forceBarrelApproach = false
                            end
                        else
                            _G.forceBarrelApproach = false
                        end
                    end

                    if #triggered > 0 then
                        local now = tick()
                        for i = #triggered, 1, -1 do
                            local b = triggered[i]
                            if now - barrelState[b.zombie] > 6 then
                                barrelState[b.zombie] = nil
                                table.remove(triggered, i)
                            end
                        end
                    end
                    if not skip and #triggered > 0 then
                        local awayDir = Vector3.new(0,0,0)
                        for _, b in ipairs(triggered) do
                            awayDir = awayDir + (hrp.Position - b.hrp.Position).Unit
                        end
                        awayDir = awayDir.Unit
                        local safePos = hrp.Position + awayDir * 30
                        local hoverPos = Vector3.new(safePos.X, safePos.Y + 10, safePos.Z)
                        local moveDir = hoverPos - hrp.Position
                        if moveDir.Magnitude > 2 then
                            bv.Velocity = moveDir.Unit * 35
                        else
                            bv.Velocity = Vector3.new(0, 0.01, 0)
                        end
                        local lookTarget = getNearestZombiePart() or (triggered[1] and triggered[1].hrp)
                        if lookTarget then
                            bg.CFrame = CFrame.lookAt(hrp.Position, lookTarget.Position)
                        end
                        task.spawn(function() ensureWeapon("Axe", true) end)
                        hum:ChangeState(Enum.HumanoidStateType.Climbing)
                        skip = true
                    end

                    if not skip and isPushingCart then
                        local nearbyCount = 0
                        local zombies = getAllZombies()
                        for _, z in ipairs(zombies) do
                            if isAttackable(z) then
                                local hrpz = z:FindFirstChild("HumanoidRootPart", true)
                                if hrpz and (hrp.Position - hrpz.Position).Magnitude <= 10 then
                                    nearbyCount = nearbyCount + 1
                                end
                            end
                        end
                        local targetZombie = nil
                        if nearbyCount >= 3 then
                            local minDist = math.huge
                            for _, z in ipairs(zombies) do
                                if isAttackable(z) then
                                    local hrpz = z:FindFirstChild("HumanoidRootPart", true)
                                    if hrpz then
                                        local dist = (hrp.Position - hrpz.Position).Magnitude
                                        if dist <= 25 and dist < minDist then
                                            minDist = dist
                                            targetZombie = hrpz
                                        end
                                    end
                                end
                            end
                        else
                            local minDist = math.huge
                            for _, z in ipairs(zombies) do
                                if getZombieType(z) == "Fast" then
                                    local hrpz = z:FindFirstChild("HumanoidRootPart", true)
                                    if hrpz then
                                        local dist = (hrp.Position - hrpz.Position).Magnitude
                                        if dist <= 25 and dist < minDist then
                                            minDist = dist
                                            targetZombie = hrpz
                                        end
                                    end
                                end
                            end
                        end
                        if targetZombie then
                            local hoverPos = targetZombie.Position + Vector3.new(0, 10, 0)
                            local moveDir = hoverPos - hrp.Position
                            if moveDir.Magnitude > 1.8 then
                                bv.Velocity = moveDir.Unit * 60
                            else
                                wobbleOffset = wobbleOffset + 0.5
                                bv.Velocity = Vector3.new(math.sin(wobbleOffset)*2, 0.01, math.cos(wobbleOffset)*2)
                            end
                            bg.CFrame = CFrame.lookAt(hrp.Position, targetZombie.Position)
                            hum:ChangeState(Enum.HumanoidStateType.Climbing)
                            skip = true
                        end
                    end

                    if not skip and #triggered == 0 and returnPos ~= nil and not returnMode then
                        returnMode = true
                    end

                    if not skip and returnMode then
                        local moveDir = returnPos - hrp.Position
                        local dist = moveDir.Magnitude
                        if dist > 1.2 then
                            bv.Velocity = moveDir.Unit * 60
                            bg.CFrame = CFrame.lookAt(hrp.Position, returnPos)
                            hum:ChangeState(Enum.HumanoidStateType.Climbing)
                            skip = true
                        else
                            returnMode = false
                            returnPos = nil
                            if lastTriggerNode then
                                currentNode = lastTriggerNode
                                lastTriggerNode = nil
                            end
                        end
                    end

                    if not skip and isPushingCart and #triggered == 0 and not returnMode then
                        local distToTarget = (hrp.Position - target.pos).Magnitude
                        local speed = bv.Velocity.Magnitude
                        if distToTarget > 20 and speed < 1 then
                            local now = tick()
                            if now - lastTeleportTime > 2 then
                                local teleportPos = returnPos or target.pos
                                if teleportPos then
                                    hrp.CFrame = CFrame.new(teleportPos)
                                    lastTeleportTime = now
                                    task.wait(0.5)
                                    lastRecordedPos = hrp.Position
                                    stuckStart = nil
                                end
                            end
                        end
                    end

                    if not skip and currentNode == 174 then
                        local zombiesNear = {}
                        for _, z in ipairs(getAllZombies()) do
                            if isAttackable(z) then
                                local hrpz = z:FindFirstChild("HumanoidRootPart", true)
                                if hrpz and (target.pos - hrpz.Position).Magnitude <= 30 then
                                    table.insert(zombiesNear, z)
                                end
                            end
                        end
                        if #zombiesNear > 0 then
                            cleaningNode174 = true
                            local targetZombie = nil
                            local minDist = math.huge
                            for _, z in ipairs(zombiesNear) do
                                local hrpz = z:FindFirstChild("HumanoidRootPart", true)
                                if hrpz then
                                    local d = (target.pos - hrpz.Position).Magnitude
                                    if d < minDist then
                                        minDist = d
                                        targetZombie = hrpz
                                    end
                                end
                            end
                            if targetZombie then
                                local hoverPos = targetZombie.Position + Vector3.new(0, 5, 0)
                                local moveDir = hoverPos - hrp.Position
                                if moveDir.Magnitude > 1.8 then
                                    bv.Velocity = moveDir.Unit * 35
                                else
                                    wobbleOffset = wobbleOffset + 0.5
                                    bv.Velocity = Vector3.new(math.sin(wobbleOffset)*2, 0.01, math.cos(wobbleOffset)*2)
                                end
                                bg.CFrame = CFrame.lookAt(hrp.Position, targetZombie.Position)
                                hum:ChangeState(Enum.HumanoidStateType.Climbing)
                                skip = true
                            end
                        else
                            if cleaningNode174 then
                                cleaningNode174 = false
                                currentNode = 174
                            end
                        end
                    end

                    if not skip then
                        local skipMove = false
                        if not isTeleportDisabled(currentNode) then
                            local currentPos = hrp.Position
                            local moveDist = (currentPos - lastRecordedPos).Magnitude
                            lastRecordedPos = currentPos
                            if moveDist < 0.5 then
                                if not stuckStart then
                                    stuckStart = tick()
                                elseif tick() - stuckStart > 3 then
                                    local teleportPos = target.pos
                                    hrp.CFrame = CFrame.new(teleportPos)
                                    task.wait(0.5)
                                    stuckStart = nil
                                    lastRecordedPos = hrp.Position
                                    skipMove = true
                                end
                            else
                                stuckStart = nil
                            end
                        else
                            lastRecordedPos = hrp.Position
                            stuckStart = nil
                        end

                        if not skipMove then
                            local lookTarget = getNearestZombiePart()
                            local moveDir = (target.pos - hrp.Position)
                            local dist = moveDir.Magnitude
                            if dist > 1.2 then
                                bv.Velocity = moveDir.Unit * currentFlySpeed
                                if lookTarget then
                                    bg.CFrame = CFrame.lookAt(hrp.Position, Vector3.new(lookTarget.Position.X, lookTarget.Position.Y, lookTarget.Position.Z))
                                else
                                    bg.CFrame = CFrame.new(Vector3.zero, moveDir)
                                end
                                hum:ChangeState(Enum.HumanoidStateType.Climbing)
                            else
                                local oldNode = prevNode
                                if currentNode ~= prevNode then
                                    if weaponActions[currentNode] then
                                        weaponActions[currentNode]()
                                    else
                                        task.spawn(function() ensureWeapon("Axe", true) end)
                                    end
                                    prevNode = currentNode
                                end
                                wobbleOffset = wobbleOffset + 0.5
                                bv.Velocity = Vector3.new(math.sin(wobbleOffset)*2, 0.01, math.cos(wobbleOffset)*2)
                                if lookTarget then
                                    bg.CFrame = CFrame.lookAt(hrp.Position, Vector3.new(lookTarget.Position.X, lookTarget.Position.Y, lookTarget.Position.Z))
                                end
                                hum:ChangeState(Enum.HumanoidStateType.Climbing)
                                if currentNode == 175 then task.wait(0.35) end
                                local nextNode = currentNode + 1
                                if currentNode == 194 and gate2Present then nextNode = 190
                                elseif currentNode == 75 then nextNode = burnPresent and 74 or 76
                                elseif currentNode == 74 then
                                    if oldNode == 75 then nextNode = 73
                                    elseif oldNode == 73 then nextNode = 75 end
                                else
                                    if target.waitFor and not checkCondition(target.waitFor) then
                                        nextNode = currentNode
                                        task.wait(0.1)
                                    end
                                end
                                if nextNode ~= currentNode then currentNode = nextNode end
                            end
                        end
                    end
                end
            end
        end
        RunService.RenderStepped:Wait()
    end
end)

-- 自动开门线程
ProcessingDoors = {}
doorMonitorThread = task.spawn(function()
    while true do
        if doorMonitorActive then
            local char = lp.Character; local root = char and char:FindFirstChild("HumanoidRootPart")
            if root then
                for _, item in pairs(Workspace:GetDescendants()) do
                    if item.Name == "Main" and item:IsA("Model") then
                        if (root.Position - item:GetModelCFrame().Position).Magnitude <= 23 then
                            local isOpen = item:GetAttribute("Open")
                            if isOpen == nil then pcall(function() isOpen = item.Open end) end
                            if isOpen == false then
                                local mainPart = item:FindFirstChild("Main")
                                local remote = mainPart and mainPart:FindFirstChild("Interact")
                                if remote and remote:IsA("RemoteEvent") and not ProcessingDoors[item] then
                                    ProcessingDoors[item] = true
                                    task.spawn(function() remote:FireServer(); task.wait(0); ProcessingDoors[item] = nil end)
                                end
                            end
                        end
                    end
                end
            end
        end
        task.wait(0)
    end
end)

-- 状态检测线程（木板、火堆、大门、铃铛）
lastBarPresent = false
bellMonitorThread = task.spawn(function()
    while true do
        if bellMonitorActive then
            local char = lp.Character
            local root = char and char:FindFirstChild("HumanoidRootPart")
            barPresent = Workspace:FindFirstChild("Barricade", true) ~= nil
            burnPresent = Workspace:FindFirstChild("BURN", true) ~= nil
            gate1Present = Workspace:FindFirstChild("Gate1", true) ~= nil
            local gate2Model = Workspace:FindFirstChild("Leipzig") and Workspace.Leipzig:FindFirstChild("Modes") and Workspace.Leipzig.Modes:FindFirstChild("Objective") and Workspace.Leipzig.Modes.Objective:FindFirstChild("Gate2")
            if gate2Model then
                local hasParts = false
                for _, child in ipairs(gate2Model:GetDescendants()) do
                    if child:IsA("BasePart") then hasParts = true; break end
                end
                gate2Present = hasParts
            else gate2Present = false end

            if lastBarPresent == true and barPresent == false then
                _G.forceBarrelApproach = true
                _G.barrelApproachNoAxe = true
            end
            lastBarPresent = barPresent

            local success, bellObj = pcall(function() return Workspace.Leipzig.Modes.Objective.BellInteract end)
            if success and bellObj and root then
                local bellPart = bellObj:IsA("BasePart") and bellObj or bellObj:FindFirstChildWhichIsA("BasePart", true)
                if bellPart and (root.Position - bellPart.Position).Magnitude <= 14 then
                    pcall(function() bellObj.Interact:FireServer() end)
                    task.wait(0)
                end
            end
        end
        task.wait(0.3)
    end
end)

-- 自动拿火把
ProximityPromptService = game:GetService("ProximityPromptService")
promptCoroutines = {}
ProximityPromptService.PromptShown:Connect(function(prompt)
    if prompt.ActionText == "Take Torch" then
        local pid = tostring(prompt:GetDebugId())
        if promptCoroutines[pid] then coroutine.close(promptCoroutines[pid]) end
        promptCoroutines[pid] = coroutine.create(function()
            while prompt and prompt.Parent and prompt.Enabled do
                task.wait(0.01)
                prompt:InputHoldBegin()
                task.wait(prompt.HoldDuration + 0.02)
                prompt:InputHoldEnd()
                task.wait(0.01)
            end
        end)
        coroutine.resume(promptCoroutines[pid])
    end
end)

-- 莱比锡 UI 控件（所有开关默认关闭）
LeipzigTab:Toggle({
    Title = "开启飞行",
    Desc = "自动飞行完成任务",
    Value = false,
    Callback = function(state)
        _G.Leipzig_Active = state
        if state then
            local hrp = lp.Character and lp.Character:FindFirstChild("HumanoidRootPart")
            if hrp then currentNode = getNearestNode(hrp.Position) end
            if showPathVisuals then createPathVisuals(); updateNodeColors() end
        else
            cleanupPhysics()
            if showPathVisuals then destroyPathVisuals() end
        end
    end
})

LeipzigTab:Slider({
    Title = "飞行速度",
    Desc = "控制自动飞行的移动速度",
    Value = { Min = 10, Max = 100, Default = 37 },
    Callback = function(value) flySpeed = value end
})

LeipzigTab:Toggle({
    Title = "自动开门",
    Desc = "自动开启场景中的门",
    Value = false,
    Callback = function(state) doorMonitorActive = state end
})

LeipzigTab:Toggle({
    Title = "路径显示",
    Desc = "显示飞行路径",
    Value = false,
    Callback = function(state)
        showPathVisuals = state
        if state then
            if _G.Leipzig_Active then createPathVisuals(); updateNodeColors() end
        else
            destroyPathVisuals()
        end
    end
})

LeipzigTab:Toggle({
    Title = "自动拉铃铛",
    Desc = "靠近铃铛时自动交互",
    Value = false,
    Callback = function(state) bellMonitorActive = state end
})

-- ==================== 我也不知道（动态修桥，包含自动拿木头、自动放置木头、自动修桥） ====================
UnknownTab = AutoAllSection:Tab({ Title = "别列津纳", Icon = "hammer" })

-- 修桥脚本的核心状态（半自动修桥专用，完全保留）
bridgeIsRunning = false
bridgeMainLoopThread = nil
bridgeTeleportLoopConnection = nil
bridgeIsTeleporting = false
bridgeTeleportTargetPosition = nil
bridgeCurrentStep = "检查修理"
bridgeRepairingInProgress = false
bridgeWoodCache = {}
bridgeWoodCacheValid = false
bridgeWoodCacheTime = 0
bridgeCurrentTargetLog = nil
bridgeOriginalGravity = workspace.Gravity
bridgeSafeFallThreshold = 50

-- 辅助函数：检测是否拿着木材
local function bridgeIsHoldingLog()
    local char = lp.Character
    if not char then return false end
    for _, obj in ipairs(char:GetChildren()) do
        if obj:IsA("Tool") and obj.Name == "Log" then
            return true
        end
    end
    return false
end

-- 获取地面高度
local function bridgeGetGroundHeight(position)
    local rayOrigin = Vector3.new(position.X, position.Y + 10, position.Z)
    local rayDirection = Vector3.new(0, -1000, 0)
    local raycastParams = RaycastParams.new()
    raycastParams.FilterType = Enum.RaycastFilterType.Blacklist
    if lp.Character then raycastParams.FilterDescendantsInstances = {lp.Character} end
    local raycastResult = workspace:Raycast(rayOrigin, rayDirection, raycastParams)
    if raycastResult then return raycastResult.Position.Y end
    return nil
end

-- 安全传送（单次）
local function bridgeSafeTeleport(targetPosition)
    local char = lp.Character
    if not char then return false end
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return false end
    local groundHeight = bridgeGetGroundHeight(targetPosition)
    local adjustedPos
    if groundHeight then
        adjustedPos = Vector3.new(targetPosition.X, groundHeight + 1.5, targetPosition.Z)
    else
        adjustedPos = targetPosition
    end
    root.CFrame = CFrame.new(adjustedPos)
    return true
end

-- 停止传送循环
local function bridgeStopTeleportLoop()
    if bridgeTeleportLoopConnection then
        bridgeTeleportLoopConnection:Disconnect()
        bridgeTeleportLoopConnection = nil
    end
    bridgeIsTeleporting = false
    bridgeTeleportTargetPosition = nil
end

-- 启动传送循环
local function bridgeStartTeleportLoop(targetPosition)
    bridgeStopTeleportLoop()
    local groundHeight = bridgeGetGroundHeight(targetPosition)
    local adjustedPos
    if groundHeight then
        local maxHeight = groundHeight + 5
        local desiredY = targetPosition.Y
        adjustedPos = Vector3.new(targetPosition.X, math.min(desiredY, maxHeight), targetPosition.Z)
    else
        adjustedPos = targetPosition
    end
    bridgeIsTeleporting = true
    bridgeTeleportTargetPosition = adjustedPos
    bridgeTeleportLoopConnection = RunService.Heartbeat:Connect(function()
        local char = lp.Character
        if not char or not bridgeIsRunning then
            bridgeStopTeleportLoop()
            return
        end
        local root = char:FindFirstChild("HumanoidRootPart")
        if not root then
            bridgeStopTeleportLoop()
            return
        end
        local currentRot = root.CFrame - root.CFrame.Position
        root.CFrame = CFrame.new(bridgeTeleportTargetPosition) * currentRot
        root.AssemblyLinearVelocity = Vector3.new()
        root.AssemblyAngularVelocity = Vector3.new()
    end)
end

-- 动态扫描木材
local function bridgeDynamicScanWood()
    if bridgeWoodCacheValid and tick() - bridgeWoodCacheTime < 1 then
        return bridgeWoodCache
    end
    local berezina = workspace:FindFirstChild("Berezina")
    if not berezina then return {} end
    local modes = berezina:FindFirstChild("Modes")
    if not modes then return {} end
    local holdout = modes:FindFirstChild("Holdout")
    if not holdout then return {} end
    local logsFolder = holdout:FindFirstChild("Log")
    if not logsFolder then return {} end
    local newCache = {}
    for _, item in ipairs(logsFolder:GetChildren()) do
        if item.Name == "Log" then
            table.insert(newCache, { object = item, position = item.Position or Vector3.new() })
        end
    end
    bridgeWoodCache = newCache
    bridgeWoodCacheValid = true
    bridgeWoodCacheTime = tick()
    return newCache
end

-- 查找最近木材
local function bridgeFindNearestLog()
    local char = lp.Character
    if not char then return nil, 0, Vector3.new() end
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return nil, 0, Vector3.new() end
    local woodList = bridgeDynamicScanWood()
    if #woodList == 0 then return nil, 0, Vector3.new() end
    if bridgeCurrentTargetLog then
        for _, woodData in ipairs(woodList) do
            if woodData.object == bridgeCurrentTargetLog then
                local pos = woodData.object.Position or woodData.object:GetModelCFrame().Position
                local dist = (root.Position - pos).Magnitude
                return woodData.object, dist, pos
            end
        end
        bridgeCurrentTargetLog = nil
    end
    local nearestLog, nearestDist, nearestPos = nil, math.huge, Vector3.new()
    for _, woodData in ipairs(woodList) do
        local pos = woodData.object.Position or woodData.object:GetModelCFrame().Position
        local dist = (root.Position - pos).Magnitude
        if dist < nearestDist then
            nearestDist, nearestLog, nearestPos = dist, woodData.object, pos
        end
    end
    if nearestLog then bridgeCurrentTargetLog = nearestLog end
    return nearestLog, nearestDist, nearestPos
end

-- 查找放置位置
local function bridgeFindPlacePosition()
    local char = lp.Character
    if not char then return nil, 0 end
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return nil, 0 end
    local bridgeFolder = workspace:FindFirstChild("Berezina") and workspace.Berezina:FindFirstChild("Modes") and workspace.Berezina.Modes:FindFirstChild("Holdout") and workspace.Berezina.Modes.Holdout:FindFirstChild("Bridge")
    if not bridgeFolder then return nil, 0 end
    local nearestPos, nearestDist = nil, math.huge
    for _, section in pairs(bridgeFolder:GetChildren()) do
        if section.Name:match("^BridgeSection%d+$") then
            for _, child in pairs(section:GetDescendants()) do
                if child.Name == "PlaceLogProximityPrompt" then
                    local parent = child.Parent
                    local pos = parent.Position
                    local dist = (root.Position - pos).Magnitude
                    if dist < nearestDist then
                        nearestDist, nearestPos = dist, pos
                    end
                end
            end
        end
    end
    return nearestPos, nearestDist
end

-- 检测是否需要修理
local function bridgeCheckNeedRepair()
    local bridgeRoot = workspace:FindFirstChild("Berezina")
    if not bridgeRoot then return nil end
    local bridgeFolder = bridgeRoot:FindFirstChild("Modes") and bridgeRoot.Modes:FindFirstChild("Holdout") and bridgeRoot.Modes.Holdout:FindFirstChild("Bridge")
    if not bridgeFolder then return nil end
    local char = lp.Character
    if not char then return nil end
    local root = char:FindFirstChild("HumanoidRootPart")
    if not root then return nil end
    local repairPos = nil
    local nearestDist = math.huge
    for _, section in pairs(bridgeFolder:GetChildren()) do
        if section.Name:match("^BridgeSection%d+$") then
            local posts = section:FindFirstChild("Posts")
            if posts then
                for _, part in pairs(posts:GetChildren()) do
                    if part:IsA("BasePart") or part:IsA("Model") then
                        local health = part:FindFirstChild("ConstructHealth")
                        if health and health:IsA("NumberValue") then
                            local pos = part.Position or part:GetModelCFrame().Position
                            local dist = (root.Position - pos).Magnitude
                            if dist < nearestDist then
                                nearestDist, repairPos = dist, pos
                            end
                        end
                    end
                end
            end
            local beam = section:FindFirstChild("Beam")
            if beam then
                local health = beam:FindFirstChild("ConstructHealth")
                if health and health:IsA("NumberValue") then
                    local pos = beam.Position or beam:GetModelCFrame().Position
                    local dist = (root.Position - pos).Magnitude
                    if dist < nearestDist then
                        nearestDist, repairPos = dist, pos
                    end
                end
            end
            for _, child in pairs(section:GetChildren()) do
                if child.Name == "Joists" then
                    local health = child:FindFirstChild("ConstructHealth")
                    if health and health:IsA("NumberValue") then
                        local pos = child.Position or child:GetModelCFrame().Position
                        local dist = (root.Position - pos).Magnitude
                        if dist < nearestDist then
                            nearestDist, repairPos = dist, pos
                        end
                    end
                end
            end
        end
    end
    return repairPos
end

-- 去修理
local function bridgeGoRepair()
    local repairPos = bridgeCheckNeedRepair()
    if not repairPos then
        bridgeRepairingInProgress = false
        return false
    end
    local groundHeight = bridgeGetGroundHeight(repairPos)
    local targetPos = groundHeight and Vector3.new(repairPos.X, groundHeight + 1.5, repairPos.Z) or repairPos
    bridgeStartTeleportLoop(targetPos)
    bridgeRepairingInProgress = true
    local startTime = tick()
    while bridgeIsRunning and tick() - startTime < 5 do
        if tick() - startTime > 1 then
            local stillNeed = bridgeCheckNeedRepair()
            if not stillNeed then
                bridgeStopTeleportLoop()
                bridgeRepairingInProgress = false
                return true
            end
        end
        RunService.Heartbeat:Wait()
    end
    bridgeStopTeleportLoop()
    if bridgeCheckNeedRepair() then
        bridgeRepairingInProgress = true
        return false
    else
        bridgeRepairingInProgress = false
        return true
    end
end

-- 获取木材
local function bridgeGetLog()
    if not bridgeIsRunning then return false end
    bridgeCurrentStep = "获取木材"
    local log, logDist, logPos = bridgeFindNearestLog()
    if not log then return false end
    local groundHeight = bridgeGetGroundHeight(logPos)
    local targetPos = groundHeight and Vector3.new(logPos.X, math.min(logPos.Y + 0.5, groundHeight + 3), logPos.Z) or Vector3.new(logPos.X, logPos.Y + 0.5, logPos.Z)
    bridgeStartTeleportLoop(targetPos)
    local targetLog = log
    local startTime = tick()
    while bridgeIsRunning and tick() - startTime < 3 do
        if not targetLog or not targetLog.Parent then
            bridgeStopTeleportLoop()
            if bridgeIsHoldingLog() then
                bridgeCurrentStep = "检查修理"
                return true
            else
                bridgeCurrentTargetLog = nil
                return false
            end
        end
        if bridgeIsHoldingLog() then
            bridgeStopTeleportLoop()
            bridgeCurrentStep = "检查修理"
            return true
        end
        RunService.Heartbeat:Wait()
    end
    bridgeStopTeleportLoop()
    bridgeCurrentStep = "检查修理"
    return false
end

-- 放置木材
local function bridgePlaceLog()
    if not bridgeIsRunning then return false end
    bridgeCurrentStep = "放置木材"
    local placePos, placeDist = bridgeFindPlacePosition()
    if not placePos then
        bridgeCurrentStep = "检查修理"
        return false
    end
    local groundHeight = bridgeGetGroundHeight(placePos)
    local targetPos = groundHeight and Vector3.new(placePos.X, groundHeight + 1, placePos.Z) or placePos
    bridgeStartTeleportLoop(targetPos)
    local startTime = tick()
    while bridgeIsRunning and tick() - startTime < 3 do
        if not bridgeIsHoldingLog() then
            bridgeStopTeleportLoop()
            bridgeCurrentStep = "检查修理"
            return true
        end
        RunService.Heartbeat:Wait()
    end
    bridgeStopTeleportLoop()
    bridgeCurrentStep = "检查修理"
    return false
end

-- 主循环
local function bridgeMainLoop()
    while true do
        if bridgeIsRunning then
            if bridgeCurrentStep == "检查修理" then
                local needRepair = bridgeCheckNeedRepair()
                if needRepair then
                    bridgeGoRepair()
                else
                    if bridgeIsHoldingLog() then
                        bridgeCurrentStep = "放置木材"
                    else
                        bridgeCurrentStep = "获取木材"
                    end
                end
            elseif bridgeCurrentStep == "获取木材" then
                bridgeGetLog()
            elseif bridgeCurrentStep == "放置木材" then
                bridgePlaceLog()
            end
        end
        RunService.Heartbeat:Wait()
    end
end

-- 启动/停止修桥（半自动）
local function bridgeStart()
    if bridgeMainLoopThread then coroutine.close(bridgeMainLoopThread) end
    bridgeMainLoopThread = coroutine.create(bridgeMainLoop)
    coroutine.resume(bridgeMainLoopThread)
end

local function bridgeStop()
    bridgeIsRunning = false
    bridgeStopTeleportLoop()
    bridgeCurrentStep = "检查修理"
    bridgeRepairingInProgress = false
end

-- 原有的半自动修桥开关（完全保留）
UnknownTab:Toggle({
    Title = "开启自动修桥［半自动］",
    Desc = "自动获取木材",
    Value = false,
    Callback = function(state)
        bridgeIsRunning = state
        if state then
            bridgeStart()
        else
            bridgeStop()
        end
    end
})

-- ==================== 以下是替换为第二个脚本的三个功能（自动拿木头、自动放置木头、自动修桥） ====================
-- 注意：这些开关与上面的半自动修桥独立，可以同时使用

-- 1. 自动拿木头（从第二个脚本提取）
L.autoFeatures.autoLog = L.autoFeatures.autoLog or { active = false, connection = nil }
UnknownTab:Toggle({
    Title = G.ToggleAutoLogTitle,
    Desc = G.ToggleAutoLogDesc,
    Value = false,
    Callback = function(state)
        L.autoFeatures.autoLog.active = state
        if state then
            if L.autoFeatures.autoLog.connection then task.cancel(L.autoFeatures.autoLog.connection) end
            L.autoFeatures.autoLog.connection = task.spawn(function()
                while L.autoFeatures.autoLog.active do
                    local remoteEvent = workspace:FindFirstChild("Berezina") and workspace.Berezina:FindFirstChild("Modes") and workspace.Berezina.Modes:FindFirstChild("Holdout") and workspace.Berezina.Modes.Holdout:FindFirstChild("Log") and workspace.Berezina.Modes.Holdout.Log:FindFirstChild("Log") and workspace.Berezina.Modes.Holdout.Log.Log:FindFirstChild("Interact")
                    if remoteEvent and remoteEvent:IsA("RemoteEvent") then
                        pcall(function() remoteEvent:FireServer() end)
                    end
                    task.wait(0.05)
                end
            end)
        else
            if L.autoFeatures.autoLog.connection then
                task.cancel(L.autoFeatures.autoLog.connection)
                L.autoFeatures.autoLog.connection = nil
            end
        end
    end
})

-- 2. 自动放置木头（从第二个脚本提取）
L.autoFeatures.autoPlace = L.autoFeatures.autoPlace or { active = false, connection = nil }
UnknownTab:Toggle({
    Title = G.ToggleAutoPlaceTitle,
    Desc = G.ToggleAutoPlaceDesc,
    Value = false,
    Callback = function(state)
        L.autoFeatures.autoPlace.active = state
        if state then
            if L.autoFeatures.autoPlace.connection then task.cancel(L.autoFeatures.autoPlace.connection) end
            L.autoFeatures.autoPlace.connection = task.spawn(function()
                while L.autoFeatures.autoPlace.active do
                    for _, prompt in pairs(workspace:GetDescendants()) do
                        if prompt:IsA("ProximityPrompt") and prompt.Name == "PlaceLogProximityPrompt" then
                            pcall(function() fireproximityprompt(prompt) end)
                        end
                    end
                    task.wait(0.1)
                end
            end)
        else
            if L.autoFeatures.autoPlace.connection then
                task.cancel(L.autoFeatures.autoPlace.connection)
                L.autoFeatures.autoPlace.connection = nil
            end
        end
    end
})

-- 3. 自动修桥（从第二个脚本提取，注意与上面的半自动修桥不同，这个是高频检测版）
local function getNearestConstruct()
    local char = lp.Character
    if not char or not char:FindFirstChild("HumanoidRootPart") then return nil end
    local root = char.HumanoidRootPart
    local bridge = workspace:FindFirstChild("Berezina") and workspace.Berezina:FindFirstChild("Modes") and workspace.Berezina.Modes:FindFirstChild("Holdout") and workspace.Berezina.Modes.Holdout:FindFirstChild("Bridge")
    if not bridge then return nil end
    local nearest, dist = nil, math.huge
    for _, section in ipairs(bridge:GetChildren()) do
        if section:IsA("Model") then
            local posts = section:FindFirstChild("Posts")
            if posts then
                for _, part in ipairs(posts:GetChildren()) do
                    if part:IsA("BasePart") and part:FindFirstChild("ConstructHealth") then
                        local d = (part.Position - root.Position).Magnitude
                        if d < dist then dist = d; nearest = part.ConstructHealth end
                    end
                end
            end
            local beam = section:FindFirstChild("Beam")
            if beam and beam:FindFirstChild("ConstructHealth") then
                local d = (beam.Position - root.Position).Magnitude
                if d < dist then dist = d; nearest = beam.ConstructHealth end
            end
            for _, child in ipairs(section:GetChildren()) do
                if child.Name == "Joists" and child:FindFirstChild("ConstructHealth") then
                    local d = (child.Position - root.Position).Magnitude
                    if d < dist then dist = d; nearest = child.ConstructHealth end
                end
            end
        end
    end
    return nearest
end

local function doRepairBridge()
    local target = getNearestConstruct()
    if not target then return end
    local hammer = lp.Backpack:FindFirstChild("Hammer") or lp.Backpack:FindFirstChild("Claw Hammer")
    if not hammer or not hammer:FindFirstChild("RemoteEvent") then return end
    hammer.RemoteEvent:FireServer("Repair", target)
end

L.autoFeatures.autoRepairBridge = L.autoFeatures.autoRepairBridge or { active = false, connection = nil }
UnknownTab:Toggle({
    Title = G.ToggleAutoRepairBridgeTitle,
    Desc = G.ToggleAutoRepairBridgeDesc,
    Value = false,
    Callback = function(state)
        L.autoFeatures.autoRepairBridge.active = state
        if state then
            if L.autoFeatures.autoRepairBridge.connection then L.autoFeatures.autoRepairBridge.connection:Disconnect() end
            L.autoFeatures.autoRepairBridge.connection = RunService.Heartbeat:Connect(doRepairBridge)
        else
            if L.autoFeatures.autoRepairBridge.connection then
                L.autoFeatures.autoRepairBridge.connection:Disconnect()
                L.autoFeatures.autoRepairBridge.connection = nil
            end
        end
    end
})

-- ==================== 原有其他功能（不变） ====================
-- 解锁成就军团
OtherTab:Toggle({
    Title = "解锁成就军团",
    Desc = "解锁成就军团",
    Value = false,
    Callback = function(state)
        if state then
            local remote = game:GetService("ReplicatedStorage"):FindFirstChild("Events")
            if remote then
                remote = remote:FindFirstChild("UnlockAchievement")
            end
            if remote then
                remote:FireServer("Legion")
                WindUI:Notify({ Title = "解锁成就军团", Content = "解锁成就军团", Duration = 2 })
            else
                WindUI:Notify({ Title = "解锁成就军团", Content = "出现未知错误", Duration = 2, Type = "error" })
            end
        else
            WindUI:Notify({ Title = "解锁成就军团", Content = "出现未知错误", Duration = 1 })
        end
    end
})

-- 降低火焰性能
L.fixFireConn = nil

local function setFireEnabled(enabled)
    for _, obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("ParticleEmitter") and obj.Name:lower():find("fire") then
            obj.Enabled = enabled
            if not enabled then
                obj.Rate = 0
            else
                obj.Rate = 20
            end
        end
    end
end

local function toggleFixFire(enable)
    if enable then
        setFireEnabled(false)
        if not L.fixFireConn then
            L.fixFireConn = workspace.DescendantAdded:Connect(function(desc)
                if desc:IsA("ParticleEmitter") and desc.Name:lower():find("fire") then
                    desc.Enabled = false
                    desc.Rate = 0
                end
            end)
        end
        WindUI:Notify({ Title = "降低火焰性能", Content = "已开启（火焰粒子已禁用）", Duration = 2 })
    else
        if L.fixFireConn then
            L.fixFireConn:Disconnect()
            L.fixFireConn = nil
        end
        setFireEnabled(true)
        WindUI:Notify({ Title = "禁用火焰粒子", Content = "已关闭禁用火焰粒子", Duration = 2 })
    end
end

OtherTab:Toggle({
    Title = "禁用部分火焰粒子",
    Desc = "禁用部分火焰粒子",
    Value = false,
    Callback = function(state)
        toggleFixFire(state)
    end
})

-- 自爆范围显示
L.bombRangeEnabled = false
L.bombRangeSpheres = {}
L.bombRangeDamageDisplay = nil
L.bombRangeConnection = nil

local SPHERE_RADIUS = 10
local SPHERE_COLOR = Color3.fromRGB(255, 80, 80)
local SPHERE_TRANSPARENCY = 0.6
local DAMAGE_THRESHOLD = 20
local Y_OFFSET = -1.5

function L.getBarrelZombies()
    local barrels = {}
    local zombiesFolder = Workspace:FindFirstChild("Zombies")
    if not zombiesFolder then return barrels end
    for _, zombie in pairs(zombiesFolder:GetChildren()) do
        if zombie:IsA("Model") and zombie:GetAttribute("Type") == "Barrel" then
            table.insert(barrels, zombie)
        end
    end
    return barrels
end

function L.getSphereCenter(zombie)
    local root = zombie:FindFirstChild("HumanoidRootPart") or zombie:FindFirstChild("Torso") or zombie:FindFirstChild("Head")
    if root then
        return root.Position + Vector3.new(0, Y_OFFSET, 0)
    end
    return nil
end

function L.createSphere(zombie)
    local center = L.getSphereCenter(zombie)
    if not center then return nil end
    local sphere = Instance.new("Part")
    sphere.Name = "BombRangeSphere"
    sphere.Shape = Enum.PartType.Ball
    sphere.Size = Vector3.new(SPHERE_RADIUS * 2, SPHERE_RADIUS * 2, SPHERE_RADIUS * 2)
    sphere.BrickColor = BrickColor.new(SPHERE_COLOR)
    sphere.Color = SPHERE_COLOR
    sphere.Material = Enum.Material.Neon
    sphere.Transparency = SPHERE_TRANSPARENCY
    sphere.Anchored = true
    sphere.CanCollide = false
    sphere.CanQuery = false
    sphere.CanTouch = false
    sphere.CastShadow = false
    sphere.Position = center
    sphere.Parent = workspace
    return sphere
end

function L.updateSphere(sphere, zombie)
    if not sphere or not zombie then return end
    local center = L.getSphereCenter(zombie)
    if center then
        sphere.Position = center
        if sphere.Size.X ~= SPHERE_RADIUS * 2 then
            sphere.Size = Vector3.new(SPHERE_RADIUS * 2, SPHERE_RADIUS * 2, SPHERE_RADIUS * 2)
        end
    end
end

function L.updateAllSpheres()
    if not L.bombRangeEnabled then return end
    local barrels = L.getBarrelZombies()
    local currentBarrelSet = {}
    for _, z in ipairs(barrels) do currentBarrelSet[z] = true end
    for zombie, sphere in pairs(L.bombRangeSpheres) do
        if not zombie.Parent or not currentBarrelSet[zombie] then
            if sphere then sphere:Destroy() end
            L.bombRangeSpheres[zombie] = nil
        end
    end
    for _, zombie in ipairs(barrels) do
        if not L.bombRangeSpheres[zombie] then
            local sphere = L.createSphere(zombie)
            if sphere then L.bombRangeSpheres[zombie] = sphere end
        else
            L.updateSphere(L.bombRangeSpheres[zombie], zombie)
        end
    end
end

function L.clearAllSpheres()
    for _, sphere in pairs(L.bombRangeSpheres) do
        if sphere then sphere:Destroy() end
    end
    L.bombRangeSpheres = {}
end

function L.getMinDistanceToBarrelCenter()
    local char = lp.Character
    if not char then return math.huge end
    local playerPos = char:FindFirstChild("HumanoidRootPart")
    if not playerPos then return math.huge end
    local minDist = math.huge
    local barrels = L.getBarrelZombies()
    for _, zombie in ipairs(barrels) do
        local center = L.getSphereCenter(zombie)
        if center then
            local dist = (center - playerPos.Position).Magnitude
            if dist < minDist then minDist = dist end
        end
    end
    return minDist
end

function L.calculateDamage(distance)
    if distance >= SPHERE_RADIUS then return 0 end
    local factor = 1 - (distance / SPHERE_RADIUS)
    local damage = 10 + (100 - 10) * factor
    return math.floor(damage)
end

function L.updateDamageDisplay()
    if not L.bombRangeEnabled then
        if L.bombRangeDamageDisplay then L.bombRangeDamageDisplay:Destroy(); L.bombRangeDamageDisplay = nil end
        return
    end
    local char = lp.Character
    if not char then
        if L.bombRangeDamageDisplay then L.bombRangeDamageDisplay:Destroy(); L.bombRangeDamageDisplay = nil end
        return
    end
    local minDistance = L.getMinDistanceToBarrelCenter()
    local damage = 0
    if minDistance <= SPHERE_RADIUS then
        damage = L.calculateDamage(minDistance)
    end
    if damage > 0 then
        if not L.bombRangeDamageDisplay then
            local billboard = Instance.new("BillboardGui")
            billboard.Name = "DamageDisplay"
            billboard.Size = UDim2.new(0, 100, 0, 40)
            billboard.StudsOffset = Vector3.new(0, 2.5, 0)
            billboard.AlwaysOnTop = true
            billboard.Parent = char
            local label = Instance.new("TextLabel")
            label.Size = UDim2.new(1, 0, 1, 0)
            label.BackgroundTransparency = 1
            label.TextSize = 24
            label.Font = Enum.Font.GothamBold
            label.TextStrokeTransparency = 0.2
            label.TextStrokeColor3 = Color3.fromRGB(0,0,0)
            label.Parent = billboard
            L.bombRangeDamageDisplay = billboard
        end
        local label = L.bombRangeDamageDisplay:FindFirstChildOfClass("TextLabel")
        if label then
            label.Text = tostring(damage)
            if damage <= DAMAGE_THRESHOLD then
                label.TextColor3 = Color3.fromRGB(255, 255, 0)
            else
                label.TextColor3 = Color3.fromRGB(255, 0, 0)
            end
        end
    else
        if L.bombRangeDamageDisplay then
            L.bombRangeDamageDisplay:Destroy()
            L.bombRangeDamageDisplay = nil
        end
    end
end

function L.onBombRangeHeartbeat()
    if not L.bombRangeEnabled then return end
    L.updateAllSpheres()
    L.updateDamageDisplay()
end

function L.startBombRange()
    if L.bombRangeConnection then return end
    L.bombRangeConnection = RunService.Heartbeat:Connect(L.onBombRangeHeartbeat)
end

function L.stopBombRange()
    if L.bombRangeConnection then
        L.bombRangeConnection:Disconnect()
        L.bombRangeConnection = nil
    end
    L.clearAllSpheres()
    if L.bombRangeDamageDisplay then L.bombRangeDamageDisplay:Destroy(); L.bombRangeDamageDisplay = nil end
end

OtherTab:Toggle({
    Title = G.ToggleBombRangeTitle,
    Desc = G.ToggleBombRangeDesc,
    Value = false,
    Callback = function(state)
        L.bombRangeEnabled = state
        if state then
            L.startBombRange()
            L.onBombRangeHeartbeat()
        else
            L.stopBombRange()
        end
    end
})

-- ==================== 碰飞模式 ====================
L.flyOffEnabled = false
L.flyOffTarget = nil
L.flyOffOriginalCFrame = nil

function L.findPlayerByText(text)
    text = text:lower()
    for _, plr in pairs(Players:GetPlayers()) do
        if string.find(plr.Name:lower(), text) or string.find(plr.DisplayName:lower(), text) then
            return plr
        end
    end
    return nil
end

chattedConn = lp.Chatted:Connect(function(msg)
    if not L.flyOffEnabled then return end
    if msg:sub(1,6):lower() == ";kill " then
        local name = msg:sub(7)
        local plr = L.findPlayerByText(name)
        if plr and plr.Character and plr.Character:FindFirstChild("Humanoid") then
            L.flyOffTarget = plr
            if lp.Character and lp.Character:FindFirstChild("HumanoidRootPart") then
                L.flyOffOriginalCFrame = lp.Character.HumanoidRootPart.CFrame
            end
            WindUI:Notify({ Title = "半无敌［碰飞］", Content = "已锁定目标: " .. plr.Name, Duration = 2 })
        end
    end
end)

task.spawn(function()
    while task.wait(0) do
        if not L.flyOffEnabled then continue end
        if not L.flyOffTarget then continue end

        local char = L.flyOffTarget.Character
        if not char or not char:FindFirstChild("Humanoid") then
            L.flyOffTarget = nil
            continue
        end

        local hum = char.Humanoid
        if hum.Health <= 0 then
            L.flyOffTarget = nil
            continue
        end

        local myChar = lp.Character
        local myHRP = myChar and myChar:FindFirstChild("HumanoidRootPart")
        local targetHRP = char:FindFirstChild("HumanoidRootPart")

        if myHRP and targetHRP then
            local offset = targetHRP.Velocity.Magnitude < 0.1 and 0 or 7
            local goal = targetHRP.CFrame * CFrame.new(0,0,-offset) * CFrame.Angles(0, math.rad(-3), 0)
            myHRP.CFrame = myHRP.CFrame:Lerp(goal, 0.4)
            myHRP.Velocity = Vector3.new(0,0,0)
            myHRP.RotVelocity = Vector3.new(0,0,0)
        end
    end
end)

task.spawn(function()
    while task.wait() do
        if not L.flyOffEnabled then continue end
        local hum = lp.Character and lp.Character:FindFirstChild("Humanoid")
        if hum then
            hum:Move(Vector3.one * 1e31)
        end
    end
end)

OtherTab:Toggle({
    Title = G.ToggleFlyOffTitle,
    Desc = G.ToggleFlyOffDesc,
    Value = false,
    Callback = function(state)
        L.flyOffEnabled = state
        if not state then
            L.flyOffTarget = nil
            L.flyOffOriginalCFrame = nil
        end
    end
})

lp.CharacterAdded:Connect(function()
    if L.flyOffEnabled then
        L.flyOffTarget = nil
        L.flyOffOriginalCFrame = nil
    end
end)

-- ==================== 移除自爆碰撞箱（仅自爆僵尸） ====================
L.barrelCollisionRemovalActive = false
L.barrelOriginalCollisionStates = {}
L.barrelOriginalQueryStates = {}
L.barrelCollisionRemovalConn = nil

function L.getAllParts(model)
    local parts = {}
    for _, descendant in pairs(model:GetDescendants()) do
        if descendant:IsA("BasePart") then
            table.insert(parts, descendant)
        end
    end
    return parts
end

function L.setBarrelCollisionEffect(zombie, enabled)
    if not zombie or not zombie.Parent then return end
    if zombie:GetAttribute("Type") ~= "Barrel" and not zombie:FindFirstChild("Barrel") then return end
    local parts = L.getAllParts(zombie)
    for _, part in ipairs(parts) do
        if enabled then
            if L.barrelOriginalCollisionStates[part] == nil then
                L.barrelOriginalCollisionStates[part] = part.CanCollide
            end
            if L.barrelOriginalQueryStates[part] == nil then
                L.barrelOriginalQueryStates[part] = part.CanQuery
            end
            part.CanCollide = false
            part.CanQuery = false
        else
            if L.barrelOriginalCollisionStates[part] ~= nil then
                part.CanCollide = L.barrelOriginalCollisionStates[part]
            else
                part.CanCollide = true
            end
            if L.barrelOriginalQueryStates[part] ~= nil then
                part.CanQuery = L.barrelOriginalQueryStates[part]
            else
                part.CanQuery = true
            end
        end
    end
end

function L.applyToAllBarrels(disable)
    local zombiesFolder = Workspace:FindFirstChild("Zombies")
    if not zombiesFolder then return end
    for _, zombie in pairs(zombiesFolder:GetChildren()) do
        if zombie:IsA("Model") and (zombie:GetAttribute("Type") == "Barrel" or zombie:FindFirstChild("Barrel")) then
            L.setBarrelCollisionEffect(zombie, disable)
        end
    end
end

function L.onBarrelZombieAdded(zombie)
    if L.barrelCollisionRemovalActive and zombie:IsA("Model") and (zombie:GetAttribute("Type") == "Barrel" or zombie:FindFirstChild("Barrel")) then
        L.setBarrelCollisionEffect(zombie, true)
    end
end

function L.startBarrelCollisionRemoval()
    if L.barrelCollisionRemovalConn then L.barrelCollisionRemovalConn:Disconnect() end
    L.barrelCollisionRemovalConn = Workspace.DescendantAdded:Connect(function(desc)
        if desc:IsA("Model") and desc.Parent and desc.Parent.Name == "Zombies" then
            L.onBarrelZombieAdded(desc)
        end
    end)
    L.applyToAllBarrels(true)
end

function L.stopBarrelCollisionRemoval()
    if L.barrelCollisionRemovalConn then
        L.barrelCollisionRemovalConn:Disconnect()
        L.barrelCollisionRemovalConn = nil
    end
    L.applyToAllBarrels(false)
    L.barrelOriginalCollisionStates = {}
    L.barrelOriginalQueryStates = {}
end

OtherTab:Toggle({
    Title = G.ToggleBarrelCollisionTitle,
    Desc = G.ToggleBarrelCollisionDesc,
    Value = false,
    Callback = function(state)
        L.barrelCollisionRemovalActive = state
        if state then
            L.startBarrelCollisionRemoval()
        else
            L.stopBarrelCollisionRemoval()
        end
    end
})

-- ==================== 传送功能 ====================
L.teleportEnabled = false
L.teleportScreenGui = nil
L.teleportButton = nil
L.teleportClickConnection = nil
L.teleportActive = false

local function teleportTo(position)
    local character = lp.Character
    if not character then return end
    local rootPart = character:FindFirstChild("HumanoidRootPart")
    if rootPart then
        local adjustedPos = position + Vector3.new(0, 2.5, 0)
        rootPart.CFrame = CFrame.new(adjustedPos)
    end
end

local function createTeleportUI()
    if L.teleportScreenGui then L.teleportScreenGui:Destroy() end
    L.teleportScreenGui = Instance.new("ScreenGui")
    L.teleportScreenGui.Name = "TeleportGUI"
    L.teleportScreenGui.ResetOnSpawn = false
    L.teleportScreenGui.Parent = pgui
    L.teleportButton = Instance.new("TextButton")
    L.teleportButton.Size = UDim2.new(0, 60, 0, 60)
    L.teleportButton.Position = UDim2.new(0.5, -30, 0.3, 0)
    L.teleportButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    L.teleportButton.BackgroundTransparency = 0.2
    L.teleportButton.BorderSizePixel = 0
    L.teleportButton.Text = "关"
    L.teleportButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    L.teleportButton.TextSize = 24
    L.teleportButton.Font = Enum.Font.GothamBold
    L.teleportButton.Parent = L.teleportScreenGui
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = L.teleportButton
    local stroke = Instance.new("UIStroke")
    stroke.Color = Color3.fromRGB(100, 200, 255)
    stroke.Thickness = 2.5
    stroke.Transparency = 0.3
    stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
    stroke.Parent = L.teleportButton
    L.teleportButton.Active = true
    L.teleportButton.Draggable = true
    L.teleportActive = false
    L.teleportButton.MouseButton1Click:Connect(function()
        L.teleportActive = not L.teleportActive
        if L.teleportActive then
            L.teleportButton.Text = "开"
            L.teleportButton.BackgroundColor3 = Color3.fromRGB(0, 120, 255)
            if not L.teleportClickConnection then
                L.teleportClickConnection = mouse.Button1Down:Connect(function()
                    if L.teleportActive then
                        local clickPos = mouse.Hit.p
                        if clickPos then teleportTo(clickPos) end
                    end
                end)
            end
            WindUI:Notify({ Title = "传送功能", Content = "点击传送已开启", Duration = 2 })
        else
            L.teleportButton.Text = "关"
            L.teleportButton.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
            if L.teleportClickConnection then
                L.teleportClickConnection:Disconnect()
                L.teleportClickConnection = nil
            end
            WindUI:Notify({ Title = "传送功能", Content = "点击传送已关闭", Duration = 2 })
        end
    end)
end

local function destroyTeleportUI()
    if L.teleportScreenGui then
        L.teleportScreenGui:Destroy()
        L.teleportScreenGui = nil
    end
    if L.teleportClickConnection then
        L.teleportClickConnection:Disconnect()
        L.teleportClickConnection = nil
    end
    L.teleportActive = false
    L.teleportButton = nil
end

OtherTab:Toggle({
    Title = G.ToggleTeleportTitle,
    Icon = "map-pin",
    Value = false,
    Callback = function(state)
        L.teleportEnabled = state
        if state then
            createTeleportUI()
        else
            destroyTeleportUI()
        end
    end
})

-- ==================== 窗口关闭/销毁 ====================
Window:OnClose(function()
    print("窗口已关闭，飞行状态保持不变")
end)

-- ==================== 动画包（低 local，速度直接设24/16，独立小方块UI） ====================
_G.AnimPack = _G.AnimPack or {}
local AP = _G.AnimPack

-- 辅助函数 ----------------------------------------------------------------
function AP.getAnimator()
    local char = game.Players.LocalPlayer.Character
    if not char then return nil, nil end
    local hum = char:FindFirstChildOfClass("Humanoid")
    if not hum then return nil, nil end
    local animator = hum:FindFirstChildOfClass("Animator")
    if not animator then
        animator = Instance.new("Animator")
        animator.Parent = hum
    end
    return hum, animator
end

function AP.playLoop(idleId, walkId, priority, onState)
    local hum, anim = AP.getAnimator()
    if not hum or not anim then return nil end
    local tracks = { idle = nil, walk = nil }
    local conns = {}
    if idleId then
        local a = Instance.new("Animation")
        a.AnimationId = "rbxassetid://"..idleId
        tracks.idle = anim:LoadAnimation(a)
        tracks.idle.Priority = priority or Enum.AnimationPriority.Action
    end
    if walkId then
        local a = Instance.new("Animation")
        a.AnimationId = "rbxassetid://"..walkId
        tracks.walk = anim:LoadAnimation(a)
        tracks.walk.Priority = priority or Enum.AnimationPriority.Action
    end
    local function update()
        if hum.MoveDirection.Magnitude > 0 then
            if tracks.walk and not tracks.walk.IsPlaying then
                if tracks.idle and tracks.idle.IsPlaying then tracks.idle:Stop() end
                tracks.walk:Play()
            end
        else
            if tracks.idle and not tracks.idle.IsPlaying then
                if tracks.walk and tracks.walk.IsPlaying then tracks.walk:Stop() end
                tracks.idle:Play()
            end
        end
    end
    table.insert(conns, hum:GetPropertyChangedSignal("MoveDirection"):Connect(update))
    update()
    if onState then onState(true) end
    return {
        stop = function()
            if onState then onState(false) end
            if tracks.idle and tracks.idle.IsPlaying then tracks.idle:Stop() end
            if tracks.walk and tracks.walk.IsPlaying then tracks.walk:Stop() end
            for _, c in ipairs(conns) do c:Disconnect() end
        end
    }
end

function AP.playOnce(animId, priority, onFinish)
    local hum, anim = AP.getAnimator()
    if not hum or not anim then return false end
    local a = Instance.new("Animation")
    a.AnimationId = "rbxassetid://"..animId
    local track = anim:LoadAnimation(a)
    track.Priority = priority or Enum.AnimationPriority.Action4
    track:Play()
    if onFinish then track.Stopped:Connect(onFinish) end
    return true
end

function AP.playCrawl(idleId, walkId, sitId, priority)
    local hum, anim = AP.getAnimator()
    if not hum or not anim then return nil end
    local tracks = { idle = nil, walk = nil, sit = nil }
    local conns = {}
    if idleId then
        local a = Instance.new("Animation")
        a.AnimationId = "rbxassetid://"..idleId
        tracks.idle = anim:LoadAnimation(a)
        tracks.idle.Priority = priority or Enum.AnimationPriority.Action
    end
    if walkId then
        local a = Instance.new("Animation")
        a.AnimationId = "rbxassetid://"..walkId
        tracks.walk = anim:LoadAnimation(a)
        tracks.walk.Priority = priority or Enum.AnimationPriority.Action
    end
    if sitId then
        local a = Instance.new("Animation")
        a.AnimationId = "rbxassetid://"..sitId
        tracks.sit = anim:LoadAnimation(a)
        tracks.sit.Priority = Enum.AnimationPriority.Action2
        tracks.sit.Looped = true
        tracks.sit:Play()
    end
    local function update()
        if hum.MoveDirection.Magnitude > 0 then
            if tracks.walk and not tracks.walk.IsPlaying then
                if tracks.idle and tracks.idle.IsPlaying then tracks.idle:Stop() end
                tracks.walk:Play()
            end
        else
            if tracks.idle and not tracks.idle.IsPlaying then
                if tracks.walk and tracks.walk.IsPlaying then tracks.walk:Stop() end
                tracks.idle:Play()
            end
        end
    end
    table.insert(conns, hum:GetPropertyChangedSignal("MoveDirection"):Connect(update))
    update()
    return {
        stop = function()
            if tracks.idle and tracks.idle.IsPlaying then tracks.idle:Stop() end
            if tracks.walk and tracks.walk.IsPlaying then tracks.walk:Stop() end
            if tracks.sit and tracks.sit.IsPlaying then tracks.sit:Stop() end
            for _, c in ipairs(conns) do c:Disconnect() end
        end
    }
end

-- 通用开关（无速度修改）
function AP.makeToggle(name, idle, walk, prio, extra)
    local active = false
    local ctrl = nil
    AP.Tab:Toggle({
        Title = name,
        Value = false,
        Callback = function(s)
            if s then
                if active then if ctrl then ctrl.stop() end; active = false end
                if extra and extra.onStart then extra.onStart() end
                if extra and extra.special == "crawl" then
                    ctrl = AP.playCrawl(idle, walk, extra.sitId, prio)
                else
                    ctrl = AP.playLoop(idle, walk, prio, function(on) if extra and extra.onState then extra.onState(on) end end)
                end
                active = true
                AP.activeAnims[name] = ctrl
            else
                if ctrl then ctrl.stop() end
                active = false
                AP.activeAnims[name] = nil
                if extra and extra.onStop then extra.onStop() end
            end
        end
    })
end

-- 带速度的开关（开启速度24，关闭速度16）
function AP.makeToggleWithSpeed(name, idle, walk, prio)
    local active = false
    local ctrl = nil
    AP.Tab:Toggle({
        Title = name,
        Value = false,
        Callback = function(s)
            local hum = AP.getAnimator()
            if s then
                if active then if ctrl then ctrl.stop() end; active = false end
                if hum then hum.WalkSpeed = 24 end
                ctrl = AP.playLoop(idle, walk, prio)
                active = true
                AP.activeAnims[name] = ctrl
            else
                if ctrl then ctrl.stop() end
                active = false
                AP.activeAnims[name] = nil
                if hum then hum.WalkSpeed = 16 end
            end
        end
    })
end

-- ========== 创建 UI Tab ==========
AP.Tab = OtherSection:Tab({ Title = "动画包", Icon = "film" })
AP.activeAnims = {}

-- ==================== 美化功能卡 ====================
local BeautySection = Window:Section({ Title = "美化", Opened = false })
local AuraTab = BeautySection:Tab({ Title = "特效", Icon = "sparkles" })

-- ========== 光环配置（可从下方列表手动替换 ID） ==========
-- 可用光环ID参考：
-- 星光: rbxassetid://134645216613107
-- 天堂: rbxassetid://139300897520961
-- 缎带: rbxassetid://132069507632161
-- 樱花: rbxassetid://81755778619404
-- 天使: rbxassetid://97658130917593
-- 风:   rbxassetid://80694081850877
-- 流:   rbxassetid://119913533725648
-- 星:   rbxassetid://73754563740680
local AURA_ASSET_ID = "rbxassetid://97658130917593"   -- 默认天使光环
local TOGGLE_KEY = Enum.KeyCode.Insert               -- 快捷键 Insert
local AUTO_ENABLE = false                            -- 脚本启动后自动关闭（默认关闭）

-- ========== 光环核心变量 ==========
L.Aura = L.Aura or {}
local Aura = L.Aura
Aura.Particles = {}          -- 存储所有粒子对象
Aura.AuraModel = nil         -- 加载的光环模型
Aura.IsEnabled = false       -- 光环开关状态
Aura.CurrentConnection = nil -- 渲染连接
Aura.Character = nil
Aura.HumanoidRootPart = nil

-- 身体部位对应表（用于将光环零件附着到正确位置）
local BodyParts = {
    Head = "Head",
    UpperTorso = "UpperTorso",
    LowerTorso = "LowerTorso",
    LeftUpperArm = "LeftUpperArm",
    LeftLowerArm = "LeftLowerArm",
    LeftHand = "LeftHand",
    RightUpperArm = "RightUpperArm",
    RightLowerArm = "RightLowerArm",
    RightHand = "RightHand",
    LeftUpperLeg = "LeftUpperLeg",
    LeftLowerLeg = "LeftLowerLeg",
    LeftFoot = "LeftFoot",
    RightUpperLeg = "RightUpperLeg",
    RightLowerLeg = "RightLowerLeg",
    RightFoot = "RightFoot",
    HumanoidRootPart = "HumanoidRootPart"
}

-- 清除所有已生成的粒子
local function ClearParticles()
    for _, particle in ipairs(Aura.Particles) do
        pcall(function() particle:Destroy() end)
    end
    Aura.Particles = {}
end

-- 应用光环（将模型中的粒子附着到角色身体对应部位）
local function ApplyAura()
    ClearParticles()
    
    if not Aura.AuraModel or not Aura.Character then return end
    
    local cloned = Aura.AuraModel:Clone()
    local children = cloned:GetChildren()
    
    for _, child in ipairs(children) do
        local targetPart = Aura.Character:FindFirstChild(child.Name)
        if targetPart then
            local subChildren = child:GetChildren()
            for _, sub in ipairs(subChildren) do
                sub.Parent = targetPart
                table.insert(Aura.Particles, sub)
            end
        end
        child:Destroy()
    end
    
    cloned:Destroy()
end

-- 加载光环模型
local function LoadAura()
    if Aura.AuraModel then
        pcall(function() Aura.AuraModel:Destroy() end)
        Aura.AuraModel = nil
    end
    
    local success, result = pcall(function()
        return game:GetObjects(AURA_ASSET_ID)[1]
    end)
    
    if success and result then
        Aura.AuraModel = result
        if Aura.IsEnabled then
            ApplyAura()
        end
        return true
    else
        warn("加载光环失败，请检查Asset ID: " .. AURA_ASSET_ID)
        return false
    end
end

-- 光环更新函数（每帧检查角色是否变化）
local function OnRenderStep()
    if not Aura.IsEnabled then return end
    
    local character = lp.Character
    if character ~= Aura.Character then
        Aura.Character = character
        if Aura.Character then
            Aura.HumanoidRootPart = Aura.Character:WaitForChild("HumanoidRootPart")
            ApplyAura()
        end
    end
end

-- 启用光环
local function EnableAura()
    if Aura.IsEnabled then return end
    Aura.IsEnabled = true
    
    if not Aura.AuraModel then
        LoadAura()
    else
        ApplyAura()
    end
    
    if not Aura.CurrentConnection then
        Aura.CurrentConnection = RunService.RenderStepped:Connect(OnRenderStep)
    end
    
    print("[光环] 已开启")
end

-- 禁用光环
local function DisableAura()
    if not Aura.IsEnabled then return end
    Aura.IsEnabled = false
    
    ClearParticles()
    
    if Aura.CurrentConnection then
        Aura.CurrentConnection:Disconnect()
        Aura.CurrentConnection = nil
    end
    
    print("[光环] 已关闭")
end

-- 切换光环开关
local function ToggleAura()
    if Aura.IsEnabled then
        DisableAura()
    else
        EnableAura()
    end
end

-- 监听快捷键
UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end
    if input.KeyCode == TOGGLE_KEY then
        ToggleAura()
    end
end)

-- 监听角色重生
lp.CharacterAdded:Connect(function(newChar)
    Aura.Character = newChar
    Aura.HumanoidRootPart = newChar:WaitForChild("HumanoidRootPart")
    if Aura.IsEnabled then
        task.wait(0.5)
        ApplyAura()
    end
end)

-- 初始化
Aura.Character = lp.Character
if Aura.Character then
    Aura.HumanoidRootPart = Aura.Character:WaitForChild("HumanoidRootPart")
end

-- 加载模型（但不自动开启，因为 AUTO_ENABLE = false）
LoadAura()
if AUTO_ENABLE then
    EnableAura()
end

-- ========== UI 控件（Toggle 开关，与光环状态同步） ==========
AuraTab:Toggle({
    Title = "天使光环",
    Desc = "天使光环特效",
    Value = false,   -- 默认关闭
    Callback = function(state)
        if state then
            EnableAura()
        else
            DisableAura()
        end
    end
})

-- 1. 山伯乐动画（无速度）
AP.makeToggle("山伯乐", "12333488814", "14463730540", Enum.AnimationPriority.Action3)

-- 2. 红眼动画（无速度）
AP.makeToggle("红眼", "12581784105", "12581785298", Enum.AnimationPriority.Action3)

-- 3. 胸甲僵尸（无速度）
AP.makeToggle("胸胸甲骑兵", "87579228279296", "102081698785465", Enum.AnimationPriority.Action3)

-- ===== 胸甲骑兵冲锋（小方块拖拽按钮） =====
AP.cavalryUI = nil
AP.cavalryBtn = nil
AP.cavalryPlaying = false

function AP.cavalryCharge()
    if AP.cavalryPlaying then
        WindUI:Notify({ Title = "胸甲骑兵冲锋", Content = "冲锋进行中，请等待完成", Duration = 1 })
        return
    end
    AP.cavalryPlaying = true
    if AP.cavalryBtn then AP.cavalryBtn.Text = "冲锋中" end
    
    local hum, anim = AP.getAnimator()
    if not hum or not anim then
        AP.cavalryPlaying = false
        if AP.cavalryBtn then AP.cavalryBtn.Text = "冲" end
        WindUI:Notify({ Title = "胸甲骑兵冲锋", Content = "无法播放动画", Duration = 1, Type = "error" })
        return
    end
    for _, t in pairs(hum:GetPlayingAnimationTracks()) do t:Stop() end
    local function load(id)
        local a = Instance.new("Animation")
        a.AnimationId = "rbxassetid://"..id
        local t = anim:LoadAnimation(a)
        t.Priority = Enum.AnimationPriority.Action4
        return t
    end
    local t1 = load("105118183189738")
    local t2 = load("17406602570")
    local finalId = "102984581737936"
    local noEnemyId = "139159672489901"
    local origSpeed = hum.WalkSpeed
    hum.WalkSpeed = 1
    t1:Play()
    t1.Stopped:Wait()
    if not AP.cavalryPlaying then return end
    hum.WalkSpeed = 28
    t2:Play()
    local stopAt = os.clock() + 5
    while os.clock() < stopAt and t2.IsPlaying do task.wait() if not AP.cavalryPlaying then break end end
    t2:Stop()
    hum.WalkSpeed = origSpeed
    if not AP.cavalryPlaying then return end
    local hasEnemy = false
    for _, pl in ipairs(game:GetService("Players"):GetPlayers()) do
        if pl ~= game.Players.LocalPlayer and pl.Character then
            local dist = (pl.Character:GetPivot().Position - hum.RootPart.Position).Magnitude
            if dist < 10 then hasEnemy = true; break end
        end
    end
    local finalT = load(hasEnemy and finalId or noEnemyId)
    if not hasEnemy then hum.WalkSpeed = 4 end
    finalT:Play()
    finalT.Stopped:Wait()
    hum.WalkSpeed = 16
    AP.cavalryPlaying = false
    if AP.cavalryBtn then AP.cavalryBtn.Text = "冲" end
    WindUI:Notify({ Title = "胸甲骑兵冲锋", Content = "冲锋完成", Duration = 2 })
end

function AP.createCavalryUI()
    if AP.cavalryUI then AP.cavalryUI:Destroy() end
    AP.cavalryUI = Instance.new("ScreenGui")
    AP.cavalryUI.Name = "CavalryChargeUI"
    AP.cavalryUI.ResetOnSpawn = false
    AP.cavalryUI.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 60, 0, 60)
    btn.Position = UDim2.new(0.5, -30, 0.3, 0)
    btn.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    btn.BackgroundTransparency = 0.2
    btn.BorderSizePixel = 0
    btn.Text = "冲"
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.TextSize = 24
    btn.Font = Enum.Font.GothamBold
    btn.Parent = AP.cavalryUI
    btn.Active = true
    btn.Draggable = true
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = btn
    local stroke = Instance.new("UIStroke")
    stroke.Color = Color3.fromRGB(100, 200, 255)
    stroke.Thickness = 2.5
    stroke.Transparency = 0.3
    stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
    stroke.Parent = btn
    AP.cavalryBtn = btn

    btn.MouseButton1Click:Connect(function()
        task.spawn(AP.cavalryCharge)
    end)
end

function AP.destroyCavalryUI()
    if AP.cavalryUI then AP.cavalryUI:Destroy(); AP.cavalryUI = nil end
    AP.cavalryPlaying = false
    AP.cavalryBtn = nil
end

AP.cavalryToggle = AP.Tab:Toggle({
    Title = "打开胸甲骑兵冲锋快捷栏",
    Value = false,
    Callback = function(state)
        if state then AP.createCavalryUI() else AP.destroyCavalryUI() end
    end
})

-- 4. 提灯人（无速度）
AP.makeToggle("提灯人", "14678879479", "14678880308", Enum.AnimationPriority.Action3)

-- 5. ZAPPER动画（无速度）
AP.makeToggle("斧头僵尸", "14498563473", "14498289874", Enum.AnimationPriority.Action3)

-- ===== ZAPPER特效（小方块拖拽按钮） =====
AP.zapperUI = nil
AP.zapperBtn = nil
AP.zapperBusy = false

function AP.createZapperUI()
    if AP.zapperUI then AP.zapperUI:Destroy() end
    AP.zapperUI = Instance.new("ScreenGui")
    AP.zapperUI.Name = "ZapperEffectUI"
    AP.zapperUI.ResetOnSpawn = false
    AP.zapperUI.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 60, 0, 60)
    btn.Position = UDim2.new(0.5, -30, 0.4, 0)
    btn.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    btn.BackgroundTransparency = 0.2
    btn.BorderSizePixel = 0
    btn.Text = "劈砍"
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.TextSize = 18
    btn.Font = Enum.Font.GothamBold
    btn.Parent = AP.zapperUI
    btn.Active = true
    btn.Draggable = true
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 12)
    corner.Parent = btn
    local stroke = Instance.new("UIStroke")
    stroke.Color = Color3.fromRGB(100, 200, 255)
    stroke.Thickness = 2.5
    stroke.Transparency = 0.3
    stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
    stroke.Parent = btn
    AP.zapperBtn = btn

    btn.MouseButton1Click:Connect(function()
        if AP.zapperBusy then
            WindUI:Notify({ Title = "斧头僵尸", Content = "正在播放动画中", Duration = 1 })
            return
        end
        AP.zapperBusy = true
        if AP.zapperBtn then AP.zapperBtn.Text = "劈砍中" end
        AP.playOnce("14499470197", Enum.AnimationPriority.Action4, function()
            AP.zapperBusy = false
            if AP.zapperBtn then AP.zapperBtn.Text = "劈砍" end
            WindUI:Notify({ Title = "斧头僵尸", Content = "播放完成", Duration = 1 })
        end)
    end)
end

function AP.destroyZapperUI()
    if AP.zapperUI then AP.zapperUI:Destroy(); AP.zapperUI = nil end
    AP.zapperBusy = false
    AP.zapperBtn = nil
end

AP.zapperToggle = AP.Tab:Toggle({
    Title = "打开斧头僵尸劈砍快捷栏",
    Value = false,
    Callback = function(state)
        if state then AP.createZapperUI() else AP.destroyZapperUI() end
    end
})

-- 6. 自爆（无速度）
AP.makeToggle("自爆", "13211198049", "13211207597", Enum.AnimationPriority.Action3)

-- 7. 爬尸（无速度）
AP.makeToggle("爬尸", "13726632691", "13726634549", Enum.AnimationPriority.Action3, { special = "crawl", sitId = "130515356351734" })

-- 8. 重剑冲锋（有速度：开24关16）
AP.makeToggleWithSpeed("重剑冲锋", "14284611111", "17406602570", Enum.AnimationPriority.Action3)

-- 9. 滑膛枪冲锋（有速度）
AP.makeToggleWithSpeed("滑膛枪冲锋", "14292935158", "14292937831", Enum.AnimationPriority.Action3)

-- 10. 冲锋（有速度）
AP.makeToggleWithSpeed("冲锋", "14284611111", "14284623849", Enum.AnimationPriority.Idle)

-- 角色重生清理动画
game.Players.LocalPlayer.CharacterAdded:Connect(function()
    for _, ctrl in pairs(AP.activeAnims) do if ctrl and ctrl.stop then ctrl.stop() end end
    AP.activeAnims = {}
end)

Window:OnDestroy(function()
    print("窗口已销毁")
    L.isFlying_orig = false
    L.clearFlyRes_orig()
    L.isFlying_new = false
    L.clearFlyRes_new()
    if L.zombieESPHeartbeatConn then L.zombieESPHeartbeatConn:Disconnect() end
    L.clearAllZombieEffects()
    if L.shootingLoopRunning then L.stopShooting() end
    for _, hl in pairs(L.playerHighlights) do if hl then hl:Destroy() end end
    for _, tag in pairs(L.playerNameTags) do if tag then tag:Destroy() end end
    L.clearJumpListeners()
    L.stopBombRange()
    L.disableHeadshot()
    if chattedConn then chattedConn:Disconnect() end
    L.flyOffEnabled = false
    L.flyOffTarget = nil
    if L.pvpHeartbeatConn then L.pvpHeartbeatConn:Disconnect() end
    L.stopBarrelCollisionRemoval()
    L.stopAutoJump()
    if L.doctorThread then task.cancel(L.doctorThread) end
    if L.chaplainThread then task.cancel(L.chaplainThread) end
    destroyTeleportUI()
    if L.speedWalkSpeedConn then L.speedWalkSpeedConn:Disconnect() end
    if L.speedCharAddedConn then L.speedCharAddedConn:Disconnect() end
    if L.autoRepairLoop then task.cancel(L.autoRepairLoop) end
    L.stopCustomShooting()
    cleanupPhysics()
    destroyPathVisuals()
    if flyThread then task.cancel(flyThread) end
    if doorMonitorThread then task.cancel(doorMonitorThread) end
    if bellMonitorThread then task.cancel(bellMonitorThread) end
    bridgeStop()
end)
