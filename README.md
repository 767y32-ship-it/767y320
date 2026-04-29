local Players = game:GetService("Players")

local admins = {
    ["YourNameHere"] = true -- حط اسمك هنا
}

local function isAdmin(player)
    return admins[player.Name] == true
end

Players.PlayerAdded:Connect(function(player)
    player.Chatted:Connect(function(msg)
        if not isAdmin(player) then return end
        
        local args = msg:split(" ")
        local command = args[1]
        
        -- سرعة خارقة
        if command == "!speed" then
            local speed = tonumber(args[2]) or 50
            player.Character.Humanoid.WalkSpeed = speed
        end
        
        -- طيران بسيط
        if command == "!jump" then
            player.Character.Humanoid.JumpPower = 120
        end
        
        -- قتل لاعب
        if command == "!kill" and args[2] then
            local target = Players:FindFirstChild(args[2])
            if target and target.Character then
                target.Character.Humanoid.Health = 0
            end
        end
        
        -- اعطاء فلوس (leaderstats لازم تكون موجودة)
        if command == "!money" and args[2] then
            local amount = tonumber(args[2]) or 100
            player.leaderstats.Cash.Value += amount
        end
        
        -- انتقال
        if command == "!tp" and args[2] then
            local target = Players:FindFirstChild(args[2])
            if target and target.Character then
                player.Character:MoveTo(target.Character:GetPivot().Position)
            end
        end
    end)
end)
