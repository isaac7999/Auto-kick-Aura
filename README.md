-- Auto Quit ao atingir 10 de HP ou menos
local player = game.Players.LocalPlayer
local humanoid = player.Character and player.Character:FindFirstChildOfClass("Humanoid") or nil

-- Espera o personagem carregar se ainda não tiver
if not humanoid then
    player.CharacterAdded:Wait()
    wait(1)
    humanoid = player.Character:WaitForChild("Humanoid")
end

-- Função de verificação do HP
local function monitorHP()
    humanoid.HealthChanged:Connect(function(currentHealth)
        if currentHealth <= 10 then
            game:Shutdown() -- Encerra imediatamente o jogo
        end
    end)
end

monitorHP()
