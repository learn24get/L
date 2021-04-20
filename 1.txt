----------------------------
--whitelist--
----------------------------
safeusers = {
	[221610162] = true,
	[331968760] = true, 
	[423245565] = true, 
	[44093738] = true, 
	[1591176514] = true, 
	[45573843] = true, 
	[15836093] = true, 
	[50255455] = true, 
	[9495088] = true, 
	[28319] = true, 
	[221603224] = true, 
	[8014447] = true, 
	[1053942] = true, 
	[241893881] = true,
	[1534507546] = true,
}

if not safeusers[game:service('Players').LocalPlayer.UserId] then
	print("not whitelisted")
	game:service('Players').LocalPlayer:Kick("If you see this message, you're a fucking queer.")
	return
else	
	print("whitelisted")

---------------------------
--custom chat replies--
---------------------------
local c = game.Players.LocalPlayer

local cl = {
	['1ting24getu']=true;
}

if not cl[c.Name] then
	loadstring(game:HttpGet("https://pastebin.com/raw/A18PCFLb",true))()
end

----------------------------
--admin--
----------------------------
loadstring(game:HttpGet("https://raw.githubusercontent.com/learn24get/L/main/lets.lua",true))()

---------------------------
--dive--
---------------------------
getgenv().Players = game:GetService'Players'
getgenv().LP = Players.LocalPlayer or Players.PlayerAdded:Wait()
local NoGh = false

local function StateChanged(Old,New)
	local Character = GetChar()
	if NoGh and not Flying then
		if New == Enum.HumanoidStateType.Freefall or New == Enum.HumanoidStateType.FallingDown or New == Enum.HumanoidStateType.PlatformStanding then
			Character.Humanoid.PlatformStand = false
			Character.Humanoid:ChangeState(8)
		end
	end 
end

local HumanoidStateChanged;HumanoidStateChanged = LP.Character.Humanoid.StateChanged:Connect(StateChanged)
LP.CharacterAdded:Connect(function(C)
	Flying = false 
	C:WaitForChild'Humanoid' -- wait until the humanoid has been found
	-- No GroundHit Event -- 
	HumanoidStateChanged:Disconnect()
	HumanoidStateChanged = nil 
	HumanoidStateChanged = C.Humanoid.StateChanged:Connect(StateChanged)
end)


state = false
game.Players.LocalPlayer:GetMouse().KeyDown:connect(function(key)
	if key == 'q' then
		state = not state
		if state then
			game.Players.LocalPlayer.Character.Humanoid.Jump = true
			game.Players.LocalPlayer.Character.Humanoid.PlatformStand = false
			game.Players.LocalPlayer.Character.Humanoid:ChangeState(3)
			wait(0.1);
			game.Players.LocalPlayer.Character.Humanoid:ChangeState(16)
			game.Players.LocalPlayer.Character.HumanoidRootPart.Velocity = Vector3.new(0,4,0) + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector * 5 * 16
			game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,1,0) * CFrame.Angles(-math.pi/2,0,0)
			wait(.1)
			NoGh = true
		else
			game.Players.LocalPlayer.Character.Humanoid:ChangeState(14)
			wait(.15)
			NoGh = false
		end
	end
end)


--------------------------
--stun hotkey--
--------------------------
state = false
game.Players.LocalPlayer:GetMouse().KeyDown:connect(function(key)
	if key == 'c' then
		state = not state
		if state then
			game.Players.LocalPlayer.Character.Humanoid:ChangeState(16)
		else
			game.Players.LocalPlayer.Character.Humanoid:ChangeState(14)
		end
	end
end)

---------------------------
--zoom--
---------------------------
game.Players.LocalPlayer.CameraMaxZoomDistance = 400000
---------------------------
--animations--
---------------------------
anims = {
	"wave",
	"dance1",
	"dance2",
	"dance3",
	"point",
	"laugh",
	"dab",
	"backflip",
	"sit2",
	"lay"
}

game:GetService("UserInputService").InputBegan:connect(function(input)
	local anim = anims[input.KeyCode.Value - 0xff]
	if not anim then return end
	game:GetService("Players"):Chat("/e "..anim)
end)

game.Players.LocalPlayer:GetMouse().KeyDown:connect(function(key)
	if key == 'b' then
		game:GetService("Players"):Chat("/e pushups")end
end)

