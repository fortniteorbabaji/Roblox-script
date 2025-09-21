# Roblox-script
-- Place ce script en LocalScript dans StarterGui

local Players = game:GetService("Players")
local player = Players.LocalPlayer

-- Création du ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "KeySystemGui"
screenGui.Parent = player:WaitForChild("PlayerGui")

-- Cadre principal
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 400, 0, 250)
frame.Position = UDim2.new(0.5, -200, 0.5, -125)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.BorderSizePixel = 0
frame.Parent = screenGui

-- Titre
local title = Instance.new("TextLabel")
title.Text = "Système de clé"
title.Font = Enum.Font.SourceSansBold
title.TextSize = 32
title.TextColor3 = Color3.fromRGB(255,255,255)
title.BackgroundTransparency = 1
title.Size = UDim2.new(1, 0, 0, 50)
title.Position = UDim2.new(0, 0, 0, 0)
title.Parent = frame

-- Label du lien
local keyLabel = Instance.new("TextLabel")
keyLabel.Text = "Votre clé : https://preview--share-code-launcher-76.lovable.app/"
keyLabel.Font = Enum.Font.SourceSans
keyLabel.TextSize = 18
keyLabel.TextColor3 = Color3.fromRGB(255,255,255)
keyLabel.BackgroundTransparency = 1
keyLabel.Size = UDim2.new(1, -40, 0, 40)
keyLabel.Position = UDim2.new(0, 20, 0, 50)
keyLabel.TextWrapped = true
keyLabel.Parent = frame

-- TextBox pour entrer la clé
local keyBox = Instance.new("TextBox")
keyBox.PlaceholderText = "Entrez votre clé ici"
keyBox.Text = ""
keyBox.Font = Enum.Font.SourceSans
keyBox.TextSize = 20
keyBox.TextColor3 = Color3.fromRGB(255,255,255)
keyBox.BackgroundColor3 = Color3.fromRGB(40,40,40)
keyBox.Size = UDim2.new(1, -40, 0, 40)
keyBox.Position = UDim2.new(0, 20, 0, 100)
keyBox.Parent = frame

-- Bouton "Obtenir la clé"
local getKeyButton = Instance.new("TextButton")
getKeyButton.Text = "Obtenir la clé"
getKeyButton.Font = Enum.Font.SourceSansBold
getKeyButton.TextSize = 22
getKeyButton.TextColor3 = Color3.fromRGB(255,255,255)
getKeyButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
getKeyButton.Size = UDim2.new(0, 160, 0, 40)
getKeyButton.Position = UDim2.new(0, 40, 0, 160)
getKeyButton.Parent = frame

-- Bouton "Utiliser la clé"
local useKeyButton = Instance.new("TextButton")
useKeyButton.Text = "Utiliser la clé"
useKeyButton.Font = Enum.Font.SourceSansBold
useKeyButton.TextSize = 22
useKeyButton.TextColor3 = Color3.fromRGB(255,255,255)
useKeyButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
useKeyButton.Size = UDim2.new(0, 160, 0, 40)
useKeyButton.Position = UDim2.new(0, 200, 0, 160)
useKeyButton.Parent = frame

-- Info Label
local infoLabel = Instance.new("TextLabel")
infoLabel.Text = ""
infoLabel.Font = Enum.Font.SourceSans
infoLabel.TextSize = 18
infoLabel.TextColor3 = Color3.fromRGB(255,255,255)
infoLabel.BackgroundTransparency = 1
infoLabel.Size = UDim2.new(1, -40, 0, 30)
infoLabel.Position = UDim2.new(0, 20, 0, 210)
infoLabel.Parent = frame

-- Copier le lien dans le presse-papiers (fonctionne seulement en Studio)
getKeyButton.MouseButton1Click:Connect(function()
    if setclipboard then
        setclipboard("https://preview--share-code-launcher-76.lovable.app/")
        infoLabel.Text = "Lien copié dans le presse-papiers !"
    else
        infoLabel.Text = "Impossible de copier automatiquement. Veuillez copier le lien manuellement."
    end
end)

-- Utiliser la clé
useKeyButton.MouseButton1Click:Connect(function()
    local key = keyBox.Text
    if key == "delta" then
        infoLabel.Text = "Clé valide ! Accès autorisé."
        -- Ici, ajoute ta logique d'accès ou d'exécution
    else
        infoLabel.Text = "Clé invalide. Veuillez réessayer."
    end
end)
