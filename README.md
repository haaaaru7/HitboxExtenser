local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
-- Crear la GUI principal
local ScreenGui = Instance.new("ScreenGui")
local main = Instance.new("Frame")
local label = Instance.new("TextLabel")
local HitboxButton, CloseButton, MinimizeButton, MaximizeButton
local HitboxSizeSlider = Instance.new("Frame")
local SliderButton = Instance.new("TextButton")
local SliderLabel = Instance.new("TextLabel")
ScreenGui.Parent = game.CoreGui
-- Configuración de la interfaz principal
main.Name = "main"
main.Parent = ScreenGui
main.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
main.Position = UDim2.new(0.35, 0, 0.32, 0)
main.Size = UDim2.new(0, 400, 0, 250)
main.Active = true
main.Draggable = true
main.BorderSizePixel = 0
main.BackgroundTransparency = 0.1
main.ClipsDescendants = true
-- Suavizar bordes
local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 10)
UICorner.Parent = main
-- Configuración de la etiqueta
label.Name = "label"
label.Parent = main
label.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
label.Size = UDim2.new(1, 0, 0, 30)
label.Font = Enum.Font.SourceSansBold
label.Text = "Hitbox GUI"
label.TextColor3 = Color3.fromRGB(255, 255, 255)
label.TextScaled = true
label.TextWrapped = true
label.BorderSizePixel = 0
-- Función para crear botones con estilo
local function createButton(name, position, text, backgroundColor, textColor)
    local button = Instance.new("TextButton")
    button.Name = name
    button.Parent = main
    button.BackgroundColor3 = backgroundColor
    button.Position = position
    button.Size = UDim2.new(0, 130, 0, 40)
    button.Font = Enum.Font.SourceSans
    button.Text = text
    button.TextColor3 = textColor
    button.TextSize = 24
    button.BorderSizePixel = 0
    button.BackgroundTransparency = 0.2
    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 10)
    corner.Parent = button
    -- Efecto de hover
    button.MouseEnter:Connect(function() button.BackgroundColor3 = Color3.fromRGB(100, 100, 100) end)
    button.MouseLeave:Connect(function() button.BackgroundColor3 = backgroundColor end)
    return button
end
-- Crear botones
HitboxButton = createButton("HitboxButton", UDim2.new(0.6, 0, 0.5, 0), "Hitbox On", Color3.fromRGB(255, 255, 255), Color3.fromRGB(0, 0, 0))
MinimizeButton = createButton("MinimizeButton", UDim2.new(0.1, 0, 0.75, 0), "Minimize", Color3.fromRGB(255, 255, 255), Color3.fromRGB(0, 0, 0))
CloseButton = createButton("CloseButton", UDim2.new(0.6, 0, 0.75, 0), "Close", Color3.fromRGB(255, 255, 255), Color3.fromRGB(0, 0, 0))
MaximizeButton = createButton("MaximizeButton", UDim2.new(0.5, -65, 0.8, 0), "Maximize", Color3.fromRGB(100, 100, 100), Color3.fromRGB(255, 0, 0))
MaximizeButton.Visible = false -- Empieza oculto
-- Configuración del slider para el tamaño del hitbox
HitboxSizeSlider.Name = "HitboxSizeSlider"
HitboxSizeSlider.Parent = main
HitboxSizeSlider.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
HitboxSizeSlider.Position = UDim2.new(0.1, 0, 0.5, 0)
HitboxSizeSlider.Size = UDim2.new(0, 180, 0, 20)
SliderButton.Name = "SliderButton"
SliderButton.Parent = HitboxSizeSlider
SliderButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SliderButton.Size = UDim2.new(0, 20, 1, 0)
SliderButton.Text = ""
SliderLabel.Name = "SliderLabel"
SliderLabel.Parent = main
SliderLabel.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
SliderLabel.Position = UDim2.new(0.1, 0, 0.6, 0)
SliderLabel.Size = UDim2.new(0, 180, 0, 30)
SliderLabel.Font = Enum.Font.SourceSansBold
SliderLabel.Text = "Hitbox Size: 2"
SliderLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
SliderLabel.TextScaled = true
