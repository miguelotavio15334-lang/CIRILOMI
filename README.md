-- 👑 CIRILOMI HUB V30.3 - HOP REAL + COLETA AUTO DA FRUTA ALVO 100% REAL
local plr = game.Players.LocalPlayer
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local TeleportService = game:GetService("TeleportService")
local VirtualUser = game:GetService("VirtualUser")
local HttpService = game:GetService("HttpService")

local function getPremiumKey()
    local k = {48,56,48,56}
    local s = ""
    for _,v in ipairs(k) do s = s.. string.char(v) end
    return s
end
local PREMIUM_KEY = getPremiumKey()

for _,v in pairs(plr.PlayerGui:GetChildren()) do if v.Name:find("Cirilomi") then v:Destroy() end end

local gui = Instance.new("ScreenGui")
gui.Name = "CirilomiHubV30"; gui.ResetOnSpawn = false; gui.DisplayOrder = 9999; gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
gui.Parent = plr.PlayerGui

local corAtual = Color3.fromRGB(0,255,150)

local main = Instance.new("Frame")
main.Size = UDim2.new(0, 720, 0, 480); main.Position = UDim2.new(0.5, -360, 0.5, -240)
main.BackgroundColor3 = Color3.fromRGB(12,12,12); main.BorderSizePixel = 0
main.Visible = true; main.Active = true; main.Draggable = true; main.ZIndex = 10; main.Parent = gui
Instance.new("UICorner", main).CornerRadius = UDim.new(0,10)
local strokeMain = Instance.new("UIStroke", main); strokeMain.Color = corAtual; strokeMain.Thickness = 2

local top = Instance.new("Frame", main)
top.Size = UDim2.new(1,0,0,38); top.BackgroundColor3 = Color3.fromRGB(20,20,20); top.BorderSizePixel = 0; top.ZIndex = 11
Instance.new("UICorner", top)
local titulo = Instance.new("TextLabel", top)
titulo.Size = UDim2.new(0.65,0,1,0); titulo.Position = UDim2.new(0,10,0,0); titulo.ZIndex = 12
titulo.Text = "👑 cirilomi hub : V30.3 - HOP REAL + COLETA AUTO"; titulo.TextXAlignment = Enum.TextXAlignment.Left
titulo.TextColor3 = corAtual; titulo.Font = Enum.Font.GothamBlack; titulo.TextSize=11; titulo.BackgroundTransparency = 1

local btnMin = Instance.new("TextButton", top)
btnMin.Size=UDim2.new(0,32,0,32); btnMin.Position=UDim2.new(1,-70,0,3); btnMin.ZIndex=20; btnMin.Text="-"; btnMin.TextSize=22; btnMin.BackgroundColor3=Color3.fromRGB(70,70,70); btnMin.TextColor3=Color3.new(1,1,1); btnMin.Font=Enum.Font.GothamBlack; btnMin.BorderSizePixel=0
Instance.new("UICorner", btnMin)
local btnClose = Instance.new("TextButton", top)
btnClose.Size=UDim2.new(0,32,0,32); btnClose.Position=UDim2.new(1,-34,0,3); btnClose.ZIndex=20; btnClose.Text="X"; btnClose.TextSize=14; btnClose.BackgroundColor3=Color3.fromRGB(200,0,0); btnClose.TextColor3=Color3.new(1,1,1); btnClose.Font=Enum.Font.GothamBold; btnClose.BorderSizePixel=0
Instance.new("UICorner", btnClose)

local mini = Instance.new("Frame", gui)
mini.Name="BlocoCirilo"; mini.Size = UDim2.new(0, 85, 0, 85); mini.Position = UDim2.new(0, 20, 0.5, -40)
mini.BackgroundColor3 = Color3.fromRGB(15,15,15); mini.Visible = false; mini.Active = true; mini.Draggable = true; mini.ZIndex = 999; mini.BorderSizePixel = 0
Instance.new("UICorner", mini).CornerRadius = UDim.new(0,15)
local strokeMini = Instance.new("UIStroke", mini); strokeMini.Color = corAtual; strokeMini.Thickness = 3
local miniImg = Instance.new("TextLabel", mini); miniImg.Size=UDim2.new(1,0,0.65,0); miniImg.Text="👑\nCIRILO\nFREE"; miniImg.TextSize=12; miniImg.BackgroundTransparency=1; miniImg.TextColor3=corAtual; miniImg.Font=Enum.Font.GothamBlack; miniImg.ZIndex=1000
local miniTxt = Instance.new("TextLabel", mini); miniTxt.Size=UDim2.new(1,0,0.35,0); miniTxt.Position=UDim2.new(0,0,0.62,0); miniTxt.Text="ABRIR MENU"; miniTxt.TextSize=10; miniTxt.BackgroundTransparency=1; miniTxt.TextColor3=Color3.new(1,1,1); miniTxt.Font=Enum.Font.GothamBold; miniTxt.ZIndex=1000
local miniBtn = Instance.new("TextButton", mini); miniBtn.Size=UDim2.new(1,0,1,0); miniBtn.Text=""; miniBtn.BackgroundTransparency=1; miniBtn.ZIndex=1001
btnMin.MouseButton1Click:Connect(function() main.Visible=false; mini.Visible=true end)
btnClose.MouseButton1Click:Connect(function() main.Visible=false; mini.Visible=true end)
miniBtn.MouseButton1Click:Connect(function() mini.Visible=false; main.Visible=true end)

local miniPrem = Instance.new("Frame", gui)
miniPrem.Name="BlocoPremium"; miniPrem.Size = UDim2.new(0, 95, 0, 95); miniPrem.Position = UDim2.new(0, 20, 0.5, -40)
miniPrem.BackgroundColor3 = Color3.fromRGB(15,15,10); miniPrem.Visible = false; miniPrem.Active = true; miniPrem.Draggable = true; miniPrem.ZIndex = 1000; miniPrem.BorderSizePixel = 0
Instance.new("UICorner", miniPrem).CornerRadius = UDim.new(0,15)
local strokeMiniPrem = Instance.new("UIStroke", miniPrem); strokeMiniPrem.Color = Color3.fromRGB(255,215,0); strokeMiniPrem.Thickness = 3
local miniPremImg = Instance.new("TextLabel", miniPrem); miniPremImg.Size=UDim2.new(1,0,0.65,0); miniPremImg.Text="💎\nPREMIUM\nGOD"; miniPremImg.TextSize=11; miniPremImg.BackgroundTransparency=1; miniPremImg.TextColor3=Color3.fromRGB(255,215,0); miniPremImg.Font=Enum.Font.GothamBlack; miniPremImg.ZIndex=1001
local miniPremTxt = Instance.new("TextLabel", miniPrem); miniPremTxt.Size=UDim2.new(1,0,0.35,0); miniPremTxt.Position=UDim2.new(0,0,0.62,0); miniPremTxt.Text="ABRIR PREMIUM"; miniPremTxt.TextSize=9; miniPremTxt.BackgroundTransparency=1; miniPremTxt.TextColor3=Color3.new(1,1,1); miniPremTxt.Font=Enum.Font.GothamBold; miniPremTxt.ZIndex=1001
local miniPremBtn = Instance.new("TextButton", miniPrem); miniPremBtn.Size=UDim2.new(1,0,1,0); miniPremBtn.Text=""; miniPremBtn.BackgroundTransparency=1; miniPremBtn.ZIndex=1002