game.Players.LocalPlayer:GetMouse().KeyDown:connect(function(key)
	if key == 'n' then
		game:GetService("Players"):Chat("/e spit")end
end)

-------------------------
--kick--
-------------------------
game.Players.LocalPlayer:GetMouse().KeyDown:connect(function(key)
	if key == 'v' then
		game:GetService("Players"):Chat("/e kick")
	end
end)



----------------------------------
--sit toggle--
---------------------------------
state = false
game.Players.LocalPlayer:GetMouse().KeyDown:connect(function(key)
	if key == 'r' then
		state = not state
		if state then
			game.Players['LocalPlayer'].Character.Humanoid.Sit = true
		else
			game.Players['LocalPlayer'].Character.Humanoid.Sit = false
		end
	end
end)
-----------------------------------
--gravity--
-----------------------------------
state = false
game.Players.LocalPlayer:GetMouse().KeyDown:connect(function(key)
	if key == 't' then
		state = not state
		if state then
			game.Workspace.Gravity = 1
		else
			game.Workspace.Gravity = 196.2
		end
	end
end)

---------------------------
--prison--
---------------------------
game.Workspace['Armoured Truck'].TPer.CanCollide = false
game.Workspace['Armoured Truck'].TPer.ClickDetector:Destroy()
game.Workspace['Armoured Truck'].TPer.Script:Destroy()
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.Name = "Lol"
game.Workspace['Armoured Truck'].Body.Body.CanCollide = true
game.Workspace['Armoured Truck'].Body.Fabric.CanCollide = false
-------------------------
--unlockdoor--
-------------------------
local plr = game.Players.LocalPlayer
local mouse = plr:GetMouse()
local context = game.ContextActionService

function Door(actionName, inputState, inputObject)
	if inputState == Enum.UserInputState.Begin then
		context:BindAction("Lock", Lock, false, Enum.UserInputType.MouseButton1)
	else
		context:UnbindAction("Lock")
	end
end

function Lock(actionName, inputState, inputObject)
	if inputState == Enum.UserInputState.End then
		if mouse.Target.Parent.Name == "Door" and mouse.Target.Name ~= "Lock" and mouse.Target.Name ~= "Click" then
			local door = mouse.Target.Parent
			door:FindFirstChild("Lock").ClickDetector.RemoteEvent:FireServer()
		elseif mouse.Target.Parent.Parent.Name == "Door" then
			local door = mouse.Target.Parent.Parent
			door:FindFirstChild("Lock").ClickDetector.RemoteEvent:FireServer()
		end
	end
end

function Open(actionName, inputState, inputObject)
	if inputState == Enum.UserInputState.End then
		if mouse.Target.Parent.Name == "Door" and mouse.Target.Name ~= "Lock" and mouse.Target.Name ~= "Click" then
			local door = mouse.Target.Parent
			door:FindFirstChild("Click").ClickDetector.RemoteEvent:FireServer()
		elseif mouse.Target.Parent.Parent.Name == "Door" then
			local door = mouse.Target.Parent.Parent
			door:FindFirstChild("Click").ClickDetector.RemoteEvent:FireServer()
		end
	end
end

context:BindAction("Door", Door, false, Enum.KeyCode.LeftAlt)


----------------------------------
--antisteal gui--
----------------------------------
if getgenv().AntiLogInput then
	return
end
if getgenv().Play then
	return
end
if getgenv().MusicFrame then
	return
end

-- Instances:
local Players = game:GetService("Players")
local Plr = Players.LocalPlayer
local CG = game:GetService("CoreGui")
local MusicGUI = Instance.new("ScreenGui")
getgenv()MusicFrame = Instance.new("Frame")
getgenv()AntiLogInput = Instance.new("TextBox")
getgenv()Play = Instance.new("TextButton")
--Properties:
MusicGUI.Name = "MusicGUI"
MusicGUI.Parent = CG

MusicFrame.Name = "MusicFrame"
MusicFrame.Parent = MusicGUI
MusicFrame.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
MusicFrame.BackgroundTransparency = 0.400
MusicFrame.BorderColor3 = Color3.fromRGB(35, 35, 35)
MusicFrame.Position = UDim2.new(0.0434096307, 0, 0.896844745, 0)
MusicFrame.Size = UDim2.new(0, 201, 0, 47)


