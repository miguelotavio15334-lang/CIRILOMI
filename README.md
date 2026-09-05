-- 👑 CIRILOMI HUB : Blox Fruits - ADMIN ONLY - VISUAL REDZ HUB
local plr = game.Players.LocalPlayer
local Players = game:GetService("Players")

-- LISTA DE ADMS - SÓ CIRILOMI E QUEM VOCÊ COLOCAR
local ADMINS = {"CIRILOMI", plr.Name}
local isAdmin = true

local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "CIRILOMIHUB"; gui.ResetOnSpawn = false

-- FRAME PRINCIPAL igual Redz Hub
local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 700, 0, 420)
main.Position = UDim2.new(0.5, -350, 0.5, -210)
main.BackgroundColor3 = Color3.fromRGB(14,14,14)
main.Active = true; main.Draggable = true
Instance.new("UICorner", main).CornerRadius = UDim.new(0,12)
Instance.new("UIStroke", main).Color = Color3.fromRGB(30,30,30)

-- TOP BAR
local top = Instance.new("Frame", main)
top.Size = UDim2.new(1,0,0,45); top.BackgroundColor3 = Color3.fromRGB(20,20,20)
Instance.new("UICorner", top).CornerRadius = UDim.new(0,12)

local titulo = Instance.new("TextLabel", top)
titulo.Size = UDim2.new(0.85,0,1,0); titulo.Position = UDim2.new(0,15,0,0)
titulo.Text = "👑 cirilomi hub : Blox Fruits by CIRILOMI"; titulo.TextXAlignment = Enum.TextXAlignment.Left
titulo.TextColor3 = Color3.fromRGB(140,80,255); titulo.Font = Enum.Font.GothamBlack; titulo.TextScaled = true; titulo.BackgroundTransparency = 1

local btnClose = Instance.new("TextButton", top)
btnClose.Size = UDim2.new(0,30,0,30); btnClose.Position = UDim2.new(1,-35,0,7)
btnClose.Text = "X"; btnClose.TextScaled=true; btnClose.BackgroundTransparency=1; btnClose.TextColor3=Color3.fromRGB(150,150,150)
btnClose.MouseButton1Click:Connect(function() main.Visible=false end)

-- SIDEBAR
local sidebar = Instance.new("Frame", main)
sidebar.Size = UDim2.new(0, 165, 1, -50); sidebar.Position = UDim2.new(0,5,0,50)
sidebar.BackgroundColor3 = Color3.fromRGB(18,18,18)
Instance.new("UICorner", sidebar).CornerRadius = UDim.new(0,10)

local scrollSide = Instance.new("ScrollingFrame", sidebar)
scrollSide.Size = UDim2.new(1,0,1,0); scrollSide.BackgroundTransparency=1; scrollSide.ScrollBarThickness=0
scrollSide.CanvasSize = UDim2.new(0,0,0,500)

local menus = {
	{"💬 Discord", true},
	{"👥 Players ADM", false},
	{"🛡️ Moderation", false},
	{"📜 Quest | Items ADM", false},
	{"🎣 Auto Fishing ADM", false},
	{"🌊 Sea Event ADM", false},
	{"👑 Race V4 Control", false},
	{"🏝️ Islands TP", false},
	{"🍎 Raid/Fruits Give", false},
	{"📊 Stats Manager", false},
	{"📍 Teleport ADM", false},
	{"📈 Status Server", false},
	{"👁️ Visual ADM", false},
}

for i, info in ipairs(menus) do
	local b = Instance.new("TextButton", scrollSide)
	b.Size = UDim2.new(0.92,0,0,32); b.Position = UDim2.new(0.04,0,0,(i-1)*36)
	b.Text = " "..info[1]; b.TextXAlignment=Enum.TextXAlignment.Left; b.TextScaled=true
	b.BackgroundColor3 = info[2] and Color3.fromRGB(60,40,100) or Color3.fromRGB(25,25,25)
	b.TextColor3 = info[2] and Color3.new(1,1,1) or Color3.fromRGB(150,150,150)
	b.Font = Enum.Font.Gotham; Instance.new("UICorner", b)
	if info[2] then
		local linha = Instance.new("Frame", b); linha.Size=UDim2.new(0,3,1,0); linha.BackgroundColor3=Color3.fromRGB(140,80,255); Instance.new("UICorner", linha)
	end