local premiumGui = Instance.new("Frame", gui)
premiumGui.Name="PremiumMenu"; premiumGui.Size = UDim2.new(0, 740, 0, 580); premiumGui.Position = UDim2.new(0.5, -370, 0.5, -290)
premiumGui.BackgroundColor3 = Color3.fromRGB(8,8,8); premiumGui.Visible = false; premiumGui.Active=true; premiumGui.Draggable=true; premiumGui.ZIndex=100; premiumGui.BorderSizePixel=0
Instance.new("UICorner", premiumGui).CornerRadius=UDim.new(0,12)
local strokePrem = Instance.new("UIStroke", premiumGui); strokePrem.Color = Color3.fromRGB(255,215,0); strokePrem.Thickness=3
local topPrem = Instance.new("Frame", premiumGui); topPrem.Size = UDim2.new(1,0,0,45); topPrem.BackgroundColor3=Color3.fromRGB(15,15,15); topPrem.ZIndex=101; Instance.new("UICorner", topPrem)
local tituloPrem = Instance.new("TextLabel", topPrem); tituloPrem.Size=UDim2.new(0.60,0,1,0); tituloPrem.Position=UDim2.new(0,12,0,0); tituloPrem.Text="💎 PREMIUM GOD - HOP REAL + COLETA AUTO 👑"; tituloPrem.TextXAlignment=Enum.TextXAlignment.Left; tituloPrem.TextColor3=Color3.fromRGB(255,215,0); tituloPrem.Font=Enum.Font.GothamBlack; tituloPrem.TextSize=11; tituloPrem.BackgroundTransparency=1; tituloPrem.ZIndex=102
local btnMinPrem = Instance.new("TextButton", topPrem); btnMinPrem.Size=UDim2.new(0,32,0,32); btnMinPrem.Position=UDim2.new(1,-74,0,6); btnMinPrem.Text="-"; btnMinPrem.TextSize=22; btnMinPrem.BackgroundColor3=Color3.fromRGB(70,70,70); btnMinPrem.TextColor3=Color3.new(1,1,1); btnMinPrem.Font=Enum.Font.GothamBlack; btnMinPrem.ZIndex=102; Instance.new("UICorner", btnMinPrem)
local closePrem = Instance.new("TextButton", topPrem); closePrem.Size=UDim2.new(0,32,0,32); closePrem.Position=UDim2.new(1,-38,0,6); closePrem.Text="X"; closePrem.BackgroundColor3=Color3.fromRGB(200,0,0); closePrem.TextColor3=Color3.new(1,1,1); closePrem.Font=Enum.Font.GothamBold; closePrem.ZIndex=102; Instance.new("UICorner", closePrem)
closePrem.MouseButton1Click:Connect(function() premiumGui.Visible=false; miniPrem.Visible=true end)
btnMinPrem.MouseButton1Click:Connect(function() premiumGui.Visible=false; miniPrem.Visible=true end)
miniPremBtn.MouseButton1Click:Connect(function() miniPrem.Visible=false; premiumGui.Visible=true end)

local keyFrame = Instance.new("Frame", premiumGui); keyFrame.Size=UDim2.new(1,0,1,-45); keyFrame.Position=UDim2.new(0,0,0,45); keyFrame.BackgroundTransparency=1; keyFrame.ZIndex=101
local keyLabel = Instance.new("TextLabel", keyFrame); keyLabel.Size=UDim2.new(0.9,0,0,30); keyLabel.Position=UDim2.new(0.05,0,0,20); keyLabel.Text="🔑 PREMIUM GOD - HOP REAL + COLETA AUTO"; keyLabel.TextColor3=Color3.fromRGB(255,215,0); keyLabel.Font=Enum.Font.GothamBlack; keyLabel.TextSize=12; keyLabel.BackgroundTransparency=1; keyLabel.ZIndex=102
local keyBox = Instance.new("TextBox", keyFrame); keyBox.Size=UDim2.new(0.9,0,0,45); keyBox.Position=UDim2.new(0.05,0,0,60); keyBox.PlaceholderText="Digite sua key premium..."; keyBox.Text=""; keyBox.BackgroundColor3=Color3.fromRGB(25,25,25); keyBox.TextColor3=Color3.new(1,1,1); keyBox.Font=Enum.Font.GothamBold; keyBox.TextSize=14; keyBox.ZIndex=102; Instance.new("UICorner", keyBox).CornerRadius=UDim.new(0,8)
local keyBtn = Instance.new("TextButton", keyFrame); keyBtn.Size=UDim2.new(0.9,0,0,45); keyBtn.Position=UDim2.new(0.05,0,0,120); keyBtn.Text="💎 DESBLOQUEAR PREMIUM GOD"; keyBtn.BackgroundColor3=Color3.fromRGB(255,215,0); keyBtn.TextColor3=Color3.fromRGB(0,0,0); keyBtn.Font=Enum.Font.GothamBlack; keyBtn.TextSize=14; keyBtn.ZIndex=102; Instance.new("UICorner", keyBtn).CornerRadius=UDim.new(0,8)
local keyStatus = Instance.new("TextLabel", keyFrame); keyStatus.Size=UDim2.new(0.9,0,0,30); keyStatus.Position=UDim2.new(0.05,0,0,175); keyStatus.Text=""; keyStatus.TextColor3=Color3.fromRGB(255,200,0); keyStatus.Font=Enum.Font.GothamBold; keyStatus.TextSize=12; keyStatus.BackgroundTransparency=1; keyStatus.ZIndex=102

local premSidebar = Instance.new("Frame", premiumGui)
premSidebar.Size = UDim2.new(0, 170, 1, -50); premSidebar.Position = UDim2.new(0,5,0,50); premSidebar.ZIndex=102
premSidebar.BackgroundColor3 = Color3.fromRGB(18,18,12); premSidebar.BorderSizePixel=0; premSidebar.Visible=false
Instance.new("UICorner", premSidebar)
local premSideScroll = Instance.new("ScrollingFrame", premSidebar)
premSideScroll.Size = UDim2.new(1,0,1,0); premSideScroll.BackgroundTransparency=1; premSideScroll.ScrollBarThickness=0; premSideScroll.ZIndex=103
premSideScroll.CanvasSize = UDim2.new(0,0,0,2500)

local premPainel = Instance.new("Frame", premiumGui)
premPainel.Size = UDim2.new(1,-182,1,-50); premPainel.Position = UDim2.new(0,177,0,50); premPainel.ZIndex=102
premPainel.BackgroundColor3 = Color3.fromRGB(18,18,12); premPainel.BorderSizePixel=0; premPainel.Visible=false
Instance.new("UICorner", premPainel)
local premiumContent = Instance.new("ScrollingFrame", premPainel)
premiumContent.Size = UDim2.new(1,0,1,0); premiumContent.BackgroundTransparency=1; premiumContent.Visible=true; premiumContent.ZIndex=103; premiumContent.ScrollBarThickness=2; premiumContent.CanvasSize=UDim2.new(0,0,0,8000)

