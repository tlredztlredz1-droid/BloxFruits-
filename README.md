local LMG2L = {}
local TweenService = game:GetService("TweenService")

LMG2L["ScreenGui_1"] = Instance.new("ScreenGui", game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui"))
LMG2L["ScreenGui_1"].ZIndexBehavior = Enum.ZIndexBehavior.Sibling

LMG2L["Frame_2"] = Instance.new("Frame", LMG2L["ScreenGui_1"])
LMG2L["Frame_2"].BorderSizePixel = 0
LMG2L["Frame_2"].BackgroundColor3 = Color3.fromRGB(0, 0, 0)
LMG2L["Frame_2"].Size = UDim2.new(0.77483, 0, 0.34356, 0)
LMG2L["Frame_2"].Position = UDim2.new(0.09189, 0, -0.06748, 0)
Instance.new("UICorner", LMG2L["Frame_2"])

LMG2L["Frame_4"] = Instance.new("Frame", LMG2L["Frame_2"])
LMG2L["Frame_4"].BorderSizePixel = 0
LMG2L["Frame_4"].BackgroundColor3 = Color3.fromRGB(255, 33, 74)
LMG2L["Frame_4"].Size = UDim2.new(0.97436, 0, 0.875, 0)
LMG2L["Frame_4"].Position = UDim2.new(0.01282, 0, 0.05357, 0)
Instance.new("UICorner", LMG2L["Frame_4"])

LMG2L["Frame_6"] = Instance.new("Frame", LMG2L["Frame_4"])
LMG2L["Frame_6"].BorderSizePixel = 0
LMG2L["Frame_6"].BackgroundColor3 = Color3.fromRGB(38, 38, 38)
LMG2L["Frame_6"].Size = UDim2.new(0.99342, 0, 0.95918, 0)
LMG2L["Frame_6"].Position = UDim2.new(0.00329, 0, 0.02041, 0)
Instance.new("UICorner", LMG2L["Frame_6"])

-- 📝 Texto
local label = Instance.new("TextLabel", LMG2L["Frame_6"])
label.BorderSizePixel = 0
label.BackgroundTransparency = 1
label.TextColor3 = Color3.fromRGB(255, 255, 255)
label.Size = UDim2.new(0.25166, 0, 1.02128, 0)
label.Position = UDim2.new(0.34768, 0, 0, 0)
label.Text = "Carregar"

-- 🔁 Lista de textos
local textos = {"Carregar...", "AutoFarmLevel", "BuyItem", "BuyFruits", "Auto Sabre", "Auto Pole"}

task.spawn(function()
    local i = 1

    while true do
        -- fade out
        local t1 = TweenService:Create(label, TweenInfo.new(0.4), {
            TextTransparency = 1
        })
        t1:Play()
        t1.Completed:Wait()

        -- troca texto
        i = i + 1
        if i > #textos then i = 1 end
        label.Text = textos[i]

        -- fade in
        local t2 = TweenService:Create(label, TweenInfo.new(0.4), {
            TextTransparency = 0
        })
        t2:Play()
        t2.Completed:Wait()

        task.wait(1)
    end
end)

-- 🔵 Bolinha azul
local azul = Instance.new("Frame", LMG2L["Frame_4"])
azul.BorderSizePixel = 0
azul.BackgroundColor3 = Color3.fromRGB(70, 255, 244)
azul.Size = UDim2.new(0.04, 0, 0.04, 0)
azul.Position = UDim2.new(0.05, 0, 0.95, 0)
Instance.new("UICorner", azul)

-- 🔁 Movimento esquerda ↔ direita
task.spawn(function()
    local t = 0.8

    while true do
        TweenService:Create(azul, TweenInfo.new(t, Enum.EasingStyle.Linear), {
            Position = UDim2.new(0.91, 0, 0.95, 0)
        }):Play()
        task.wait(t)

        TweenService:Create(azul, TweenInfo.new(t, Enum.EasingStyle.Linear), {
            Position = UDim2.new(0.05, 0, 0.95, 0)
        }):Play()
        task.wait(t)
    end
end)

-- 🎨 Cor pulsando
task.spawn(function()
    while true do
        local t1 = TweenService:Create(azul, TweenInfo.new(0.6), {
            BackgroundColor3 = Color3.fromRGB(0, 180, 255)
        })
        local t2 = TweenService:Create(azul, TweenInfo.new(0.6), {
            BackgroundColor3 = Color3.fromRGB(70, 255, 244)
        })

        t1:Play()
        t1.Completed:Wait()
        t2:Play()
        t2.Completed:Wait()
    end
end)

return LMG2L["ScreenGui_1"]
