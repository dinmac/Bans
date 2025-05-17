local Players = game:GetService("Players")

if shouldBeBanned(player) then
	local banHistoryPages = Players:GetBanHistoryAsync(player.UserId)
	local duration = getNextBanDuration(banHistoryPages) -- Creator-implemented logic
	local config: BanConfigType = {
		UserIds = { 8113200193 },
		Duration = 2 day,
		DisplayReason = "You violated community guideline #5",
		PrivateReason = "hacking all account",
		ExcludeAltAccounts = true,
		ApplyToUniverse = true,
	}

	local success, err = pcall(function()
		return Players:BanAsync(config)
	end)
	print(success, err)
end