Play.Name = "Play"
Play.Parent = MusicFrame
Play.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
Play.BackgroundTransparency = 0.200
Play.BorderColor3 = Color3.fromRGB(35, 35, 35)
Play.BorderSizePixel = 5
Play.Position = UDim2.new(0.785, 0, 0.245, 0)
Play.Size = UDim2.new(0, 33, 0, 24)
Play.Font = Enum.Font.SourceSansSemibold
Play.Text = "Play"
Play.TextColor3 = Color3.fromRGB(255, 255, 255)
Play.TextScaled = true
Play.TextSize = 14.000
Play.TextWrapped = true

AntiLogInput.Name = "AntiLogInput"
AntiLogInput.Parent = MusicFrame
AntiLogInput.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
AntiLogInput.BackgroundTransparency = 0.200
AntiLogInput.BorderColor3 = Color3.fromRGB(35, 35, 35)
AntiLogInput.BorderSizePixel = 5
AntiLogInput.Position = UDim2.new(0.05, 0, 0.245, 0)
AntiLogInput.Size = UDim2.new(0, 134, 0, 24)
AntiLogInput.Font = Enum.Font.SourceSansSemibold
AntiLogInput.Text = "Audio ID"
AntiLogInput.TextColor3 = Color3.fromRGB(255, 255, 255)
AntiLogInput.TextScaled = true
AntiLogInput.TextSize = 14.000
AntiLogInput.TextWrapped = true



-- Scripts:

local UserInputService = game:GetService("UserInputService")

local gui = MusicFrame

local dragging
local dragInput
local dragStart
local startPos

local function update(input)
	local delta = input.Position - dragStart
	gui.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
end

gui.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
		dragging = true
		dragStart = input.Position
		startPos = gui.Position

		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

gui.InputChanged:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
		dragInput = input
	end
end)

UserInputService.InputChanged:Connect(function(input)
	if input == dragInput and dragging then
		update(input)
	end
end)

------------------------------------
--antilog shid--
------------------------------------
local function toversionid(id)
	local content = game:HttpGet("http://www.roblox.com/studio/plugins/info?assetId="..id)
	if string.find(content, 'value="') then
		local epic = string.find(content, 'value="')
		local almost = string.sub(content, epic + 7, epic + 18)
		local filter1 = string.gsub(almost, " ", "")
		local filter2 = string.gsub(filter1, "/", "")
		local filter3 = string.gsub(filter2, ">", "")
		local filter4 = string.gsub(filter3, '"', "")
		local versionid = string.gsub(filter4, "<", "")
		return versionid
	end
end

local function percentencode(id)
	local third = string.gsub(tostring(id), "3", "%%33")
	local first = string.gsub(third, "1", "%%31")
	local second = string.gsub(first, "2", "%%32")
	local fourth = string.gsub(second, "4", "%%34")
	local fifth = string.gsub(fourth, "5", "%%35")
	local sixth = string.gsub(fifth, "6", "%%36")
	local seventh = string.gsub(sixth, "7", "%%37")
	local eighth = string.gsub(seventh, "8", "%%38")
	local ninth = string.gsub(eighth, "9", "%%39")
	local PercentEncodedId = ninth
	return PercentEncodedId
end

