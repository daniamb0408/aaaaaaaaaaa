local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "GrowAGardenDupe"
ScreenGui.Parent = game.CoreGui

local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0, 250, 0, 120)
Frame.Position = UDim2.new(0.5, -125, 0.5, -60)
Frame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Frame.Parent = ScreenGui

local ButtonDupe = Instance.new("TextButton")
ButtonDupe.Size = UDim2.new(0, 230, 0, 50)
ButtonDupe.Position = UDim2.new(0, 10, 0, 30)
ButtonDupe.BackgroundColor3 = Color3.fromRGB(80, 160, 80)
ButtonDupe.Text = "Ativar Dupe"
ButtonDupe.TextColor3 = Color3.new(1,1,1)
ButtonDupe.Parent = Frame

local TextLabel = Instance.new("TextLabel")
TextLabel.Size = UDim2.new(0, 230, 0, 20)
TextLabel.Position = UDim2.new(0, 10, 0, 5)
TextLabel.BackgroundTransparency = 1
TextLabel.Text = "Dupe Grow a Garden"
TextLabel.TextColor3 = Color3.new(1,1,1)
TextLabel.Parent = Frame

local function ativarDupe()
    local player = game.Players.LocalPlayer
    local ReplicatedStorage = game:GetService("ReplicatedStorage")
    local remote = ReplicatedStorage:FindFirstChild("RemoteEvent")

    if not remote then return end

    local args = {
        ["action"] = "plantSeed",
        ["seedId"] = 123,
        ["position"] = player.Character.HumanoidRootPart.Position
    }

    remote:FireServer(args)
    wait(0.1)
    remote:FireServer(args)
end

ButtonDupe.MouseButton1Click:Connect(ativarDupe)
