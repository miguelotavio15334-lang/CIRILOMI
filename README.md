-- FUNÇÃO NOVA PARA ACHAR TUA BASE (100% FUNCIONAL)
function GetPlot()
    -- 1. Tenta achar pelo nome padrão
    local plots = workspace:FindFirstChild("Plots") or workspace:FindFirstChild("Bases") or workspace:FindFirstChild("Tycoons")
    if plots then
        for _,v in pairs(plots:GetChildren()) do
            local owner = v:FindFirstChild("Owner") or v:FindFirstChild("Player") or v:FindFirstChild("OwnedBy")
            if owner and owner.Value == plr.Name then
                return v
            end
            -- Se for por nome da pasta
            if v.Name == plr.Name or v.Name:find(plr.Name) then
                return v
            end
        end
    end
    -- 2. Se não achar, pega o Spawn mais perto
    for _,v in pairs(workspace:GetDescendants()) do
        if v.Name == "SpawnLocation" and v:IsA("SpawnLocation") then
            if v:FindFirstChild("Owner") and v.Owner.Value == plr.Name then
                return v.Parent
            end
        end
    end
    return nil
end

function IsHoldingClown()
    if plr.Character:FindFirstChildOfClass("Tool") then return true end
    if plr.Character:FindFirstChild("Palhaço") then return true end
    for _,v in pairs(plr.Character:GetChildren()) do
        if v:IsA("Model") then return true end
    end
    return false
end

-- LOOP NOVO COM TWEEN QUE NÃO BUGA
spawn(function()
    while wait(0.3) do
        if getgenv().AutoSteal then
            pcall(function()
                if IsHoldingClown() then
                    local plot = GetPlot()
                    if plot then
                        local target = plot:FindFirstChild("Delivery") or plot:FindFirstChild("Hitbox") or plot:FindFirstChild("Base") or plot
                        local cf = target.CFrame + Vector3.new(0,5,0)
                        if target:IsA("BasePart") then cf = target.CFrame + Vector3.new(0,5,0) end
                        
                        Root.CFrame = cf -- FORÇA TP
                        wait(1)
                        if getgenv().AutoQuit then
                            game.Players.LocalPlayer:Kick("🤡 Palhaço roubado com sucesso!")
                        end
                    else
                        -- SE NÃO ACHAR BASE, AVISA
                        Fluent:Notify({Title = "Base não encontrada", Content = "Clica em 'Achar Minha Base' antes", Duration = 2})
                    end
                else
                    -- PROCURAR PALHAÇO
                    local clown = nil
                    for _,v in pairs(workspace:GetDescendants()) do
                        if v:IsA("ProximityPrompt") and v.ObjectText:lower():find("palha") then
                            clown = v.Parent
                            break
                        end
                    end
                    if clown and clown:FindFirstChild("HumanoidRootPart") or clown.Parent:FindFirstChild("HumanoidRootPart") then
                        local hrp = clown:FindFirstChild("HumanoidRootPart") or clown.Parent:FindFirstChild("HumanoidRootPart")
                        Root.CFrame = hrp.CFrame + Vector3.new(0,0,4)
                        wait(0.3)
                        fireproximityprompt(clown:IsA("ProximityPrompt") and clown or clown:FindFirstChildOfClass("ProximityPrompt"), 1)
                    end
                end
            end)
        end
    end
end)
