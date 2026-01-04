🧠 1️⃣ Leaderstats (Level System)
game.Players.PlayerAdded:Connect(function(player)
	local leaderstats = Instance.new("Folder")
	leaderstats.Name = "leaderstats"
	leaderstats.Parent = player

	local Level = Instance.new("IntValue")
	Level.Name = "Level"
	Level.Value = 1
	Level.Parent = leaderstats
end)
⚔️ 2️⃣ Killing will increase your level
game.Players.PlayerAdded:Connect(function(player)
	player.CharacterAdded:Connect(function(character)
		local humanoid = character:WaitForChild("Humanoid")

		humanoid.Died:Connect(function()
			local tag = humanoid:FindFirstChild("creator")
			if tag and tag.Value then
				local killer = tag.Value
				if killer:FindFirstChild("leaderstats") then
					killer.leaderstats.Level.Value += 1
				end
			end
		end)
	end)
end)
🏆 3️⃣ Noob ➜ Pro System
local PRO_LEVEL = 10

game.Players.PlayerAdded:Connect(function(player)
	player.CharacterAdded:Connect(function(character)
		local humanoid = character:WaitForChild("Humanoid")
		local level = player.leaderstats.Level

		if level.Value >= PRO_LEVEL then
			humanoid.WalkSpeed = 24
			humanoid.JumpPower = 70
		else
			humanoid.WalkSpeed = 16
			humanoid.JumpPower = 50
		end
	end)
end)