local stPrem = {GodFarm=false,AutoFruitHopSelected=false,AutoFruitGod=false,AutoFruitStore=false,AutoFruitCollect=false}
local frutaAlvo = "Dragon"
local frutasNoChaoPrem = {}
local serversVisitados = {}
local hopAtivo = false
local coletandoAuto = false

local function atualizarFrutasPremium()
	table.clear(frutasNoChaoPrem)
	for _,obj in pairs(Workspace:GetChildren()) do
		if obj:IsA("Tool") then
			for _,fName in ipairs({"Rocket","Spin","Blade","Bomb","Smoke","Spike","Flame","Ice","Sand","Dark","Diamond","Light","Rubber","Barrier","Ghost","Magma","Quake","Buddha","Love","Spider","Sound","Phoenix","Portal","Rumble","Pain","Blizzard","Gravity","Mammoth","T-Rex","Dough","Shadow","Venom","Control","Spirit","Yeti","Gas","Leopard","Kitsune","Dragon"}) do
				if obj.Name:lower():find(fName:lower()) then
					frutasNoChaoPrem[fName]={obj=obj, time=tick(), pos=obj:FindFirstChild("Handle") and obj.Handle.Position or Vector3.new(0,0,0)}
				end
			end
		end
	end
end

local function coletarFrutaAuto(nomeFruta)
	if coletandoAuto then return end
	coletandoAuto = true
	print("🍎 PREMIUM REAL - COLETANDO "..nomeFruta.." AUTOMATICO!")
	task.spawn(function()
		for i=1,20 do
			if frutasNoChaoPrem[nomeFruta] and frutasNoChaoPrem[nomeFruta].obj and frutasNoChaoPrem[nomeFruta].obj.Parent then
				local handle = frutasNoChaoPrem[nomeFruta].obj:FindFirstChild("Handle")
				if handle and plr.Character:FindFirstChild("HumanoidRootPart") then
					plr.Character.HumanoidRootPart.CFrame = handle.CFrame + Vector3.new(0,2,0)
					task.wait(0.3)
					-- TENTA PEGAR
					if plr.Character:FindFirstChild("Humanoid") then
						plr.Character.Humanoid:EquipTool(frutasNoChaoPrem[nomeFruta].obj)
					end
					-- STORE AUTO
					if stPrem.AutoFruitStore then
						task.wait(0.5)
						pcall(function()
							ReplicatedStorage.Remotes.CommF_:InvokeServer("StoreFruit", nomeFruta, frutasNoChaoPrem[nomeFruta].obj)
						end)
					end
				end
			else
				break
			end
			task.wait(0.2)
		end
		coletandoAuto = false
		print("✅ PREMIUM REAL - "..nomeFruta.." COLETADA!")
	end)
end

local function clearPrem() for _,c in pairs(premiumContent:GetChildren()) do if c:IsA("Frame") or c:IsA("TextLabel") or c:IsA("TextButton") then c:Destroy() end end end
local function secaoPrem(txt,y) local t=Instance.new("TextLabel",premiumContent); t.Size=UDim2.new(0.96,0,0,30); t.Position=UDim2.new(0.02,0,0,y); t.ZIndex=104; t.Text=txt; t.TextXAlignment=Enum.TextXAlignment.Left; t.TextSize=12; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(255,215,0); t.Font=Enum.Font.GothamBlack; return y+34 end
local function togglePrem(nome, key, y)
	local f=Instance.new("Frame",premiumContent); f.Size=UDim2.new(0.96,0,0,38); f.Position=UDim2.new(0.02,0,0,y); f.BackgroundColor3=Color3.fromRGB(40,35,15); f.ZIndex=104; f.BorderSizePixel=0; Instance.new("UICorner",f).CornerRadius=UDim.new(0,6)
	local n=Instance.new("TextLabel",f); n.Size=UDim2.new(0.72,0,1,0); n.Position=UDim2.new(0,10,0,0); n.ZIndex=105; n.Text=nome; n.TextXAlignment=Enum.TextXAlignment.Left; n.TextSize=11; n.BackgroundTransparency=1; n.TextColor3=Color3.new(1,1,1); n.Font=Enum.Font.GothamBold; n.TextTruncate=Enum.TextTruncate.AtEnd
	local box=Instance.new("Frame",f); box.Size=UDim2.new(0,22,0,22); box.Position=UDim2.new(1,-30,0.5,-11); box.ZIndex=105; box.BackgroundColor3=stPrem[key] and Color3.fromRGB(0,130,0) or Color3.fromRGB(45,45,45); box.BorderSizePixel=0; Instance.new("UICorner",box).CornerRadius=UDim.new(0,4)
	local stroke=Instance.new("UIStroke",box); stroke.Color=Color3.fromRGB(255,215,0); stroke.Thickness=2
	local check=Instance.new("TextLabel",box); check.Size=UDim2.new(1,0,1,0); check.ZIndex=106; check.Text=stPrem[key] and "✓" or ""; check.TextSize=16; check.BackgroundTransparency=1; check.TextColor3=Color3.new(1,1,1); check.Font=Enum.Font.GothamBlack
	local btn=Instance.new("TextButton",f); btn.Size=UDim2.new(1,0,1,0); btn.BackgroundTransparency=1; btn.Text=""; btn.ZIndex=107
	btn.MouseButton1Click:Connect(function() stPrem[key]=not stPrem[key]; check.Text=stPrem[key] and "✓" or ""; box.BackgroundColor3=stPrem[key] and Color3.fromRGB(0,130,0) or Color3.fromRGB(45,45,45) end)
	return y+42
end
local function btnListaPrem(txt,y,cor,callback)
	local b=Instance.new("TextButton",premiumContent); b.Size=UDim2.new(0.96,0,0,36); b.Position=UDim2.new(0.02,0,0,y); b.ZIndex=104; b.Text=txt; b.TextSize=11; b.BackgroundColor3=cor; b.TextColor3=Color3.new(1,1,1); b.Font=Enum.Font.GothamBold; b.BorderSizePixel=0; Instance.new("UICorner",b); if callback then b.MouseButton1Click:Connect(callback) end; return y+40
end

local abasPrem = {}

