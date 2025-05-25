-- Script para executor mobile (telemóvel) - Teste de duplicação

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer
local backpack = player:WaitForChild("Backpack")
local playerGui = player:WaitForChild("PlayerGui")

-- Evita múltiplas GUIs
if playerGui:FindFirstChild("DupeTestGUI") then
    playerGui:FindFirstChild("DupeTestGUI"):Destroy()
end

-- Cria GUI
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "DupeTestGUI"
screenGui.ResetOnSpawn = false
screenGui.IgnoreGuiInset = true
screenGui.Parent = playerGui

-- Cria botão
local button = Instance.new("TextButton")
button.Name = "DupeButton"
button.Text = "🔁 DUPLICAR"
button.Size = UDim2.new(0, 160, 0, 50)
button.Position = UDim2.new(0.5, -80, 1, -60)
button.AnchorPoint = Vector2.new(0.5, 1)
button.BackgroundColor3 = Color3.fromRGB(25, 150, 25)
button.TextColor3 = Color3.new(1, 1, 1)
button.Font = Enum.Font.GothamBold
button.TextSize = 20
button.Parent = screenGui

-- Ação ao clicar
button.MouseButton1Click:Connect(function()
    local template = ReplicatedStorage:FindFirstChild("ToolTemplate")
    if template then
        local clone = template:Clone()
        clone.Parent = backpack
        print("✅ Tool duplicada com sucesso.")
    else
        warn("❌ ToolTemplate não encontrado no ReplicatedStorage.")
    end
end)
