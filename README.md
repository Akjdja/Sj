local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local replacementAnimations = {
    --block--
    ["10470389827"] = "rbxassetid://16039070113",
    --1--
    ["14374357351"] = "rbxassetid://12467789963",
    --3--
    ["12447247483"] = "rbxassetid://14406991505",
    ["12309835105"] = "rbxassetid://13073745835",
    --counter--
    ["13603396939"] = "rbxassetid://16310343179",
    --ult--
    [""] = "rbxassetid://",
}

local function onAnimationPlayed(animationTrack)
    if player.Character and humanoid then
        local animationId = animationTrack.Animation.AnimationId:match("%d+")
        local replacementId = replacementAnimations[animationId]

        if replacementId then
            animationTrack:Stop()

            local newAnimation = Instance.new("Animation")
            newAnimation.AnimationId = replacementId
            local newTrack = humanoid:LoadAnimation(newAnimation)
            newTrack:Play()
        end
    end
end

humanoid.AnimationPlayed:Connect(onAnimationPlayed)

player.CharacterAdded:Connect(function(newCharacter)
    character = newCharacter
    humanoid = newCharacter:WaitForChild("Humanoid")
    humanoid.AnimationPlayed:Connect(onAnimationPlayed)
end)
--Names--
local player = game.Players.LocalPlayer
local playerGui = player.PlayerGui
local hotbar = playerGui:FindFirstChild("Hotbar")
local backpack = hotbar:FindFirstChild("Backpack")
local hotbarFrame = backpack:FindFirstChild("Hotbar")

-- Button 1
local baseButton1 = hotbarFrame:FindFirstChild("1").Base
local ToolName1 = baseButton1.ToolName
ToolName1.Text = "Energy Combination"

-- Button 2
local baseButton2 = hotbarFrame:FindFirstChild("2").Base
local ToolName2 = baseButton2.ToolName
ToolName2.Text = "Limitless Grip"

-- Button 3
local baseButton3 = hotbarFrame:FindFirstChild("3").Base
local ToolName3 = baseButton3.ToolName
ToolName3.Text = "Crimson Snare"

-- Button 4
local baseButton4 = hotbarFrame:FindFirstChild("4").Base
local ToolName4 = baseButton4.ToolName
ToolName4.Text = "Martial Arts Counter"

local function waitForGui()
    local player = game.Players.LocalPlayer
    local playerGui = player:WaitForChild("PlayerGui")
    
    while true do
        local screenGui = playerGui:FindFirstChild("ScreenGui")
        if screenGui then
            local magicHealthFrame = screenGui:FindFirstChild("MagicHealth")
            if magicHealthFrame then
                local textLabel = magicHealthFrame:FindFirstChild("TextLabel")
                if textLabel then
                    textLabel.Text = "FULL POWER"
                    return
                end
            end
        end
        wait(1)
    end
end

waitForGui()

--Vfx for moves
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")

local replacementAnimations = {
    --1
    ["12273188754"] = "rbxassetid://12273188754",
    ["14374357351"] = "rbxassetid://12467789963",
    --3
    ["Your Id Here"] = "rbxassetid://Here your id",
    ["Your Id Here"] = "rbxassetid://Here your id"
}

local function onAnimationPlayed(animationTrack)
    if player.Character and humanoid then
        local animationId = animationTrack.Animation.AnimationId:match("%d+")
        local replacementId = replacementAnimations[animationId]

        if replacementId then
            animationTrack:Stop()

            local newAnimation = Instance.new("Animation")
            newAnimation.AnimationId = replacementId
            local newTrack = humanoid:LoadAnimation(newAnimation)
            newTrack:Play()
            
            if replacementId == "rbxassetid://12273188754" then
                wait(0.3)
                
                local Test = game:GetService("ReplicatedStorage").Resources.FiveSeasonsFX.CharFX.ArmBurst.Attachment
                local test = Test:Clone()
                test.Parent = character.Hitbox_LeftArm
                
                for _, child in ipairs(test:GetChildren()) do
                    if child:IsA("ParticleEmitter") then
                        child.Color = ColorSequence.new(Color3.new(0, 225, 255))
                        child:Emit(5)
                        child.Enabled = true
                    end
                end
                
                wait(3)
                test:Destroy()
            end
            if replacementId == "rbxassetid://14374357351" then
                wait(1.5)
                
                local Test2 = game:GetService("ReplicatedStorage").Resources.KJEffects.KJWallCombo.FinalImpact.Attachment
                local test2 = Test:Clone()
                test2.Parent = character.Hitbox_LeftArm
                
                for _, child in ipairs(test2:GetChildren()) do
                    if child:IsA("ParticleEmitter") then
                        child.Color = ColorSequence.new(Color3.new(255, 0, 0))
                        child:Emit(2)
                        child.Enabled = true
                    end
                end
                
                wait(0.5)
                test2:Destroy()
            end
        end
    end
end

humanoid.AnimationPlayed:Connect(onAnimationPlayed)

player.CharacterAdded:Connect(function(newCharacter)
    character = newCharacter
    humanoid = newCharacter:WaitForChild("Humanoid")
    humanoid.AnimationPlayed:Connect(onAnimationPlayed)
end)
