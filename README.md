local espColor = Color3.fromRGB(255, 0, 0)

for _, v in pairs(game.Players:GetPlayers()) do
    if v ~= game.Players.LocalPlayer and v.Character then
        local highlight = Instance.new("Highlight")
        highlight.Adornee = v.Character
        highlight.FillColor = espColor
        highlight.OutlineColor = Color3.new(1,1,1)
        highlight.Parent = v.Character
    end
end
