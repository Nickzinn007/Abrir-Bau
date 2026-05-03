-- feito por CHAGAS HUB

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Criar ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "AbrirBauGUI"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- Criar Frame
local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 320, 0, 120)
mainFrame.Position = UDim2.new(0.5, -160, 0.5, 60)
mainFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

local corner = Instance.new("UICorner")
corner.CornerRadius = UDim.new(0, 10)
corner.Parent = mainFrame

-- Titulo
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.Position = UDim2.new(0, 0, 0, 0)
title.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
title.BorderSizePixel = 0
title.Text = "🎁 Abrir Bau CHAGAS HUB"
title.TextColor3 = Color3.fromRGB(255, 255, 0)
title.TextSize = 16
title.Font = Enum.Font.GothamBold
title.Parent = mainFrame

local titleCorner = Instance.new("UICorner")
titleCorner.CornerRadius = UDim.new(0, 10)
titleCorner.Parent = title

-- Botao
local abrirBauButton = Instance.new("TextButton")
abrirBauButton.Size = UDim2.new(0, 280, 0, 45)
abrirBauButton.Position = UDim2.new(0.5, -140, 0, 55)
abrirBauButton.BackgroundColor3 = Color3.fromRGB(180, 120, 0)
abrirBauButton.BorderSizePixel = 0
abrirBauButton.Text = "🎁 Abrir Bau CHAGAS HUB"
abrirBauButton.TextColor3 = Color3.fromRGB(255, 255, 255)
abrirBauButton.TextSize = 16
abrirBauButton.Font = Enum.Font.GothamBold
abrirBauButton.Parent = mainFrame

local bauCorner = Instance.new("UICorner")
bauCorner.CornerRadius = UDim.new(0, 8)
bauCorner.Parent = abrirBauButton

-- Remote
local invRequest = ReplicatedStorage:WaitForChild("Modules"):WaitForChild("InvRemotes"):WaitForChild("InvRequest")

local guardarArgs = {
    "trasnferebau",
    "Entro",
    "Tratamento",
    5,
    1
}

-- Hover
abrirBauButton.MouseEnter:Connect(function()
    abrirBauButton.Size = UDim2.new(0, 290, 0, 50)
end)

abrirBauButton.MouseLeave:Connect(function()
    abrirBauButton.Size = UDim2.new(0, 280, 0, 45)
end)

-- Click
abrirBauButton.MouseButton1Click:Connect(function()
    abrirBauButton.Text = "Abrindo..."
    task.spawn(function()
        invRequest:InvokeServer(unpack(guardarArgs))
    end)
    task.wait(0.5)
    abrirBauButton.Text = "Bau Aberto!"
    task.wait(1)
    abrirBauButton.Text = "Abrir Bau CHAGAS HUB"
end)
