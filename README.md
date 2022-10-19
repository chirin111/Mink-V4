local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Player = game:GetService("Players").LocalPlayer

local ArgsDash = {
	Character = Player.Character,
	Duration = .25,
	CFrame = Player.Character.HumanoidRootPart.CFrame,
}

local old; old = hookmetamethod(game, "__namecall", newcclosure(function(self, ...)
	if self.Name == "CommE" then
		local args = {...}

		if args[1] == "Dodge" then
			coroutine.wrap(function() require(ReplicatedStorage.Effect.Container.Shared.LightningTP)(ArgsDash) end)()
		end
	end
	
	return old(self, ...)
end))

syn.set_thread_identity(5)

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Player = game:GetService("Players").LocalPlayer

local ArgsTransform = {
	Character = game.Players.LocalPlayer.Character,
	CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame,
	Color1 = Color3.fromRGB(102, 255, 153),
	Color2 = Color3.fromRGB(102, 255, 153),
	Color3 = Color3.fromRGB(102, 255, 153),
}

Player.Character.Humanoid:LoadAnimation(ReplicatedStorage.Util.Anims.Storage["2"].RaceTransform):Play()

delay(1, function()
	pcall(function() require(ReplicatedStorage.Effect.Container.RaceTransformation.Main)(ArgsTransform) end)
end)
