local player = game.Players.LocalPlayer
local workspace = game:GetService("Workspace")

local function autoMine()
    while true do
        for _, part in pairs(workspace:GetDescendants()) do
            if part:IsA("BasePart") and (part.Name == "coal" or part.Name == "ore") then
                firetouchinterest(player.Character.HumanoidRootPart, part, 0)
                wait(0.2)
                firetouchinterest(player.Character.HumanoidRootPart, part, 1)
            end
        end
        wait(2)
    end
end

player.CharacterAdded:Connect(function()
    wait(1)
    autoMine()
end)

if player.Character then
    autoMine()
end
