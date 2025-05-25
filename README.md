local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer
local backpack = player:WaitForChild("Backpack")
local playerGui = player:WaitForChild("PlayerGui")

local oldGui = playerGui:FindFirstChild("DupeTestGUI")
if oldGui then oldGui:Destroy() end

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "DupeTestGUI"
screenGui.ResetOnSpawn = false
screenGui.IgnoreGuiInset = true
screenGui.Parent = playerGui

local button = Instance.new("TextButton")
button.Name = "DupeButton"
button.Text = "🔁 DUPLICAR"
button.Size = UDim2.new(0, 160, 0, 50)
button.Position = UDim2.new(0.5, -80, 1, -60)
button.AnchorPoint = Vector2.new(0.5, 1)
button.BackgroundColor3 = Color3.fromRGB(30, 180, 30)
button.TextColor3 = Color3.new(1, 1, 1)
button.Font = Enum.Font.GothamBold
button.TextSize = 20
button.Parent = screenGui

button.MouseButton1Click:Connect(function()
    local character = player.Character
    local toolToClone = nil

    if character then
        for _, item in ipairs(character:GetChildren()) do
            if item:IsA("Tool") then
                toolToClone = item
                break
            end
        end
    end

    if not toolToClone then
        toolToClone = ReplicatedStorage:FindFirstChild("ToolTemplate")
    end

    if toolToClone then
        local clone = toolToClone:Clone()
        clone.Parent = backpack
        print("✅ Item duplicado.")
    else
        warn("❌ Nenhum Tool encontrado para duplicar.")
    end
end)
