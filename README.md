-- Coloque este LocalScript em StarterPlayerScripts

local player = game.Players.LocalPlayer
local workspace = game:GetService("Workspace")

-- Função que tenta minerar automaticamente
local function autoMine()
    while true do
        -- Procura por minas de carvão e minério no workspace
        for _, part in pairs(workspace:GetDescendants()) do
            if part:IsA("BasePart") and (part.Name == "coal" or part.Name == "ore") then
                -- Simula toque/mineração
                firetouchinterest(player.Character.HumanoidRootPart, part, 0)
                wait(0.2)
                firetouchinterest(player.Character.HumanoidRootPart, part, 1)
            end
        end
        wait(2) -- Tempo entre cada ciclo de farm
    end
end

-- Aguarda o personagem ser carregado
player.CharacterAdded:Connect(function()
    wait(1) -- Aguarda o personagem spawnar totalmente
    autoMine()
end)

-- Se o personagem já estiver carregado, inicia imediatamente
if player.Character then
    autoMine()
end
