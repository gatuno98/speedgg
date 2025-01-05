-- Define a velocidade de corrida (em unidades por segundo)
local velocidadeRapida = 100

-- Função para ajustar a velocidade de corrida
local function aumentarVelocidade()
    local player = game.Players.LocalPlayer
    local character = player.Character

    -- Verifica se o personagem e o humanoide existem
    if character and character:FindFirstChild("Humanoid") then
        local humanoide = character:FindFirstChild("Humanoid")
        
        -- Ajusta a velocidade de corrida
        humanoide.WalkSpeed = velocidadeRapida
    end
end

-- Função para retornar à velocidade normal (caso necessário)
local function velocidadeNormal()
    local player = game.Players.LocalPlayer
    local character = player.Character

    if character and character:FindFirstChild("Humanoid") then
        local humanoide = character:FindFirstChild("Humanoid")
        
        -- Ajusta a velocidade para o valor padrão (normal)
        humanoide.WalkSpeed = 16
    end
end

-- Inicia a velocidade rápida ao pressionar a tecla "Shift" (opcional)
game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.LeftShift then
        aumentarVelocidade()
    end
end)

-- Retorna à velocidade normal ao soltar a tecla "Shift"
game:GetService("UserInputService").InputEnded:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.LeftShift then
        velocidadeNormal()
    end
end)