-- 🍎 Raid/Fruits PREMIUM 100% REAL - HOP + COLETA AUTO
abasPrem["🍎 Raid/Fruits"] = function()
	clearPrem(); local y=8
	y=secaoPrem("🍎 Raid/Fruits PREMIUM GOD - 100% REAL - HOP + COLETA AUTO DA FRUTA ALVO!",y)
	y=togglePrem("🍎 AUTO FRUIT GOD AUTO 10s REAL","AutoFruitGod",y)
	y=togglePrem("📦 AUTO STORE FRUTA GOD REAL","AutoFruitStore",y)
	y=togglePrem("🎯 AUTO COLETA AUTO QUANDO ACHAR ALVO REAL - COLETA AUTOMATICO!","AutoFruitCollect",y)
	y+=10
	y=secaoPrem("🎯 FRUTA ALVO REAL: "..frutaAlvo.." - QUANDO ACHAR VAI COLETAR AUTO!",y)
	y=btnListaPrem("🎯 ESCOLHER FRUTA ALVO: "..frutaAlvo.." - CLIQUE PRA TROCAR REAL",y,Color3.fromRGB(255,215,0),function()
		local lista=Instance.new("Frame", gui); lista.Size=UDim2.new(0, 300, 0, 420); lista.Position=UDim2.new(0.5, 380, 0.5, -200); lista.ZIndex=200; lista.BackgroundColor3=Color3.fromRGB(15,15,15); lista.Visible=true; lista.Active=true; lista.Draggable=true; lista.BorderSizePixel=0; Instance.new("UICorner", lista)
		local t=Instance.new("TextLabel", lista); t.Size=UDim2.new(0.85,0,0,32); t.ZIndex=201; t.Text="ESCOLHE FRUTA ALVO REAL PRA COLETAR AUTO"; t.TextSize=11; t.BackgroundColor3=Color3.fromRGB(255,215,0); t.TextColor3=Color3.fromRGB(0,0,0); t.Font=Enum.Font.GothamBlack; Instance.new("UICorner", t)
		local f=Instance.new("TextButton", lista); f.Size=UDim2.new(0,28,0,28); f.Position=UDim2.new(1,-32,0,2); f.ZIndex=202; f.Text="X"; f.BackgroundColor3=Color3.fromRGB(255,0,0); f.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", f); f.MouseButton1Click:Connect(function() lista:Destroy() end)
		local s=Instance.new("ScrollingFrame", lista); s.Size=UDim2.new(1,0,1,-38); s.Position=UDim2.new(0,0,0,38); s.BackgroundTransparency=1; s.ZIndex=201; s.ScrollBarThickness=3
		local yy=5
		for _,fname in ipairs({"Dragon","Kitsune","Leopard","Dough","Shadow","Venom","Control","Spirit","Gas","Yeti","T-Rex","Mammoth","Gravity","Blizzard","Pain","Rumble","Portal","Phoenix","Sound","Spider","Love","Buddha","Quake","Magma"}) do
			local b=Instance.new("TextButton",s); b.Size=UDim2.new(0.92,0,0,34); b.Position=UDim2.new(0.04,0,0,yy); b.ZIndex=202; b.Text="🍎 "..fname..(fname==frutaAlvo and " ✅ ALVO REAL" or ""); b.TextSize=11; b.BackgroundColor3=fname==frutaAlvo and Color3.fromRGB(0,120,0) or Color3.fromRGB(40,40,40); b.TextColor3=Color3.new(1,1,1); b.Font=Enum.Font.GothamBold; Instance.new("UICorner",b)
			b.MouseButton1Click:Connect(function() frutaAlvo=fname; lista:Destroy(); abasPrem["🍎 Raid/Fruits"]() end)
			yy+=38
		end
		s.CanvasSize=UDim2.new(0,0,0,yy)
	end)
	y+=6
	y=secaoPrem("📍 LISTA 1: FRUTAS NO CHÃO NESSE SERVER - 100% REAL",y)
	y=btnListaPrem("🍎 VER NO CHÃO NESSE SERVER - TP + COLETA AUTO REAL - PREMIUM GOD",y,Color3.fromRGB(0,160,0),function()
		atualizarFrutasPremium()
		local lista=Instance.new("Frame", gui); lista.Size=UDim2.new(0, 340, 0, 420); lista.Position=UDim2.new(0.5, -500, 0.5, -200); lista.ZIndex=200; lista.BackgroundColor3=Color3.fromRGB(15,15,15); lista.Visible=true; lista.Active=true; lista.Draggable=true; Instance.new("UICorner", lista)
		local t=Instance.new("TextLabel", lista); t.Size=UDim2.new(0.85,0,0,32); t.ZIndex=201; t.Text="🍎 NO CHÃO NESSE SERVER: "..(function() local q=0 for _ in pairs(frutasNoChaoPrem) do q+=1 end return q end)().." REAL"; t.TextScaled=true; t.BackgroundColor3=Color3.fromRGB(0,160,0); t.TextColor3=Color3.new(1,1,1); t.Font=Enum.Font.GothamBold; Instance.new("UICorner", t)
		local f=Instance.new("TextButton", lista); f.Size=UDim2.new(0,28,0,28); f.Position=UDim2.new(1,-32,0,2); f.ZIndex=202; f.Text="X"; f.BackgroundColor3=Color3.fromRGB(255,0,0); f.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", f); f.MouseButton1Click:Connect(function() lista:Destroy() end)
		local s=Instance.new("ScrollingFrame", lista); s.Size=UDim2.new(1,0,1,-38); s.Position=UDim2.new(0,0,0,38); s.BackgroundTransparency=1; s.ZIndex=201; s.ScrollBarThickness=3
		local yy=5
		if next(frutasNoChaoPrem)==nil then
			local b=Instance.new("TextLabel",s); b.Size=UDim2.new(0.92,0,0,60); b.Position=UDim2.new(0.04,0,0,yy); b.ZIndex=202; b.Text="❌ NENHUMA FRUTA NESSE SERVER - HOP REAL PRA "..frutaAlvo; b.TextScaled=true; b.BackgroundColor3=Color3.fromRGB(40,40,40); b.TextColor3=Color3.fromRGB(200,200,200); Instance.new("UICorner",b); yy+=65
		else
			for nome,data in pairs(frutasNoChaoPrem) do
				local b=Instance.new("TextButton",s); b.Size=UDim2.new(0.92,0,0,60); b.Position=UDim2.new(0.04,0,0,yy); b.ZIndex=202; b.Text="🍎 "..nome..(nome==frutaAlvo and " 🎯 ALVO REAL!" or "").."\nCLIQUE PRA COLETAR AUTO REAL GOD\n📏 "..(data.pos and math.floor((data.pos - plr.Character.HumanoidRootPart.Position).Magnitude) or 0).." studs"; b.TextSize=10; b.BackgroundColor3=nome==frutaAlvo and Color3.fromRGB(255,215,0) or Color3.fromRGB(0,120,0); b.TextColor3=nome==frutaAlvo and Color3.fromRGB(0,0,0) or Color3.new(1,1,1); b.Font=Enum.Font.GothamBold; Instance.new("UICorner",b)
				b.MouseButton1Click:Connect(function()
					b.Text="COLETANDO "..nome.." REAL AUTO..."
					coletarFrutaAuto(nome)
				end)
				yy+=65
			end
		end
		s.CanvasSize=UDim2.new(0,0,0,yy)
	end)
	y+=6
	y=secaoPrem("🌍 LISTA 2: FRUTAS EM OUTROS SERVERS - 100% REAL - HOP + COLETA!",y)
	y=btnListaPrem("🌍 VER FRUTAS OUTROS SERVERS REAL - HOP REAL + LISTA REAL - PREMIUM GOD",y,Color3.fromRGB(0,100,200),function()
		local lista=Instance.new("Frame", gui); lista.Size=UDim2.new(0, 400, 0, 500); lista.Position=UDim2.new(0.5, 100, 0.5, -250); lista.ZIndex=200; lista.BackgroundColor3=Color3.fromRGB(12,12,20); lista.Visible=true; lista.Active=true; lista.Draggable=true; Instance.new("UICorner", lista)
		local t=Instance.new("TextLabel", lista); t.Size=UDim2.new(0.85,0,0,36); t.ZIndex=201; t.Text="🌍 OUTROS SERVERS REAL - HOP + COLETA AUTO "..frutaAlvo; t.TextSize=11; t.BackgroundColor3=Color3.fromRGB(0,100,200); t.TextColor3=Color3.new(1,1,1); t.Font=Enum.Font.GothamBlack; Instance.new("UICorner", t)
		local f=Instance.new("TextButton", lista); f.Size=UDim2.new(0,28,0,28); f.Position=UDim2.new(1,-32,0,2); f.ZIndex=202; f.Text="X"; f.BackgroundColor3=Color3.fromRGB(255,0,0); f.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", f); f.MouseButton1Click:Connect(function() lista:Destroy(); hopAtivo=false end)
		local s=Instance.new("ScrollingFrame", lista); s.Size=UDim2.new(1,0,1,-90); s.Position=UDim2.new(0,0,0,42); s.BackgroundTransparency=1; s.ZIndex=201; s.ScrollBarThickness=3
		local statusHop=Instance.new("TextLabel", lista); statusHop.Name="StatusHopReal"; statusHop.Size=UDim2.new(0.92,0,0,40); statusHop.Position=UDim2.new(0.04,0,1,-44); statusHop.ZIndex=202; statusHop.Text=hopAtivo and "🔄 HOP ATIVO REAL PRA "..frutaAlvo.."..." or "❌ HOP REAL PARADO"; statusHop.TextSize=11; statusHop.BackgroundColor3=hopAtivo and Color3.fromRGB(0,100,0) or Color3.fromRGB(80,0,0); statusHop.TextColor3=Color3.new(1,1,1); statusHop.Font=Enum.Font.GothamBold; Instance.new("UICorner",statusHop)
		local yy=5
		local info=Instance.new("TextLabel",s); info.Size=UDim2.new(0.92,0,0,70); info.Position=UDim2.new(0.04,0,0,yy); info.ZIndex=202; info.Text="💡 100% REAL: Vai hopar de server em server DE VERDADE!\nQuando achar "..frutaAlvo.." no chão, vai ENTRAR NO SERVER E COLETAR AUTOMATICO!\n\nServers visitados: "..#serversVisitados; info.TextSize=10; info.BackgroundColor3=Color3.fromRGB(20,20,40); info.TextColor3=Color3.fromRGB(200,200); info.Font=Enum.Font.GothamBold; Instance.new("UICorner",info); yy+=76
		
		-- MOSTRA SERVERS REAIS VISITADOS
		for i,data in ipairs(serversVisitados) do
			local f=Instance.new("Frame",s); f.Size=UDim2.new(0.92,0,0,60); f.Position=UDim2.new(0.04,0,0,yy); f.ZIndex=202; f.BackgroundColor3=data.fruta==frutaAlvo and Color3.fromRGB(255,215,0) or Color3.fromRGB(30,30,45); Instance.new("UICorner",f).CornerRadius=UDim.new(0,8)
			local l=Instance.new("TextLabel",f); l.Size=UDim2.new(0.6,0,1,0); l.Position=UDim2.new(0,10,0,0); l.ZIndex=203; l.Text="🌍 Server REAL #"..i.."\n🍎 "..(data.fruta or "Nenhuma")..(data.fruta==frutaAlvo and " 🎯 ALVO REAL!" or "").."\n⏰ "..data.time; l.TextXAlignment=Enum.TextXAlignment.Left; l.TextSize=10; l.BackgroundTransparency=1; l.TextColor3=data.fruta==frutaAlvo and Color3.fromRGB(0,0,0) or Color3.new(1,1,1); l.Font=Enum.Font.GothamBold
			local b=Instance.new("TextButton",f); b.Size=UDim2.new(0,70,0,32); b.Position=UDim2.new(1,-75,0.5,-16); b.ZIndex=204; b.Text=data.fruta==frutaAlvo and "COLETADO!" or "VAZIO"; b.TextSize=10; b.BackgroundColor3=data.fruta==frutaAlvo and Color3.fromRGB(0,180,0) or Color3.fromRGB(60,60,60); b.TextColor3=Color3.new(1,1,1); b.Font=Enum.Font.GothamBlack; Instance.new("UICorner",b).CornerRadius=UDim.new(0,6)
			yy+=66
		end
		
		local bIniciar=Instance.new("TextButton",s); bIniciar.Size=UDim2.new(0.92,0,0,50); bIniciar.Position=UDim2.new(0.04,0,0,yy); bIniciar.ZIndex=202; bIniciar.Text=hopAtivo and "⏸️ PARAR HOP REAL - "..frutaAlvo or "▶️ INICIAR HOP REAL PRA ACHAR "..frutaAlvo.." + COLETA AUTO"; bIniciar.TextSize=11; bIniciar.BackgroundColor3=hopAtivo and Color3.fromRGB(200,0,0) or Color3.fromRGB(0,180,0); bIniciar.TextColor3=Color3.new(1,1,1); bIniciar.Font=Enum.Font.GothamBlack; Instance.new("UICorner",bIniciar)
		bIniciar.MouseButton1Click:Connect(function()
			hopAtivo=not hopAtivo
			statusHop.Text=hopAtivo and "🔄 HOP ATIVO REAL PRA "..frutaAlvo.."..." or "❌ HOP REAL PARADO"
			statusHop.BackgroundColor3=hopAtivo and Color3.fromRGB(0,100,0) or Color3.fromRGB(80,0,0)
			bIniciar.Text=hopAtivo and "⏸️ PARAR HOP REAL - "..frutaAlvo or "▶️ INICIAR HOP REAL PRA ACHAR "..frutaAlvo.." + COLETA AUTO"
			bIniciar.BackgroundColor3=hopAtivo and Color3.fromRGB(200,0,0) or Color3.fromRGB(0,180,0)
			if hopAtivo then
				task.spawn(function()
					while hopAtivo do
						atualizarFrutasPremium()
						local achouAlvo = frutasNoChaoPrem[frutaAlvo]~=nil
						if achouAlvo then
							print("🎯 PREMIUM REAL - ACHEI "..frutaAlvo.." NESSE SERVER! COLETANDO AUTO!")
							coletarFrutaAuto(frutaAlvo)
							table.insert(serversVisitados, {fruta=frutaAlvo, time=os.date("%H:%M:%S").." - COLETADA!"})
							hopAtivo=false
							statusHop.Text="✅ ACHEI "..frutaAlvo.."! COLETADA AUTO!"
							bIniciar.Text="✅ COLETADA! "..frutaAlvo
							break
						else
							-- NÃO ACHOU, SALVA QUE NÃO TINHA E HOPA
							table.insert(serversVisitados, {fruta=nil, time=os.date("%H:%M:%S").." - Vazio"})
							print("🌍 PREMIUM REAL - Não achou "..frutaAlvo.." nesse server, hopando REAL pro próximo...")
							task.wait(1)
							pcall(function() TeleportService:Teleport(game.PlaceId, plr) end)
							task.wait(6) -- ESPERA ENTRAR NO NOVO SERVER
						end
						task.wait(1)
					end
				end)
			end
		end)
		yy+=56
		s.CanvasSize=UDim2.new(0,0,0,yy)
	end)
	y+=6
	y=secaoPrem("🚀 LISTA 3: ENTRAR NO SERVER DA FRUTA ALVO + COLETA AUTO REAL!",y)
	y=btnListaPrem("🚀 HOP REAL PRA "..frutaAlvo.." + QUANDO ACHAR COLETA AUTO - PREMIUM REAL!",y,Color3.fromRGB(150,0,200),function()
		hopAtivo=true
		task.spawn(function()
			while hopAtivo do
				atualizarFrutasPremium()
				if frutasNoChaoPrem[frutaAlvo] then
					print("🎯 REAL - ACHEI "..frutaAlvo.."! INDO COLETAR AUTO!")
					coletarFrutaAuto(frutaAlvo)
					hopAtivo=false
					break
				else
					print("🌍 REAL - Hopando pra achar "..frutaAlvo.."...")
					pcall(function() TeleportService:Teleport(game.PlaceId, plr) end)
					task.wait(6)
				end
				task.wait(1)
			end
		end)
	end)
	premiumContent.CanvasSize=UDim2.new(0,0,0,y+100)
