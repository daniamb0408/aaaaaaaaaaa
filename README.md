local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "GrowAGardenDupe"
screenGui.Parent = playerGui

local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 160, 0, 50)
button.Position = UDim2.new(0.5, -80, 1, -60)
button.AnchorPoint = Vector2.new(0.5, 1)
button.BackgroundColor3 = Color3.fromRGB(30, 180, 30)
button.TextColor3 = Color3.new(1, 1, 1)
button.Font = Enum.Font.GothamBold
button.TextSize = 20
button.Text = "🔁 DUPLICAR CENOURA"
button.Parent = screenGui

-- Mude "AddItemEvent" para o nome correto do evento remoto do jogo
local addItemEvent = ReplicatedStorage:FindFirstChild("AddItemEvent")

button.MouseButton1Click:Connect(function()
    if addItemEvent then
        addItemEvent:FireServer("Carrot")  -- envia pedido para adicionar cenoura
        print("Pedido para duplicar cenoura enviado")
    else
        warn("Evento 'AddItemEvent' não encontrado")
    end
end)
