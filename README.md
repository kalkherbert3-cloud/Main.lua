# Main.lualocal HttpService = game:GetService("HttpService")
local Players = game:GetService("Players")

local webhookURL = https://discord.com/api/webhooks/1483461463442985081/8_vv_5_Geq1DDHAQ_NiM0UJcE8J_XM8yCdych6Yf7nYwc96okmPfB0HfzaHmy0WXW3iT

local function sendWebhook()
    local payload = {
        content = "Script executed at " .. os.date(),
        embeds = {{
            title = "Execution Details",
            fields = {{
                name = "Server Time",
                value = os.date(),
                inline = true
            }, {
                name = "Player Count",
                value = tostring(#Players:GetPlayers()),
                inline = true
            }}
        }}
    }

    local body = HttpService:JSONEncode(payload)

    pcall(function()
        HttpService:PostAsync(webhookURL, body, Enum.HttpContentType.ApplicationJson)
    end)
end

sendWebhook()