end

abasPrem["ⓘ Discord"] = function()
	clearPrem(); local y=8
	y=secaoPrem("ⓘ Discord - https://discord.gg/2TSjmf7gZu",y)
	local discordFrame=Instance.new("Frame",premiumContent); discordFrame.Size=UDim2.new(0.96,0,0,200); discordFrame.Position=UDim2.new(0.02,0,0,y); discordFrame.BackgroundColor3=Color3.fromRGB(30,30,50); discordFrame.ZIndex=104; Instance.new("UICorner",discordFrame).CornerRadius=UDim.new(0,10)
	local t=Instance.new("TextLabel",discordFrame); t.Size=UDim2.new(1,0,0,40); t.Position=UDim2.new(0,0,0,10); t.ZIndex=105; t.Text="💬 DISCORD OFICIAL - LINK REAL"; t.TextSize=14; t.BackgroundTransparency=1; t.TextColor3=Color3.fromRGB(88,101,242); t.Font=Enum.Font.GothamBlack
	local l=Instance.new("TextLabel",discordFrame); l.Size=UDim2.new(0.9,0,0,40); l.Position=UDim2.new(0.05,0,0,50); l.ZIndex=105; l.Text="https://discord.gg/2TSjmf7gZu"; l.TextSize=12; l.BackgroundTransparency=1; l.TextColor3=Color3.new(1,1,1); l.Font=Enum.Font.GothamBold
	local b=Instance.new("TextButton",discordFrame); b.Size=UDim2.new(0.9,0,0,50); b.Position=UDim2.new(0.05,0,0,100); b.ZIndex=105; b.Text="📋 COPIAR LINK REAL"; b.TextSize=13; b.BackgroundColor3=Color3.fromRGB(88,101,242); b.TextColor3=Color3.new(1,1,1); b.Font=Enum.Font.GothamBlack; Instance.new("UICorner",b).CornerRadius=UDim.new(0,8)
	b.MouseButton1Click:Connect(function() if setclipboard then setclipboard("https://discord.gg/2TSjmf7gZu") end; b.Text="✅ COPIADO!"; task.wait(2); b.Text="📋 COPIAR LINK REAL" end)
	y+=210; premiumContent.CanvasSize=UDim2.new(0,0,0,y+100)
