-- ROUBE UM PALHAÇO - AUTO STEAL SIMPLES (SEM HUB)
getgenv().AutoSteal = true
getgenv().AutoQuit = true

local plr = game.Players.LocalPlayer
local Root = plr.Character:WaitForChild("HumanoidRootPart")

-- ACHAR TUA BASE (anda uma vez na tua base antes de ligar)
local MinhaBasePos = nil
for _,v in pairs(workspace:GetDescendants()) do
    if v.Name == "TouchInterest" and v.Parent.Name:lower():find("base") then
        if (v.Parent.Position - Root.Position).Magnitude < 50 then
            MinhaBasePos = v.Parent.CFrame + Vector3.new(0,5,0)
        end
    end
end

-- Se não achar automatico, salva tua posição atual como base
if not MinhaBasePos then
    MinhaBasePos = Root.CFrame
    print("Base salva na tua posição atual!")
end

spawn(function()
    while wait(0.3) do
        if getgenv().AutoSteal then
            pcall(function()
                -- 1. VER SE TA SEGURANDO ALGO
                local holding = plr.Character:FindFirstChildOfClass("Tool")
                
                if holding then
                    -- TA SEGURANDO = LEVA PRA BASE
                    Root.CFrame = MinhaBasePos
                    wait(1.5)
                    if getgenv().AutoQuit then
                        plr:Kick("🤡 Roubado!")
                    end
                else
                    -- NÃO TA SEGURANDO = PEGA PALHAÇO
                    for _,v in pairs(workspace:GetDescendants()) do
                        if v:IsA("ProximityPrompt") then
                            if v.ObjectText:lower():find("roub") or v.ActionText:lower():find("roub") or v.Parent.Name:lower():find("palha") then
                                local model = v.Parent
                                local hrp = model:FindFirstChild("HumanoidRootPart") or model.Parent:FindFirstChild("HumanoidRootPart")
                                if hrp and (hrp.Position - Root.Position).Magnitude < 1000 then
                                    Root.CFrame = hrp.CFrame + Vector3.new(0,0,3)
                                    wait(0.2)
                                    fireproximityprompt(v, 1)
                                end
                            end
                        end
                    end
                end
            end)
        end
    end
end)

print("RODANDO! Pega palhaço e leva pra base")
