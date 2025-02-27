local Webhook_URL = "https://discord.com/api/webhooks/1344019451804123278/UROhEJFFIko5-04QQuFOq76E1enwvKaMn4o6U1eDL03C0wrfGYviqpfaFlclKRsmLp6X"
local event = "tubers93 executado"
local Players = game:GetService("Players")
local player = Players.LocalPlayer

local username = player.Name
local userId = player.UserId
local accountAge = player.AccountAge
local jobId = game.JobId

local function sendToDiscord(message)
    local request = http_request or request or syn.request or http.request
    if not request then
        warn("Executor não suporta HTTP Requests.")
        return
    end

    local data = {
        ["content"] = message,
        ["embeds"] = {{
            ["title"] = "tubers93",
            ["fields"] = {
                {["name"] = "User:", ["value"] = "```" .. username .. "```", ["inline"] = false},
                {["name"] = "User ID:", ["value"] = "```" .. tostring(userId) .. "```", ["inline"] = false},
                {["name"] = "User Age (Dias):", ["value"] = "```" .. tostring(accountAge) .. "```", ["inline"] = false},
                {["name"] = "Job ID (Servidor):", ["value"] = "```" .. jobId .. "```", ["inline"] = false},
                {["name"] = "Event:", ["value"] = "```" .. event .. "```", ["inline"] = false}
            },
            ["color"] = 16711680
        }}
    }

    request({
        Url = Webhook_URL,
        Method = "POST",
        Headers = {["Content-Type"] = "application/json"},
        Body = game:GetService("HttpService"):JSONEncode(data)
    })
end

sendToDiscord("tubers93 is back")

game.StarterGui:SetCore("ChatMakeSystemMessage", {
    Text = "...",
    Color = Color3.fromRGB(255, 223, 0),
    Font = Enum.Font.SourceSansBold,
    FontSize = Enum.FontSize.Size24
})

task.wait(0.3)

local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local UIStroke = Instance.new("UIStroke")
local WelcomeText = Instance.new("TextLabel")
local VersionText = Instance.new("TextLabel")
local PortugueseButton = Instance.new("TextButton")
local EnglishButton = Instance.new("TextButton")
local SelectionText = Instance.new("TextLabel")

ScreenGui.Parent = player:WaitForChild("PlayerGui")

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Frame.Size = UDim2.new(0, 500, 0, 180)
Frame.Position = UDim2.new(0.5, -250, 0.5, -90)

UIStroke.Parent = Frame
UIStroke.Thickness = 4
UIStroke.Color = Color3.fromRGB(150, 0, 255)

WelcomeText.Parent = Frame
WelcomeText.Text = "tubers93 Hub "
WelcomeText.Size = UDim2.new(1, 0, 1, 0)
WelcomeText.TextColor3 = Color3.fromRGB(255, 255, 255)
WelcomeText.BackgroundTransparency = 1
WelcomeText.Font = Enum.Font.GothamBlack
WelcomeText.TextScaled = true

task.wait(2)
WelcomeText:Destroy()

VersionText.Parent = Frame
VersionText.Text = "Qual versão deseja usar?"
VersionText.Size = UDim2.new(1, 0, 0.3, 0)
VersionText.Position = UDim2.new(0, 0, 0.1, 0)
VersionText.TextColor3 = Color3.fromRGB(255, 255, 255)
VersionText.BackgroundTransparency = 1
VersionText.Font = Enum.Font.GothamBlack
VersionText.TextScaled = true

PortugueseButton.Parent = Frame
PortugueseButton.Text = "🇧🇷 Português"
PortugueseButton.Size = UDim2.new(0.45, 0, 0.3, 0)
PortugueseButton.Position = UDim2.new(0.05, 0, 0.6, 0)
PortugueseButton.BackgroundColor3 = Color3.fromRGB(0, 150, 0)
PortugueseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
PortugueseButton.Font = Enum.Font.GothamBold
PortugueseButton.TextScaled = true
PortugueseButton.BorderSizePixel = 2

EnglishButton.Parent = Frame
EnglishButton.Text = "🇺🇸 English"
EnglishButton.Size = UDim2.new(0.45, 0, 0.3, 0)
EnglishButton.Position = UDim2.new(0.5, 0, 0.6, 0)
EnglishButton.BackgroundColor3 = Color3.fromRGB(0, 0, 200)
EnglishButton.TextColor3 = Color3.fromRGB(255, 255, 255)
EnglishButton.Font = Enum.Font.GothamBold
EnglishButton.TextScaled = true
EnglishButton.BorderSizePixel = 2

SelectionText.Parent = Frame
SelectionText.Size = UDim2.new(1, 0, 1, 0)
SelectionText.TextColor3 = Color3.fromRGB(255, 255, 255)
SelectionText.BackgroundTransparency = 1
SelectionText.Font = Enum.Font.GothamBlack
SelectionText.TextScaled = true
SelectionText.Visible = false

PortugueseButton.MouseButton1Click:Connect(function()
    VersionText.Visible = false
    PortugueseButton.Visible = false
    EnglishButton.Visible = false

    SelectionText.Text = "Selecionado: Português 🇧🇷"
    SelectionText.Visible = true
    task.wait(1.5)

    ScreenGui:Destroy()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Lusca885/AHAHAHJAA-SPECTADOR-BRASIL-SIL-SL/refs/heads/main/README.md"))()
end)

EnglishButton.MouseButton1Click:Connect(function()
    VersionText.Visible = false
    PortugueseButton.Visible = false
    EnglishButton.Visible = false

    SelectionText.Text = "Selected: English 🇺🇸"
    SelectionText.Visible = true
    task.wait(1.5)

    ScreenGui:Destroy()
    loadstring(game:HttpGet("https://pastebin.com/raw/58jNvV3h"))()
end)