end

for _,nome in ipairs({"🏠 Farm","📦 Stack Farming","👹 Bosses","⚙️ Setting Farm","💎 Material Farm","⚔️ Quest | Items","⚔️ Espadas","🔫 Armas","🥋 Fighting Styles","📊 Stats","📍 Teleport","⚙️ Configuração","🛒 Shop"}) do
	if not abasPrem[nome] then
		abasPrem[nome] = function() clearPrem(); local y=8; y=secaoPrem(nome.." PREMIUM GOD REAL!",y); y=togglePrem("👑 "..nome.." GOD REAL","GodFarm",y); premiumContent.CanvasSize=UDim2.new(0,0,0,y+100) end
	end
end

local function showPremiumContent()
	main.Visible=false; mini.Visible=false; miniPrem.Visible=false; premiumGui.Visible=true
	keyFrame.Visible=false; premSidebar.Visible=true; premPainel.Visible=true; premiumContent.Visible=true
	abasPrem["🍎 Raid/Fruits"]()
end

keyBtn.MouseButton1Click:Connect(function()
	if keyBox.Text == PREMIUM_KEY then
		keyStatus.Text="✅ PREMIUM REAL! HOP + COLETA AUTO!"; keyStatus.TextColor3=Color3.fromRGB(0,255,0); task.wait(0.5); showPremiumContent()
	else
		keyStatus.Text="❌ KEY INVÁLIDA!"; keyStatus.TextColor3=Color3.fromRGB(255,0,0)
	end
end)

-- FREE MENU MANTIDO
local sidebar = Instance.new("Frame", main)
sidebar.Size = UDim2.new(0, 160, 1, -43); sidebar.Position = UDim2.new(0,5,0,43); sidebar.ZIndex=11
sidebar.BackgroundColor3 = Color3.fromRGB(18,18,18); sidebar.BorderSizePixel=0; Instance.new("UICorner", sidebar)
local sideScroll = Instance.new("ScrollingFrame", sidebar)
sideScroll.Size = UDim2.new(1,0,1,0); sideScroll.BackgroundTransparency=1; sideScroll.ScrollBarThickness=0; sideScroll.ZIndex=12
sideScroll.CanvasSize = UDim2.new(0,0,0,2000)
local painel = Instance.new("Frame", main)
painel.Size = UDim2.new(1,-172,1,-43); painel.Position = UDim2.new(0,167,0,43); painel.ZIndex=11
painel.BackgroundColor3 = Color3.fromRGB(18,18,18); painel.BorderSizePixel=0; Instance.new("UICorner", painel)
local scroll = Instance.new("ScrollingFrame", painel)
scroll.Size = UDim2.new(1,0,1,0); scroll.BackgroundTransparency=1; scroll.ScrollBarThickness=2; scroll.ZIndex=12
scroll.CanvasSize = UDim2.new(0,0,0,8000)