end

-- PAINEL DIREITO
local painel = Instance.new("Frame", main)
painel.Size = UDim2.new(1,-180,1,-50); painel.Position = UDim2.new(0,175,0,50)
painel.BackgroundColor3 = Color3.fromRGB(18,18,18)
Instance.new("UICorner", painel).CornerRadius = UDim.new(0,10)

local scrollPainel = Instance.new("ScrollingFrame", painel)
scrollPainel.Size = UDim2.new(1,0,1,0); scrollPainel.BackgroundTransparency=1; scrollPainel.ScrollBarThickness=3
scrollPainel.CanvasSize = UDim2.new(0,0,0,900)

local function criarToggle(nome, desc, y, ligado)
	local f = Instance.new("Frame", scrollPainel)
	f.Size = UDim2.new(0.96,0,0,58); f.Position = UDim2.new(0.02,0,0,y)
	f.BackgroundColor3 = Color3.fromRGB(28,28,28); Instance.new("UICorner", f)
	
	local t1 = Instance.new("TextLabel", f); t1.Size=UDim2.new(0.68,0,0.5,0); t1.Position=UDim2.new(0,10,0,5)
	t1.Text=nome; t1.TextXAlignment=Enum.TextXAlignment.Left; t1.TextScaled=true; t1.BackgroundTransparency=1; t1.TextColor3=Color3.new(1,1,1); t1.Font=Enum.Font.GothamBold
	
	local t2 = Instance.new("TextLabel", f); t2.Size=UDim2.new(0.68,0,0.4,0); t2.Position=UDim2.new(0,10,0,30)
	t2.Text=desc; t2.TextXAlignment=Enum.TextXAlignment.Left; t2.TextScaled=true; t2.BackgroundTransparency=1; t2.TextColor3=Color3.fromRGB(120,120,120); t2.Font=Enum.Font.Gotham
	
	local toggleBG = Instance.new("Frame", f); toggleBG.Size=UDim2.new(0,52,0,28); toggleBG.Position=UDim2.new(1,-62,0,15)
	toggleBG.BackgroundColor3=ligado and Color3.fromRGB(140,80,255) or Color3.fromRGB(60,60,60); Instance.new("UICorner", toggleBG).CornerRadius=UDim.new(1,0)
	
	local bolinha = Instance.new("Frame", toggleBG); bolinha.Size=UDim2.new(0,22,0,22); bolinha.Position=UDim2.new(ligado and 1 or 0, ligado and -24 or 2, 0,3)
	bolinha.BackgroundColor3=Color3.new(1,1,1); Instance.new("UICorner", bolinha).CornerRadius=UDim.new(1,0)
	
	local btn = Instance.new("TextButton", f); btn.Size=UDim2.new(1,0,1,0); btn.BackgroundTransparency=1; btn.Text=""
	local on = ligado
	btn.MouseButton1Click:Connect(function()
		on=not on
		toggleBG.BackgroundColor3=on and Color3.fromRGB(140,80,255) or Color3.fromRGB(60,60,60)
		bolinha.Position=UDim2.new(on and 1 or 0, on and -24 or 2, 0,3)
	end)
	return f
end

criarToggle("👑 CIRILOMI - God Mode ADM", "Ativa god mode só pra CIRILOMI", 10, true)
criarToggle("Kick Player", "Expulsa troll do server - CIRILOMI", 75, false)
criarToggle("Ban Player", "Bane hacker permanente", 140, false)
criarToggle("Give Fruit CIRILOMI", "CIRILOMI dá fruta de evento", 205, false)
criarToggle("Spawn Boss Event", "CIRILOMI spawna boss pra evento", 270, true)
criarToggle("Server Lock CIRILOMI", "Tranca server - só CIRILOMI deixa entrar", 335, false)
criarToggle("Logs Discord CIRILOMI", "Manda logs ADM pro Discord da CIRILOMI", 400, true)
criarToggle("Spectate + TP", "CIRILOMI vê tela do player", 465, false)
criarToggle("Auto Quest Skull Guitar", "CIRILOMI completa auto - ADM", 530, false)
criarToggle("Auto CDK", "Completes all 6 CDK trials + Boss automatically - CIRILOMI", 595, true)

print("👑 CIRILOMI HUB CARREGADO - SÓ PRA ADM CIRILOMI!")
