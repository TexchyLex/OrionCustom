-- Configuration
local r = math.random(0, 255)
local g = math.random(0, 255) 
local b = math.random(0, 255)

local highlightColor = Color3.fromRGB(r, g, b)

-- Functions
local function getPlayers()
  return game:GetService("Players"):GetPlayers()
end

local function highlightPlayer(player)
    local character = player.Character
    if character then
      local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
      if humanoidRootPart then
        local highlight = Instance.new("BoxHandleAdornment", humanoidRootPart)
        highlight.Color3 = player.TeamColor.Color -- Use the player's team color
        highlight.Adornee = humanoidRootPart
        highlight.AlwaysOnTop = true
        highlight.ZIndex = 1 
        highlight.Transparency = 0.5
        
        local billboardGui = Instance.new("BillboardGui")
        billboardGui.Adornee = humanoidRootPart
        billboardGui.Size = UDim2.new(0, 100, 0, 50)
        billboardGui.StudsOffset = Vector3.new(0, 3, 0) -- Position it a bit above the player
        billboardGui.AlwaysOnTop = true -- Make it visible through walls
        billboardGui.Parent = character -- Parent to the character, not the HumanoidRootPart

        local textBox = Instance.new("TextBox", billboardGui)
        textBox.Text = player.Name
        textBox.BackgroundTransparency = 1
        textBox.Size = UDim2.new(1, 0, 1, 0) -- Relative to the BillboardGui
        textBox.Position = UDim2.new(0, 0, 0, 0) -- Relative to the BillboardGui
        textBox.TextColor3 = player.TeamColor.Color -- Use the player's team color for the text
        textBox.TextSize = 14
        textBox.Font = Enum.Font.SourceSansBold
        textBox.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
        textBox.TextStrokeTransparency = 0.15
      end
    end
end

local function removeHighlights()
  for _, player in ipairs(getPlayers()) do
    local character = player.Character
    if character then
      for _, obj in ipairs(character:GetChildren()) do
        if obj:IsA("BoxHandleAdornment") or obj:IsA("BillboardGui") then
          obj:Destroy()
        end
      end
    end
  end
end

local function highlightPlayers()
    removeHighlights()
    
    local localPlayer = game:GetService("Players").LocalPlayer
    for _, player in ipairs(getPlayers()) do
      if player ~= localPlayer then
        highlightPlayer(player)
      end
    end
  end

-- Main Loop
while true do
  highlightPlayers()
  
  r = math.random(0, 255)
  g = math.random(0, 255)
  b = math.random(0, 255)

  highlightColor = Color3.fromRGB(r, g, b)
  
  wait(2)
end
