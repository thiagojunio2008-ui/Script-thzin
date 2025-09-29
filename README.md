-- Sistema de Level Up
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
    -- cria valores do jogador
    local stats = Instance.new("Folder")
    stats.Name = "Stats"
    stats.Parent = player

    local level = Instance.new("IntValue")
    level.Name = "Level"
    level.Value = 1
    level.Parent = stats

    local xp = Instance.new("IntValue")
    xp.Name = "XP"
    xp.Value = 0
    xp.Parent = stats
end)

-- Função para dar XP
function AddXP(player, amount)
    local stats = player:FindFirstChild("Stats")
    if stats then
        local xp = stats:FindFirstChild("XP")
        local level = stats:FindFirstChild("Level")
        xp.Value += amount

        if xp.Value >= (level.Value * 100) then
            xp.Value = 0
            level.Value += 1
            print(player.Name .. " subiu para o level " .. level.Value)
        end
    end
end
