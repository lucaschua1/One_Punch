local Character
local Hitbox
local Weld
function Setup()
	Character = game.Players.LocalPlayer.Character
	Hitbox = Instance.new("Part")
	Hitbox.Size = Vector3.new(4, 2, 3)
	Hitbox.Transparency = 1
	Hitbox.CanCollide = false
	Hitbox.Anchored = false
	Hitbox.Parent = workspace
	Hitbox.Name = "Hitbox"
	Weld = Instance.new("Weld")
	Weld.Name = "Weld"
	Weld.Parent = Hitbox
	Weld.Part0 = Character:WaitForChild("HumanoidRootPart")
	Weld.Part1 = Hitbox
	Hitbox.Touched:Connect(function()
		--Does nothing, only creates a TouchInterest we need.
	end)
end
Setup()
game.Players.LocalPlayer.CharacterAdded:Connect(function()
	Setup()
end)
game:GetService("UserInputService").InputBegan:Connect(function(Input)
	--who doesn't love redundancy
	if Input.KeyCode == Enum.KeyCode.F and Character and Hitbox and Weld then
		for Index, Value in ipairs(Hitbox:GetTouchingParts()) do
			if Value.Parent then
				if Value.Parent:IsA("Model") then
					if Value.Parent:FindFirstChild("Humanoid") then
						if game.Players:GetPlayerFromCharacter(Value.Parent) then
							if game.Players:GetPlayerFromCharacter(Value.Parent) ~= game.Players.LocalPlayer then
								for Index = 1, 10  do
									game.ReplicatedStorage.meleeEvent:FireServer(game.Players:GetPlayerFromCharacter(Value.Parent))
								end
							end
						end
					end
				end
			end
		end
	end
end)
