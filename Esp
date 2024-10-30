local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Camera = workspace.CurrentCamera
local RunService = game:GetService("RunService")

-- Function to create a highlight for a player
local function createHighlight(player)
    local highlight = Instance.new("Highlight")
    highlight.Name = "Highlight"
    highlight.Adornee = player.Character
    highlight.FillColor = Color3.new(1, 0, 0) -- Initial color red
    highlight.FillTransparency = 0.5
    highlight.Parent = player.Character
end

-- Function to update the highlight color based on visibility
local function updateHighlight(player)
    if player.Character and player.Character:FindFirstChild("Highlight") then
        local highlight = player.Character.Highlight
        local characterPosition = player.Character.HumanoidRootPart.Position
        local cameraPosition = Camera.CFrame.Position
        
        -- Calculate visibility using a basic distance check
        local distance = (characterPosition - cameraPosition).magnitude
        if distance < 50 then -- Change the distance threshold as needed
            highlight.FillColor = Color3.new(0, 1, 0) -- Green if seen
        else
            highlight.FillColor = Color3.new(1, 0, 0) -- Red if not seen
        end
    end
end

-- Function to handle player added
local function onPlayerAdded(player)
    player.CharacterAdded:Connect(function(character)
        wait(1) -- Wait for character to load
        createHighlight(player)

        -- Continuously check for visibility
        while true do
            updateHighlight(player)
            wait(0.1) -- Update every 0.1 seconds
        end
    end)
end

-- Connect the player added event
Players.PlayerAdded:Connect(onPlayerAdded)

-- Check for already existing players
for _, player in pairs(Players:GetPlayers()) do
    onPlayerAdded(player)
end
