local Fluent = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/main.lua"))()
local Window = Fluent:CreateWindow({
    Title = "CiriliMinu 🤡",
    SubTitle = "Roube um Palhaço",
    TabWidth = 160,
    Size = UDim2.fromOffset(500, 380),
    Acrylic = true,
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.End
})

local Tabs = {
    Main = Window:AddTab({ Title = "🤡 Farm", Icon = "home" }),
}

local plr = game.Players.LocalPlayer
local char = plr.Character or plr.CharacterAdded:Wait()
local Root = char:WaitForChild("HumanoidRootPart")

local baseCFrame = nil
Tabs.Main:AddButton({
    Title = "1. Salvar Minha Base (Fica na base e clica)",
    Callback = function()
        baseCFrame = plr.Character.HumanoidRootPart.CFrame
        Fluent:Notify({Title = "Base Salva!", Content = "Base salva com sucesso", Duration = 3})
    end
})

getgenv().AutoFarm = false
getgenv().AutoKit = false

Tabs.Main:AddToggle("Farm", { Title = "2. Auto Farm Palhaço", Default = false }):OnChanged(function(v)
    getgenv().AutoFarm = v
    if v and not baseCFrame then
        baseCFrame = Root.CFrame
        Fluent:Notify({Title = "Aviso", Content = "Salvei tua base automatico na posição atual", Duration = 3})
    end
end)

Tabs.Main:AddToggle("Kit", { Title = "Kitar depois de roubar", Default = false }):OnChanged(function(v)
    getgenv().AutoKit = v
end)

-- LOOP QUE REALMENTE FUNCIONA NO DELTA
task.spawn(function()
    while true do
        task.wait(0.3)
        if getgenv().AutoFarm then
            pcall(function()
                local tool = plr.Character and plr.Character:FindFirstChildOfClass("Tool")
                
                if tool and baseCFrame then
                    -- TA COM PALHAÇO = VOLTA PRA BASE
                    Root.CFrame = baseCFrame + Vector3.new(0,3,0)
                    task.wait(1)
                    if getgenv().AutoKit then
                        game:GetService("TeleportService"):Teleport(game.PlaceId, plr)
                    end
                else
                    -- SEM PALHAÇO = PROCURA PRA ROUBAR
                    for _,v in pairs(workspace:GetDescendants()) do
                        if v:IsA("ProximityPrompt") and v.Enabled then
                            local model = v.Parent
                            local hrp = model:FindFirstChild("HumanoidRootPart") or model.Parent:FindFirstChild("HumanoidRootPart")
                            if hrp then
                                local dist = (hrp.Position - Root.Position).Magnitude
                                if dist < 500 then
                                    Root.CFrame = hrp.CFrame + Vector3.new(0,0,3)
                                    task.wait(0.2)
                                    fireproximityprompt(v)
                                    break
                                end
                            end
                        end
                    end
                end
            end)
        end
    end
end)

Window:SelectTab(1)
Fluent:Notify({Title = "CiriliMinu Hub", Content = "Hub carregado! Salva tua base primeiro", Duration = 5})