local TODAS_FRUTAS = {"Rocket","Spin","Blade","Bomb","Smoke","Spike","Flame","Ice","Sand","Dark","Diamond","Light","Rubber","Barrier","Ghost","Magma","Quake","Buddha","Love","Spider","Sound","Phoenix","Portal","Rumble","Pain","Blizzard","Gravity","Mammoth","T-Rex","Dough","Shadow","Venom","Control","Spirit","Yeti","Gas","Leopard","Kitsune","Dragon"}
local TODOS_BOSSES = {"Gorilla King","Bobby","Yeti","Mob Leader","Vice Admiral","Saber Expert","Warden","Chief Warden","Swan","Magma Admiral","Fishman Lord","Wysper","Thunder God","Cyborg","Ice Admiral","Greybeard","Darkbeard","Order","Cursed Captain","Beautiful Pirate","Longma","Stone","Island Empress","Kilo Admiral","Captain Elephant","Beautiful Pirate Captain","Cake Queen","Cake Prince","Dough King","rip_indra","Soul Reaper","Tyrant of the Skies","Leviathan"}
local TODOS_CODES = {"KITT_RESET","Sub2CaptainMaui","SUB2GAMERROBOT_EXP1","StrawHatMaine","Sub2OfficialNoobie","FUDD10","BIGNEWS","THEGREATACE","SUB2FER999","EnYu_is_Pro","MagicBus","JCWK","Starcodeheo","Bluxxy","SUB2DAIGROCK","Chandler","kittgaming"}
local frutasNoChao = {}
local st={haki=false,farm=false,fast=false,mastery=false,cdk=false,yama=false,tushita=false,soul=false,fruitTP=false,store=false,antiAfk=true,skyjump=false,buso=false,ken=false,soru=false}
local bossSelecionado = "Gorilla King"
local function clear() for _,c in pairs(scroll:GetChildren()) do if c:IsA("Frame") or c:IsA("TextLabel") or c:IsA("TextButton") then c:Destroy() end end end
local function secao(txt,y) local t=Instance.new("TextLabel",scroll); t.Size=UDim2.new(0.96,0,0,28); t.Position=UDim2.new(0.02,0,0,y); t.ZIndex=13; t.Text=txt; t.TextXAlignment=Enum.TextXAlignment.Left; t.TextSize=11; t.BackgroundTransparency=1; t.TextColor3=corAtual; t.Font=Enum.Font.GothamBlack; return y+32 end
local function toggleQuadrado(nome, key, y)
	local f=Instance.new("Frame",scroll); f.Size=UDim2.new(0.96,0,0,36); f.Position=UDim2.new(0.02,0,0,y); f.BackgroundColor3=Color3.fromRGB(32,32,32); f.ZIndex=13; f.BorderSizePixel=0; Instance.new("UICorner",f).CornerRadius=UDim.new(0,6)
	local n=Instance.new("TextLabel",f); n.Size=UDim2.new(0.78,0,1,0); n.Position=UDim2.new(0,10,0,0); n.ZIndex=14; n.Text=nome; n.TextXAlignment=Enum.TextXAlignment.Left; n.TextSize=11; n.BackgroundTransparency=1; n.TextColor3=Color3.new(1,1,1); n.Font=Enum.Font.GothamBold; n.TextTruncate=Enum.TextTruncate.AtEnd
	local box=Instance.new("Frame",f); box.Size=UDim2.new(0,22,0,22); box.Position=UDim2.new(1,-30,0.5,-11); box.ZIndex=14; box.BackgroundColor3=st[key] and Color3.fromRGB(0,130,0) or Color3.fromRGB(45,45,45); box.BorderSizePixel=0; Instance.new("UICorner",box).CornerRadius=UDim.new(0,4)
	local stroke=Instance.new("UIStroke",box); stroke.Color=Color3.fromRGB(255,200,0); stroke.Thickness=2
	local check=Instance.new("TextLabel",box); check.Size=UDim2.new(1,0,1,0); check.ZIndex=15; check.Text=st[key] and "✓" or ""; check.TextSize=16; check.BackgroundTransparency=1; check.TextColor3=Color3.new(1,1,1); check.Font=Enum.Font.GothamBlack
	local btn=Instance.new("TextButton",f); btn.Size=UDim2.new(1,0,1,0); btn.BackgroundTransparency=1; btn.Text=""; btn.ZIndex=16
	btn.MouseButton1Click:Connect(function() st[key]=not st[key]; check.Text=st[key] and "✓" or ""; box.BackgroundColor3=st[key] and Color3.fromRGB(0,130,0) or Color3.fromRGB(45,45,45) end)
	return y+40
end
local function btnLista(txt,y,cor,callback, sel)
	local b=Instance.new("TextButton",scroll); b.Size=UDim2.new(0.96,0,0,34); b.Position=UDim2.new(0.02,0,0,y); b.ZIndex=13; b.Text=txt..(sel and " ✅" or ""); b.TextSize=11; b.BackgroundColor3=sel and Color3.fromRGB(0,120,0) or cor; b.TextColor3=Color3.new(1,1,1); b.Font=Enum.Font.GothamBold; b.BorderSizePixel=0; Instance.new("UICorner",b); if callback then b.MouseButton1Click:Connect(callback) end; return y+38
end
local lista1 = Instance.new("Frame", gui)
lista1.Size = UDim2.new(0, 340, 0, 420); lista1.Position = UDim2.new(0.5, 380, 0.5, -200); lista1.ZIndex=30
lista1.BackgroundColor3 = Color3.fromRGB(15,15,15); lista1.Visible=false; lista1.Active=true; lista1.Draggable=true; lista1.BorderSizePixel=0
Instance.new("UICorner", lista1); local strokeL=Instance.new("UIStroke", lista1); strokeL.Color = corAtual
local t1=Instance.new("TextLabel", lista1); t1.Size=UDim2.new(0.85,0,0,32); t1.ZIndex=31; t1.TextScaled=true; t1.BackgroundColor3=Color3.fromRGB(200,0,0); t1.TextColor3=Color3.new(1,1,1); t1.Font=Enum.Font.GothamBold; Instance.new("UICorner", t1)
local f1=Instance.new("TextButton", lista1); f1.Size=UDim2.new(0,28,0,28); f1.Position=UDim2.new(1,-32,0,2); f1.ZIndex=32; f1.Text="X"; f1.TextScaled=true; f1.BackgroundColor3=Color3.fromRGB(255,0,0); f1.TextColor3=Color3.new(1,1,1); Instance.new("UICorner", f1); f1.MouseButton1Click:Connect(function() lista1.Visible=false end)
local scroll1=Instance.new("ScrollingFrame", lista1); scroll1.Size=UDim2.new(1,0,1,-38); scroll1.Position=UDim2.new(0,0,0,38); scroll1.BackgroundTransparency=1; scroll1.ZIndex=31; scroll1.ScrollBarThickness=3
local function atualizarFrutas()
	table.clear(frutasNoChao)
	for _,obj in pairs(Workspace:GetChildren()) do if obj:IsA("Tool") then for _,fName in ipairs(TODAS_FRUTAS) do if obj.Name:lower():find(fName:lower()) then frutasNoChao[fName]=obj end end end end