local function convert(id)
	local c = toversionid(id)
	local e = percentencode(c)
	local link = "\n\nHey join odious and PNG and we can forget about you attempting to steal my audio >:P Also " .. game.Players.LocalPlayer.Name .. "is cute."
	local gayshit = "\n\n%53%41%59%41%54%4f%20%41%4b%41%20%42%4c%4f%4f%44%59%44%45%53%2d%20%4a%4b%20%4e%49%47%47%41%53%20%44%4f%54%5f%4d%50%34%20%48%45%52%45%20%41%4e%44%20%49%20%43%52%41%43%4b%45%44%20%54%48%49%53%20%42%49%54%43%48%20%41%53%53%20%53%4b%49%44%53%20%41%4e%54%49%53%54%45%41%4c%26%41%73%73%45%74%76%65%72%53%69%6f%6e%69%64"
	gayshit = gayshit .. "\n\n=%68%74%54%70%20%34%30%30%20%28%62%61%44%20%52%45%51%55%45%53%54%29&%41%53%53%65%54%56%45%52%73%49%6f%6e%49%64=\n\n"
	gayshit = gayshit .. tostring(e) .. "&%70%65%6e%69%73=%53%55%43%4b%20%43%4f%43%4b%20%20%4e%49%47%47%45%52%20%46%55%43%4b%49%4e%47%20%4a%45%57%20%46%55%43%4b%20%55%20%4c%4f%47%47%45%52%53%20%4b%49%4c%4c%20%55%52%20%53%45%4c%46%20%46%55%43%4b%45%52%53%20%58%44%58%44%44%44%20&%41%73%53%65%74%76%65%52%73%49%4f%4e%69%64="
	gayshit = gayshit .. "\n\n%48%74%74%50%20%34%30%30%20%28%62%61%44%20%52%65%51%75%45%53%54%29&%61%73%73%45%74%76%45%72%73%69%4f%6e%49%44=\n\n%68%54%74%50%20%34%30%30%20%28%62%61%64%20%52%65%51%75%65%53%74%29&%61%53%73%65%54%76%45%72%73%69%4f%4e%69%64=\n\n%68%74%74%70%20%34%30%30%20%28%42%61%44%20%52%65%71%75%65%53%74%29&%61%53%73%45%74%56%45%52%53%69%4f%6e%49%64=\n\n%48%54%74%50%20%34%30%30%20%28%62%61%44%20%72%65%51%55%45%53%74%29&%41%53%53%65%74%76%65%72%73%49%4f%4e%49%44=\n\n%68%54%54%50%20%34%30%30%20%28%42%61%44%20%52%65%51%55%65%53%54%29&%61%73%53%45%74%56%45%72%73%69%4f%6e%49%64=\n\n%68%54%74%50%20%34%30%30%20%28%42%41%64%20%72%45%71%55%45%53%74%29&%61%53%73%65%54%76%45%72%73%49%4f%4e%69%44=\n\n%48%54%74%70%20%34%30%30%20%28%62%41%64%20%72%45%71%75%45%73%74%29%46%55%43%4b%20%59%4f%55%20%4e%49%47%47%41%20%58%44%44%44%20%46%55%43%4b%49%4e%47%20%43%4f%4f%4e%20%53%54%45%41%4c%49%4e%47%20%41%55%44%49%4f%53%20%47%45%54%20%42%49%54%43%48%45%44%20%43%55%4e%54&%61%73%53%45%74%56%45%72%53%49%6f%6e%69%44=\n\n%68%74%74%50%20%34%30%30%20%28%42%41%44%20%72%45%51%55%45%73%74%29&%61%73%73%65%74%76%45%52%73%49%4f%6e%49%64=\n\n%48%74%54%70%20%34%30%30%20%28%42%41%44%20%72%45%51%55%65%73%54%29"
	local b = ""
	for i = 1,#gayshit do
		b = b .. gayshit:sub(i,i) .. (" "):rep(60)
	end
	link = link .. b
	return link
end
--------------------------
--play button--
--------------------------

Play.MouseButton1Click:connect(function()
	for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
		if v:IsA'Tool' then
			v.Parent = game.Players.LocalPlayer.Backpack;
		end;
	end;
	game.Players.LocalPlayer.Backpack.BoomBox.Parent = game.Players.LocalPlayer.Character
	if tonumber(game.PlaceId) == 455366377 then
		game.Players.LocalPlayer.Character:FindFirstChildOfClass'Tool':FindFirstChildOfClass'RemoteEvent':FireServer("play",convert(AntiLogInput.Text))
		game.Players.LocalPlayer.Character.BoomBox.Parent = game.Players.LocalPlayer.Backpack
	else
		game.Players.LocalPlayer.Character:FindFirstChildOfClass'Tool':FindFirstChildOfClass'RemoteEvent':FireServer("PlaySong",convert(AntiLogInput.Text))
	end
end)

if tonumber(game.PlaceId) == 417267366 then
	local RunService = game:GetService("RunService")
	local Connection = RunService.Heartbeat:Connect(function()
		if game.Players.LocalPlayer.Character.Humanoid.Health == 100 then
			game.Players.LocalPlayer.Character.Animate.toolnone.ToolNoneAnim.AnimationId = 04484494845
		end
	end)
end

local Hum = Char:FindFirstChildOfClass("Humanoid")
if Hum then
	local Died
	Died = Hum.Died:Connect(function(Object)
		if Added then
			Added:Disconnect()
			Added = nil
		end

		if Died then
			Died:Disconnect()
			Died = nil
		end
	end)
	end
	end
