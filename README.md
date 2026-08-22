local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local Window = Fluent:CreateWindow({
    Title = "❤️CiriliMinu - Roube um Palhaço❤️",
    SubTitle = "| Auto Steal + Base + Quit",
    TabWidth = 180,
    Size = UDim2.fromOffset(580, 400),
    Acrylic = false,
    Theme = "Black",
    MinimizeKey = Enum.KeyCode.End
})

-- SERVICES
local plr = game.Players.LocalPlayer
local CoreGui = game:GetService("CoreGui")
local VirtualInputManager = game:GetService("VirtualInputManager")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")

repeat wait() until plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
local Root = plr.Character.HumanoidRootPart

getgenv().AutoSteal = false
getgenv().AutoQuit = true
getgenv().Alvo = "Palhaço" -- nome do palhaço mais raro

-- FUNÇÕES
function _tp(cf) Root.CFrame = cf end

function GetPlot()
    -- Tenta achar tua base
    for _,v in pairs(workspace.Plots:GetChildren()) do
        if v:FindFirstChild("Owner") and v.Owner.Value == plr.Name then
            return v
        end
    end
    return nil
end

function GetBestClown()
    local best = nil
    local bestVal = -1
    for _,v in pairs(workspace.Clowns:GetChildren()) do -- ou workspace:FindFirstChild("Palhaços")
        if v:FindFirstChild("Value") and v:FindFirstChild("HumanoidRootPart") then
            if v.Value.Value > bestVal and not v:GetAttribute("Stolen") then
                bestVal = v.Value.Value
                best = v
            end
        end
    end
    -- Tenta de outro jeito se não achar
    if not best then
        for _,v in pairs(workspace:GetDescendants()) do
            if v.Name:lower():find("palha") and v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") then
                return v
            end
        end
    end
    return best
end

function IsHoldingClown()
    -- Verifica se tá segurando palhaço
    for _,tool in pairs(plr.Character:GetChildren()) do
        if tool.Name:lower():find("palha") or tool:GetAttribute("Clown") then
            return true
        end
    end
    if plr.Character:FindFirstChild("Clown") or plr:GetAttribute("HoldingClown") then
        return true
    end
    return false
end

-- BOTÃO FLUTUANTE
local ScreenGui = Instance.new("ScreenGui") ScreenGui.Parent = CoreGui
local ToggleButton = Instance.new("ImageButton")
ToggleButton.Size = UDim2.new(0, 50, 0, 50) ToggleButton.Position = UDim2.new(0.15, 0, 0.15, 0)
ToggleButton.Image = "rbxassetid://130364232574601" ToggleButton.Parent = ScreenGui
Instance.new("UICorner", ToggleButton).CornerRadius = UDim.new(1,0)
ToggleButton.MouseButton1Click:Connect(function() VirtualInputManager:SendKeyEvent(true, "End", false, game) VirtualInputManager:SendKeyEvent(false, "End", false, game) end)
local dragging = false local dragInput, dragStart, startPos
ToggleButton.InputBegan:Connect(function(input) if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then dragging = true dragStart = input.Position startPos = ToggleButton.Position end end)
ToggleButton.InputChanged:Connect(function(input) if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then dragInput = input end end)
UserInputService.InputChanged:Connect(function(input) if dragging and input == dragInput then local delta = input.Position - dragStart ToggleButton.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y) end end)

-- ABAS
local Tabs = {
  Main = Window:AddTab({Title = "🤡Roube um Palhaço", Icon = ""}),
  Settings = Window:AddTab({Title = "⚙️Settings", Icon = ""}),
}

-- TOGGLE PRINCIPAL
Tabs.Main:AddToggle("AutoFarmPalhaco", {Title = "Auto Farm Palhaço", Default = false}):OnChanged(function(v) getgenv().AutoSteal = v end)
Tabs.Main:AddToggle("AutoQuit", {Title = "Kitar após roubar [ON]", Default = true}):OnChanged(function(v) getgenv().AutoQuit = v end)
Tabs.Main:AddButton({Title = "Achar Minha Base", Callback = function()
    local plot = GetPlot()
    if plot then _tp(plot:FindFirstChild("Spawn").CFrame + Vector3.new(0,5,0)) else Fluent:Notify({Title = "Erro", Content = "Base não encontrada", Duration = 3}) end
end})

-- LOOP AUTO STEAL
spawn(function()
    while wait(0.2) do
        if getgenv().AutoSteal then
            pcall(function()
                -- SE JA TIVER SEGURANDO PALHAÇO -> LEVA PRA BASE
                if IsHoldingClown() then
                    local plot = GetPlot()
                    if plot then
                        local basePos = plot:FindFirstChild("Delivery") or plot:FindFirstChild("Spawn") or plot:FindFirstChild("Center")
                        if basePos then
                            _tp(basePos.CFrame + Vector3.new(0,5,0))
                            wait(1.5)
                            if getgenv().AutoQuit then
                                Fluent:Notify({Title = "Roubado!", Content = "Kitando pra proteger...", Duration = 2})
                                wait(1)
                                game:Shutdown() -- Kita
                                -- Se Shutdown não funcionar, usa:
                                -- plr:Kick("Palhaço roubado com sucesso 🤡")
                            end
                        end
                    end
                else
                    -- SE NÃO TIVER PALHAÇO -> VAI PEGAR
                    local clown = GetBestClown()
                    if clown and clown:FindFirstChild("HumanoidRootPart") then
                        _tp(clown.HumanoidRootPart.CFrame + Vector3.new(0,0,3))
                        wait(0.2)
                        -- Tenta interagir
                        fireproximityprompt(clown:FindFirstChildOfClass("ProximityPrompt"), 1)
                        for _,prompt in pairs(clown:GetDescendants()) do
                            if prompt:IsA("ProximityPrompt") then
                                fireproximityprompt(prompt)
                            end
                        end
                    end
                end
            end)
        end
    end
end)

Window:SelectTab(1)
Fluent:Notify({Title = "CiriliMinu", Content = "Roube um Palhaço carregado! Liga o Auto Farm", Duration = 5})