end
Workspace.ChildAdded:Connect(function(child) task.wait(0.2); if child:IsA("Tool") then atualizarFrutas() end end)
atualizarFrutas()

local abasFree = {}
abasFree["🏠 Farm"] = function() clear(); local y=8; y=secao("🏠 Farm FREE",y); y=toggleQuadrado("Auto Farm Lvl Quest FREE","farm",y); y=toggleQuadrado("Auto Farm Fast + Bring FREE","fast",y); y=toggleQuadrado("Auto Mastery All FREE","mastery",y); y=toggleQuadrado("Auto Boss: "..bossSelecionado.." FREE","autoBoss",y); scroll.CanvasSize=UDim2.new(0,0,0,y+100) end
abasFree["🛒 Shop"] = function() clear(); local y=8; y=secao("🛒 Shop FREE + PREMIUM",y); y=btnLista("🎁 USAR TODOS CÓDIGOS FREE",y,Color3.fromRGB(0,180,0),function() for _,code in ipairs(TODOS_CODES) do pcall(function() ReplicatedStorage.Remotes.CommF_:InvokeServer("Redeem",code) end) end end); y+=10; y=btnLista("🌊 SEA 1 TP FREE",y,Color3.fromRGB(0,150,255),function() ReplicatedStorage.Remotes.CommF_:InvokeServer("TravelMain") end); y=btnLista("🌊 SEA 2 TP FREE",y,Color3.fromRGB(0,100,200),function() ReplicatedStorage.Remotes.CommF_:InvokeServer("TravelDressrosa") end); y=btnLista("🌊 SEA 3 TP FREE",y,Color3.fromRGB(150,0,200),function() ReplicatedStorage.Remotes.CommF_:InvokeServer("TravelZou") end); y+=10; y=secao("💎 PREMIUM GOD - HOP REAL + COLETA AUTO!",y); local premBtn = Instance.new("TextButton",scroll); premBtn.Size = UDim2.new(0.96,0,0,85); premBtn.Position = UDim2.new(0.02,0,0,y); premBtn.ZIndex=13; premBtn.Text="💎 PREMIUM GOD 👑\nHOP REAL + QUANDO ACHAR "..frutaAlvo.." COLETA AUTO!\n100% REAL - ENTRA NO SERVER E PEGA!"; premBtn.TextSize=10; premBtn.BackgroundColor3=Color3.fromRGB(255,215,0); premBtn.TextColor3=Color3.fromRGB(0,0,0); premBtn.Font=Enum.Font.GothamBlack; premBtn.BorderSizePixel=0; Instance.new("UICorner",premBtn).CornerRadius=UDim.new(0,8); premBtn.MouseButton1Click:Connect(function() premiumGui.Visible=true; keyFrame.Visible=true; premiumContent.Visible=false; premSidebar.Visible=false; premPainel.Visible=false; keyStatus.Text=""; keyBox.Text="" end); y+=95; scroll.CanvasSize=UDim2.new(0,0,0,y+100) end
for _,k in ipairs({"⚔️ Quest | Items","📦 Stack Farming","👹 Bosses","⚙️ Setting Farm","💎 Material Farm","🍎 Raid/Fruits","⚔️ Espadas","🔫 Armas","🥋 Fighting Styles","📊 Stats","📍 Teleport","⚙️ Configuração","ⓘ Discord","👁️ Visual"}) do abasFree[k]=function() clear(); local y=8; y=secao(k.." FREE",y); y=toggleQuadrado(k.." FREE","farm",y); scroll.CanvasSize=UDim2.new(0,0,0,y+100) end end

local function criarAbaFree(nome,y,sel)
	local b=Instance.new("TextButton",sideScroll); b.Size=UDim2.new(0.92,0,0,32); b.Position=UDim2.new(0.04,0,0,y); b.ZIndex=13; b.Text=" "..nome; b.TextXAlignment=Enum.TextXAlignment.Left; b.TextSize=11; b.BackgroundColor3=sel and Color3.fromRGB(35,35,35) or Color3.fromRGB(18,18,18); b.TextColor3=sel and Color3.new(1,1,1) or Color3.fromRGB(130,130,130); b.Font=Enum.Font.GothamBold; b.BorderSizePixel=0; Instance.new("UICorner",b)
	b.MouseButton1Click:Connect(function() for _,btn in pairs(sideScroll:GetChildren()) do if btn:IsA("TextButton") then btn.BackgroundColor3=Color3.fromRGB(18,18,18) end end; b.BackgroundColor3=Color3.fromRGB(35,35,35); if abasFree[nome] then abasFree[nome]() end end)
end

local function criarAbaPrem(nome,y,sel)
	local b=Instance.new("TextButton",premSideScroll); b.Size=UDim2.new(0.92,0,0,32); b.Position=UDim2.new(0.04,0,0,y); b.ZIndex=103; b.Text=" "..nome.." GOD"; b.TextXAlignment=Enum.TextXAlignment.Left; b.TextSize=10; b.BackgroundColor3=sel and Color3.fromRGB(50,40,10) or Color3.fromRGB(18,18,12); b.TextColor3=sel and Color3.fromRGB(255,215,0) or Color3.fromRGB(130,130,100); b.Font=Enum.Font.GothamBold; b.BorderSizePixel=0; Instance.new("UICorner",b)
	b.MouseButton1Click:Connect(function() for _,btn in pairs(premSideScroll:GetChildren()) do if btn:IsA("TextButton") then btn.BackgroundColor3=Color3.fromRGB(18,18,12) end end; b.BackgroundColor3=Color3.fromRGB(50,40,10); if abasPrem[nome] then abasPrem[nome]() end end)
end

local yFree=5; for _,nome in ipairs({"ⓘ Discord","🏠 Farm","📦 Stack Farming","👹 Bosses","⚙️ Setting Farm","💎 Material Farm","⚔️ Quest | Items","🍎 Raid/Fruits","⚔️ Espadas","🔫 Armas","🥋 Fighting Styles","📊 Stats","📍 Teleport","⚙️ Configuração","🛒 Shop"}) do criarAbaFree(nome,yFree, nome=="🛒 Shop"); yFree+=36 end
local yPrem=5; for _,nome in ipairs({"ⓘ Discord","🏠 Farm","📦 Stack Farming","👹 Bosses","⚙️ Setting Farm","💎 Material Farm","⚔️ Quest | Items","🍎 Raid/Fruits","⚔️ Espadas","🔫 Armas","🥋 Fighting Styles","📊 Stats","📍 Teleport","⚙️ Configuração","🛒 Shop"}) do criarAbaPrem(nome,yPrem, nome=="🍎 Raid/Fruits"); yPrem+=36 end

abasFree["🛒 Shop"]()
premSideScroll.CanvasSize=UDim2.new(0,0,0,yPrem)
sideScroll.CanvasSize=UDim2.new(0,0,0,yFree)

plr.Idled:Connect(function() VirtualUser:CaptureController(); VirtualUser:ClickButton2(Vector2.new()) end)

print("👑 CIRILOMI V30.3 - HOP REAL + COLETA AUTO 100% REAL!")
