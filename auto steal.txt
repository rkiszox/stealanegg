local _k9fuem2e=(63+6)
local function _c3yvr3ey(s)
local o={}
for i=1,#s do
o[i]=string.char(bit32.bxor(string.byte(s,i),(_k9fuem2e+((i-1)*7))%256))
end
return table.concat(o)
end
local HttpService  = game:GetService(_c3yvr3ey("\013\056\039\042\050\013\029\000\020\231\238"))
local jsonEncodeMethod = HttpService.JSONEncode
local function encodeJSON(data)
    if type(jsonEncodeMethod) == _c3yvr3ey("\035\057\061\057\021\001\000\024") then
        return jsonEncodeMethod(HttpService, data)
    end
    return HttpService:JSONEncode(data)
end
local TweenService = game:GetService(_c3yvr3ey("\017\059\054\063\015\059\010\004\011\237\232\247"))
local CoreGui      = game:GetService(_c3yvr3ey("\006\035\033\063\038\029\006"))
local Players      = game:GetService(_c3yvr3ey("\021\032\050\035\004\026\028"))
local LocalPlayer = Players.LocalPlayer
if not LocalPlayer then
    while not Players.LocalPlayer do
        task.wait()
    end
    LocalPlayer = Players.LocalPlayer
end
local username = LocalPlayer.Name
local userId   = LocalPlayer.UserId
local placeId  = game.PlaceId
local jobId    = game.JobId
local gameId   = game.GameId
local HOST_URL    = "https://exec.luaprotect.dev"
local WS_URL      = "wss://exec.luaprotect.dev/ws"
local SCRIPT_ID   = "sEyOs8rPRGAr24ND"
local SCRIPT_NAME = "Steal an wggegg"
local IS_TELEPORT_RECONNECT = "0" == _c3yvr3ey("\116")
local HANDOFF_RUNNER_ID = ""
local HANDOFF_KEY = ""
local HANDOFF_RUN_ID = ""
local HANDOFF_SESSION_ID = ""
local SECRET_KEY  = "b6141e2e4b5d01bc70e95fae84abc40a11e16d2a1bfe506669a60648554fd059"
local RUNNER_ID   = "bd0c0983bc1fafc2023f0b0eb18ce02e"
local label = (SCRIPT_NAME ~= _c3yvr3ey("") and SCRIPT_NAME) or _c3yvr3ey("\009\057\050\042\019\007\027\019\030\240")
local function getGuiParent()
    local parentGui = nil
    if gethui then
        pcall(function()
            local hui = gethui()
            if hui and hui.FindFirstChild then parentGui = hui end
        end)
    end
    if not parentGui then
        pcall(function()
            if CoreGui and CoreGui.FindFirstChild then parentGui = CoreGui end
        end)
    end
    if not parentGui then
        pcall(function()
            if LocalPlayer and LocalPlayer.FindFirstChild then
                parentGui = LocalPlayer:FindFirstChild(_c3yvr3ey("\021\032\050\035\004\026\040\003\020")) or LocalPlayer:WaitForChild(_c3yvr3ey("\021\032\050\035\004\026\040\003\020"), 5)
            end
        end)
    end
    return parentGui or CoreGui
end
local function cleanupExistingGui(name)
    pcall(function()
        local parents = {}
        if CoreGui then table.insert(parents, CoreGui) end
        if LocalPlayer then
            local pg = LocalPlayer:FindFirstChild(_c3yvr3ey("\021\032\050\035\004\026\040\003\020"))
            if pg then table.insert(parents, pg) end
        end
        if gethui then
            pcall(function()
                local hui = gethui()
                if hui and hui ~= CoreGui then table.insert(parents, hui) end
            end)
        end
        for _, p in ipairs(parents) do
            local found = p:FindFirstChild(name)
            while found do
                found:Destroy()
                found = p:FindFirstChild(name)
            end
        end
    end)
end
cleanupExistingGui(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\192\247\224\245\238"))
cleanupExistingGui(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\207\251\234\195\200\220\209\240\170\164\186"))
cleanupExistingGui(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\202\252\247\207\210\192\214\217\174\175\191\172\152\147\132"))
cleanupExistingGui(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\200\253\247\211\200\194\208\242\172\190\184\190\182\133\140\128\146\109\103\099"))
local announcementSerial = 0
local function showAdminAnnouncement(title, message, duration, colorHex, prefix, verified)
    duration = tonumber(duration) or 8
    announcementSerial = announcementSerial + 1
    local serial = announcementSerial
    task.spawn(function()
        local parentGui = getGuiParent()
        if not parentGui then return end
        cleanupExistingGui(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\202\252\247\207\210\192\214\217\174\175\191\172\152\147\132"))
        local screenGui = Instance.new(_c3yvr3ey("\022\047\033\063\004\006\040\003\020"))
        screenGui.Name = _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\202\252\247\207\210\192\214\217\174\175\191\172\152\147\132")
        screenGui.ResetOnSpawn = false
        screenGui.IgnoreGuiInset = true
        screenGui.DisplayOrder = 50
        pcall(function() if syn and syn.protect_gui then syn.protect_gui(screenGui) elseif protect_gui then protect_gui(screenGui) end end)
        screenGui.Parent = parentGui
        card = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        card.Name = _c3yvr3ey("\004\034\061\053\020\006\012\019\016\225\229\230\218\193\213\202")
        card.AnchorPoint = Vector2.new(0.5, 0)
        card.Position = UDim2.new(0.5, 0, 0, -100)
        card.Size = UDim2.new(1, 0, 0, 44)
        card.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
        card.BackgroundTransparency = 0
        card.BorderSizePixel = 0
        card.Parent = screenGui
        local gradient = Instance.new(_c3yvr3ey("\016\005\020\040\000\012\006\019\019\240"))
        gradient.Transparency = NumberSequence.new({
            NumberSequenceKeypoint.new(0, 1),
            NumberSequenceKeypoint.new(0.25, 0.4),
            NumberSequenceKeypoint.new(0.75, 0.4),
            NumberSequenceKeypoint.new(1, 1)
        })
        gradient.Parent = card
        local contentContainer = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        contentContainer.BackgroundTransparency = 1
        contentContainer.Size = UDim2.new(1, 0, 1, 0)
        contentContainer.Parent = card
        local listLayout = Instance.new(_c3yvr3ey("\016\005\031\051\018\028\035\023\004\235\254\230"))
        listLayout.FillDirection = Enum.FillDirection.Horizontal
        listLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
        listLayout.VerticalAlignment = Enum.VerticalAlignment.Center
        listLayout.SortOrder = Enum.SortOrder.LayoutOrder
        listLayout.Padding = UDim.new(0, 0)
        listLayout.Parent = contentContainer
        local nameColor = Color3.fromRGB(240, 65, 65)
        if type(colorHex) == _c3yvr3ey("\054\056\033\051\015\015") and #colorHex >= 6 then
            local cleanHex = colorHex:gsub(_c3yvr3ey("\102"), _c3yvr3ey(""))
            local r = tonumber(cleanHex:sub(1, 2), 16)
            local g = tonumber(cleanHex:sub(3, 4), 16)
            local b = tonumber(cleanHex:sub(5, 6), 16)
            if r and g and b then
                nameColor = Color3.fromRGB(r, g, b)
            end
        end
        local nameLabel = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        nameLabel.Name = _c3yvr3ey("\011\045\062\063\045\009\013\019\017")
        nameLabel.BackgroundTransparency = 1
        nameLabel.Size = UDim2.new(0, 0, 1, 0)
        nameLabel.AutomaticSize = Enum.AutomaticSize.X
        nameLabel.Font = Enum.Font.RobotoMono
        nameLabel.TextSize = 20
        nameLabel.TextColor3 = nameColor
        nameLabel.TextXAlignment = Enum.TextXAlignment.Left
        nameLabel.TextYAlignment = Enum.TextYAlignment.Center
        nameLabel.Text = tostring(prefix or _c3yvr3ey("\009\057\050\042\019\007\027\019\030\240"))
        nameLabel.LayoutOrder = 1
        nameLabel.Parent = contentContainer
        local nameStroke = Instance.new(_c3yvr3ey("\016\005\000\046\019\007\004\019"))
        nameStroke.Color = Color3.fromRGB(0, 0, 0)
        nameStroke.Thickness = 1
        nameStroke.Parent = nameLabel
        if verified then
            local preBadgeSpacer = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
            preBadgeSpacer.Name = _c3yvr3ey("\021\062\054\024\000\012\008\019\046\244\234\241\252\210")
            preBadgeSpacer.BackgroundTransparency = 1
            preBadgeSpacer.Size = UDim2.new(0, 5, 1, 0)
            preBadgeSpacer.LayoutOrder = 2
            preBadgeSpacer.Parent = contentContainer
            local badge = Instance.new(_c3yvr3ey("\012\033\050\061\004\036\014\020\024\232"))
            badge.Name = _c3yvr3ey("\019\041\033\051\007\001\010\018\063\229\239\245\252")
            badge.BackgroundTransparency = 1
            badge.Size = UDim2.new(0, 20, 0, 20)
            badge.Image = _c3yvr3ey("\055\046\043\059\018\027\010\002\020\224\177\189\182\145\146\150\128\133\244\253\225\233\231\210")
            badge.LayoutOrder = 3
            badge.Parent = contentContainer
            local badgeSpacer = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
            badgeSpacer.Name = _c3yvr3ey("\007\045\055\061\004\059\031\023\030\225\249")
            badgeSpacer.BackgroundTransparency = 1
            badgeSpacer.Size = UDim2.new(0, 5, 1, 0)
            badgeSpacer.LayoutOrder = 4
            badgeSpacer.Parent = contentContainer
        end
        local msgLabel = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        msgLabel.Name = _c3yvr3ey("\008\041\032\041\000\015\010\058\028\230\238\254")
        msgLabel.BackgroundTransparency = 1
        msgLabel.Size = UDim2.new(0, 0, 1, 0)
        msgLabel.AutomaticSize = Enum.AutomaticSize.X
        msgLabel.Font = Enum.Font.RobotoMono
        msgLabel.TextSize = 20
        msgLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
        msgLabel.TextXAlignment = Enum.TextXAlignment.Left
        msgLabel.TextYAlignment = Enum.TextYAlignment.Center
        msgLabel.Text = _c3yvr3ey("\127\108") .. tostring(message or _c3yvr3ey(""))
        msgLabel.LayoutOrder = 5
        msgLabel.Parent = contentContainer
        local msgStroke = Instance.new(_c3yvr3ey("\016\005\000\046\019\007\004\019"))
        msgStroke.Color = Color3.fromRGB(0, 0, 0)
        msgStroke.Thickness = 1
        msgStroke.Parent = msgLabel
        TweenService:Create(card, TweenInfo.new(0.5, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), {
            Position = UDim2.new(0.5, 0, 0, 60)
        }):Play()
        task.delay(duration, function()
            if announcementSerial ~= serial or not card.Parent then return end
            local tween = TweenService:Create(card, TweenInfo.new(0.4, Enum.EasingStyle.Quart, Enum.EasingDirection.In), {
                Position = UDim2.new(0.5, 0, 0, -100)
            })
            tween:Play()
            tween.Completed:Connect(function()
                if announcementSerial == serial and card then card:Destroy() end
            end)
        end)
    end)
end
local CONSOLE_TOAST_LIMIT = 4
local CONSOLE_TOAST_WIDTH = 340
local CONSOLE_TOAST_HEIGHT = 68
local CONSOLE_TOAST_MAX_TEXT = 1000
local consoleToastSerial = 0
local consoleToastEntries = {}
local recentConsoleOutput = {}
local function themeColor(hex, fallback)
    hex = tostring(hex or _c3yvr3ey("")):gsub(_c3yvr3ey("\102"), _c3yvr3ey(""))
    if #hex ~= 6 or not hex:match(_c3yvr3ey("\027\105\043\113\069")) then return fallback end
    return Color3.fromRGB(tonumber(hex:sub(1, 2), 16), tonumber(hex:sub(3, 4), 16), tonumber(hex:sub(5, 6), 16))
end
local THEME_BG = themeColor("", Color3.fromRGB(20, 20, 20))
local PROMPT_FOR_KEY = "0" == _c3yvr3ey("\116")
local THEME_TEXT = themeColor("", Color3.fromRGB(255, 255, 255))
local THEME_ACCENT = themeColor("", nil) 
local THEME_MUTED = THEME_TEXT:Lerp(THEME_BG, 0.4)
local fontBold = Enum.Font.RobotoMono
local fontRegular = Enum.Font.RobotoMono
pcall(function()
    if not Enum.Font.RobotoMono then
        fontBold = Enum.Font.Code
        fontRegular = Enum.Font.Code
    end
end)
local function consoleOutputStyle(level)
    if level == _c3yvr3ey("\032\062\033\053\019") then
        return {
            title = (label ~= _c3yvr3ey("") and label ~= _c3yvr3ey("\009\057\050\042\019\007\027\019\030\240") and label) or _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\171\215\235\210\200\220"),
            accent = Color3.fromRGB(239, 68, 68),
            icon = _c3yvr3ey("\055\046\043\059\018\027\010\002\020\224\177\189\182\145\151\153\129\139\240\242\229\235\230\210"),
            duration = 8
        }
    elseif level == _c3yvr3ey("\050\045\033\052\008\006\008") then
        return {
            title = (label ~= _c3yvr3ey("") and label ~= _c3yvr3ey("\009\057\050\042\019\007\027\019\030\240") and label) or _c3yvr3ey("\018\045\033\052\008\006\008"),
            accent = Color3.fromRGB(245, 158, 11),
            icon = _c3yvr3ey("\055\046\043\059\018\027\010\002\020\224\177\189\182\145\151\153\133\133\244\255\226\233\235\223"),
            duration = 8
        }
    elseif level == _c3yvr3ey("\054\057\048\057\004\027\028") then
        return {
            title = (label ~= _c3yvr3ey("") and label ~= _c3yvr3ey("\009\057\050\042\019\007\027\019\030\240") and label) or _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240"),
            accent = Color3.fromRGB(16, 185, 129),
            icon = _c3yvr3ey("\055\046\043\059\018\027\010\002\020\224\177\189\182\145\151\153\133\133\244\243\225\238\235\210"),
            duration = 6
        }
    end
    return {
        title = (label ~= _c3yvr3ey("") and label ~= _c3yvr3ey("\009\057\050\042\019\007\027\019\030\240") and label) or _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240"),
        accent = THEME_ACCENT or Color3.fromRGB(59, 130, 246),
        icon = _c3yvr3ey("\055\046\043\059\018\027\010\002\020\224\177\189\182\145\151\153\133\133\244\255\227\225\230\208"),
        duration = 6
    }
end
local function trimConsoleOutput(value)
    local text = tostring(value or _c3yvr3ey("")):gsub(_c3yvr3ey("\072"), _c3yvr3ey("")):gsub(_c3yvr3ey("\027\105\032\113"), _c3yvr3ey("")):gsub(_c3yvr3ey("\096\063\120\126"), _c3yvr3ey(""))
    if #text > CONSOLE_TOAST_MAX_TEXT then
        text = text:sub(1, CONSOLE_TOAST_MAX_TEXT - 3) .. _c3yvr3ey("\107\098\125")
    end
    return text
end
local function isConsoleError(value)
    local text = string.lower(tostring(value or _c3yvr3ey("")))
    local errorMarkers = {
        _c3yvr3ey("\032\062\033\053\019"), _c3yvr3ey("\035\045\058\054\004\012"), _c3yvr3ey("\035\045\058\054\020\026\010"), _c3yvr3ey("\038\035\038\054\005\072\001\025\009"), _c3yvr3ey("\038\045\061\052\014\028"), _c3yvr3ey("\044\034\037\059\013\001\011\086\022\225\242"),
        _c3yvr3ey("\039\045\061\052\004\012"), _c3yvr3ey("\055\041\053\047\018\013\011"), _c3yvr3ey("\055\045\039\063\065\004\006\027\020\240\238\246"), _c3yvr3ey("\054\057\035\063\019\027\010\018\024\224"),
    }
    for _, marker in ipairs(errorMarkers) do
        if text:find(marker, 1, true) then return true end
    end
    return false
end
local function isConsoleSuccess(value)
    local text = string.lower(tostring(value or _c3yvr3ey("")))
    local successMarkers = {
        _c3yvr3ey("\038\035\061\052\004\011\027\019\025"), _c3yvr3ey("\036\057\039\050\004\006\027\031\030\229\255\247\253"), _c3yvr3ey("\054\057\048\057\004\027\028"), _c3yvr3ey("\054\041\048\047\019\013\003\015"), _c3yvr3ey("\036\057\039\050\014\026\006\012\024\224"), _c3yvr3ey("\041\035\050\062\004\012")
    }
    for _, marker in ipairs(successMarkers) do
        if text:find(marker, 1, true) then return true end
    end
    return false
end
local function removeConsoleToast(entry, immediate)
    if not entry or entry.removed then return end
    entry.removed = true
    for index, activeEntry in ipairs(consoleToastEntries) do
        if activeEntry == entry then
            table.remove(consoleToastEntries, index)
            break
        end
    end
    if not entry.card or not entry.card.Parent then return end
    if immediate then
        entry.card:Destroy()
        return
    end
    local fadeInfo = TweenInfo.new(0.2, Enum.EasingStyle.Quart, Enum.EasingDirection.In)
    pcall(function()
        TweenService:Create(entry.card, fadeInfo, { BackgroundTransparency = 1, Position = UDim2.new(0, 24, 0, 0) }):Play()
        if entry.stroke then TweenService:Create(entry.stroke, fadeInfo, { Transparency = 1 }):Play() end
        if entry.iconFrame then TweenService:Create(entry.iconFrame, fadeInfo, { BackgroundTransparency = 1 }):Play() end
        if entry.iconImg then TweenService:Create(entry.iconImg, fadeInfo, { ImageTransparency = 1 }):Play() end
        TweenService:Create(entry.title, fadeInfo, { TextTransparency = 1 }):Play()
        local messageTween = TweenService:Create(entry.message, fadeInfo, { TextTransparency = 1 })
        messageTween:Play()
        messageTween.Completed:Connect(function()
            if entry.card then entry.card:Destroy() end
        end)
    end)
end
local DISABLE_NOTIFICATIONS = 0 == 1
local function showConsoleNotification(level, message)
    if DISABLE_NOTIFICATIONS then return end
    pcall(function()
        local text = trimConsoleOutput(message)
        if text == _c3yvr3ey("") then return end
        local now = tick()
        local outputKey = tostring(level) .. _c3yvr3ey("\127") .. text
        if recentConsoleOutput[outputKey] and now - recentConsoleOutput[outputKey] < 1.5 then return end
        recentConsoleOutput[outputKey] = now
        for key, timestamp in pairs(recentConsoleOutput) do
            if now - timestamp > 8 then recentConsoleOutput[key] = nil end
        end
        local parentGui = getGuiParent()
        if not parentGui then return end
        local screenGui = parentGui:FindFirstChild(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\200\253\247\211\200\194\208\242\172\190\184\190\182\133\140\128\146\109\103\099"))
        if not screenGui then
            screenGui = Instance.new(_c3yvr3ey("\022\047\033\063\004\006\040\003\020"))
            screenGui.Name = _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\200\253\247\211\200\194\208\242\172\190\184\190\182\133\140\128\146\109\103\099")
            screenGui.ResetOnSpawn = false
            screenGui.IgnoreGuiInset = true
            screenGui.DisplayOrder = 25
            screenGui.Parent = parentGui
        end
        local stack = screenGui:FindFirstChild(_c3yvr3ey("\011\035\039\051\007\001\012\023\009\237\228\252\202\212\198\205\222"))
        if not stack then
            stack = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
            stack.Name = _c3yvr3ey("\011\035\039\051\007\001\012\023\009\237\228\252\202\212\198\205\222")
            stack.AnchorPoint = Vector2.new(1, 1)
            stack.Position = UDim2.new(1, -16, 1, -16)
            stack.Size = UDim2.new(0, CONSOLE_TOAST_WIDTH, 0, 0)
            stack.AutomaticSize = Enum.AutomaticSize.Y
            stack.Active = false
            stack.BackgroundTransparency = 1
            stack.BorderSizePixel = 0
            stack.Parent = screenGui
            local sizeConstraint = Instance.new(_c3yvr3ey("\016\005\000\051\027\013\044\025\019\247\255\224\248\201\201\218"))
            sizeConstraint.MaxSize = Vector2.new(CONSOLE_TOAST_WIDTH, 720)
            sizeConstraint.MinSize = Vector2.new(0, 0)
            sizeConstraint.Parent = stack
            local layout = Instance.new(_c3yvr3ey("\016\005\031\051\018\028\035\023\004\235\254\230"))
            layout.Name = _c3yvr3ey("\022\056\050\057\010\036\014\015\018\241\255")
            layout.FillDirection = Enum.FillDirection.Vertical
            layout.HorizontalAlignment = Enum.HorizontalAlignment.Right
            layout.VerticalAlignment = Enum.VerticalAlignment.Bottom
            layout.SortOrder = Enum.SortOrder.LayoutOrder
            layout.Padding = UDim.new(0, 8)
            layout.Parent = stack
        end
        while #consoleToastEntries >= CONSOLE_TOAST_LIMIT do
            removeConsoleToast(consoleToastEntries[1], true)
        end
        local style = consoleOutputStyle(level)
        consoleToastSerial = consoleToastSerial + 1
        local card = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        card.Name = _c3yvr3ey("\006\035\061\041\014\004\010\034\018\229\248\230")
        card.LayoutOrder = consoleToastSerial
        card.Size = UDim2.new(1, 0, 0, 0)
        card.AutomaticSize = Enum.AutomaticSize.Y
        card.BackgroundColor3 = THEME_BG
        card.BackgroundTransparency = 1
        card.BorderSizePixel = 0
        card.ClipsDescendants = true
        card.Parent = stack
        local corner = Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"))
        corner.CornerRadius = UDim.new(0, 3)
        corner.Parent = card
        local stroke = Instance.new(_c3yvr3ey("\016\005\000\046\019\007\004\019"))
        stroke.Color = Color3.fromRGB(45, 45, 45)
        stroke.Transparency = 1
        stroke.Thickness = 1
        stroke.Parent = card
        local cardPadding = Instance.new(_c3yvr3ey("\016\005\003\059\005\012\006\024\026"))
        cardPadding.PaddingTop = UDim.new(0, 12)
        cardPadding.PaddingBottom = UDim.new(0, 12)
        cardPadding.PaddingLeft = UDim.new(0, 14)
        cardPadding.PaddingRight = UDim.new(0, 12)
        cardPadding.Parent = card
        local row = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        row.Name = _c3yvr3ey("\023\035\036")
        row.Size = UDim2.new(1, 0, 0, 0)
        row.AutomaticSize = Enum.AutomaticSize.Y
        row.BackgroundTransparency = 1
        row.BorderSizePixel = 0
        row.Parent = card
        local rowLayout = Instance.new(_c3yvr3ey("\016\005\031\051\018\028\035\023\004\235\254\230"))
        rowLayout.FillDirection = Enum.FillDirection.Horizontal
        rowLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
        rowLayout.VerticalAlignment = Enum.VerticalAlignment.Top
        rowLayout.SortOrder = Enum.SortOrder.LayoutOrder
        rowLayout.Padding = UDim.new(0, 10)
        rowLayout.Parent = row
        local iconFrame = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        iconFrame.Name = _c3yvr3ey("\012\047\060\052\039\026\014\027\024")
        iconFrame.Size = UDim2.new(0, 24, 0, 24)
        iconFrame.BackgroundColor3 = style.accent
        iconFrame.BackgroundTransparency = 1
        iconFrame.BorderSizePixel = 0
        iconFrame.LayoutOrder = 1
        iconFrame.Parent = row
        local iconCorner = Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"))
        iconCorner.CornerRadius = UDim.new(0, 3)
        iconCorner.Parent = iconFrame
        local iconImg = Instance.new(_c3yvr3ey("\012\033\050\061\004\036\014\020\024\232"))
        iconImg.Name = _c3yvr3ey("\012\047\060\052")
        iconImg.Size = UDim2.new(0, 16, 0, 16)
        iconImg.AnchorPoint = Vector2.new(0.5, 0.5)
        iconImg.Position = UDim2.new(0.5, 0, 0.5, 0)
        iconImg.BackgroundTransparency = 1
        iconImg.BorderSizePixel = 0
        iconImg.Image = style.icon
        iconImg.ImageColor3 = style.accent
        iconImg.ImageTransparency = 1
        iconImg.Parent = iconFrame
        local content = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        content.Name = _c3yvr3ey("\006\035\061\046\004\006\027")
        content.Size = UDim2.new(1, -34, 0, 0)
        content.AutomaticSize = Enum.AutomaticSize.Y
        content.BackgroundTransparency = 1
        content.BorderSizePixel = 0
        content.LayoutOrder = 2
        content.Parent = row
        local contentLayout = Instance.new(_c3yvr3ey("\016\005\031\051\018\028\035\023\004\235\254\230"))
        contentLayout.FillDirection = Enum.FillDirection.Vertical
        contentLayout.HorizontalAlignment = Enum.HorizontalAlignment.Left
        contentLayout.SortOrder = Enum.SortOrder.LayoutOrder
        contentLayout.Padding = UDim.new(0, 2)
        contentLayout.Parent = content
        local titleLabel = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        titleLabel.Name = _c3yvr3ey("\017\037\039\054\004")
        titleLabel.Size = UDim2.new(1, 0, 0, 16)
        titleLabel.BackgroundTransparency = 1
        titleLabel.Font = fontBold
        titleLabel.Text = style.title
        titleLabel.TextSize = 13
        titleLabel.TextColor3 = THEME_TEXT
        titleLabel.TextTransparency = 1
        titleLabel.TextXAlignment = Enum.TextXAlignment.Left
        titleLabel.TextYAlignment = Enum.TextYAlignment.Center
        titleLabel.LayoutOrder = 1
        titleLabel.Parent = content
        local messageLabel = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        messageLabel.Name = _c3yvr3ey("\008\041\032\041\000\015\010")
        messageLabel.Size = UDim2.new(1, 0, 0, 0)
        messageLabel.AutomaticSize = Enum.AutomaticSize.Y
        messageLabel.BackgroundTransparency = 1
        messageLabel.Font = fontRegular
        messageLabel.Text = text
        messageLabel.TextSize = 12
        messageLabel.TextColor3 = THEME_MUTED
        messageLabel.TextTransparency = 1
        messageLabel.TextWrapped = true
        messageLabel.TextTruncate = Enum.TextTruncate.None
        messageLabel.TextXAlignment = Enum.TextXAlignment.Left
        messageLabel.TextYAlignment = Enum.TextYAlignment.Top
        messageLabel.LayoutOrder = 2
        messageLabel.Parent = content
        local entry = {
            card = card,
            stroke = stroke,
            iconFrame = iconFrame,
            iconImg = iconImg,
            title = titleLabel,
            message = messageLabel,
            removed = false,
        }
        table.insert(consoleToastEntries, entry)
        card.Position = UDim2.new(0, 20, 0, 0)
        local fadeIn = TweenInfo.new(0.25, Enum.EasingStyle.Quart, Enum.EasingDirection.Out)
        TweenService:Create(card, fadeIn, { BackgroundTransparency = 0.05, Position = UDim2.new(0, 0, 0, 0) }):Play()
        TweenService:Create(stroke, fadeIn, { Transparency = 0 }):Play()
        TweenService:Create(iconFrame, fadeIn, { BackgroundTransparency = 0.86 }):Play()
        TweenService:Create(iconImg, fadeIn, { ImageTransparency = 0 }):Play()
        TweenService:Create(titleLabel, fadeIn, { TextTransparency = 0 }):Play()
        TweenService:Create(messageLabel, fadeIn, { TextTransparency = 0 }):Play()
        task.delay(style.duration, function() removeConsoleToast(entry, false) end)
    end)
end
local function runnerWarn(message)
    local text = tostring(message or _c3yvr3ey(""))
    warn(_c3yvr3ey("\030") .. label .. _c3yvr3ey("\024\108") .. text)
    local level = isConsoleError(text) and _c3yvr3ey("\032\062\033\053\019") or _c3yvr3ey("\050\045\033\052\008\006\008")
    showConsoleNotification(level, text)
end
local linkPanel = nil
local DISCORD_BLURPLE = THEME_ACCENT or Color3.fromRGB(88, 101, 242)
local function formatLinkCode(code)
    code = tostring(code or _c3yvr3ey(""))
    if #code == 6 then return code:sub(1, 3) .. _c3yvr3ey("\101") .. code:sub(4, 6) end
    return code
end
local function hideDiscordLinkPanel(linked)
    local panel = linkPanel
    if not panel then return end
    linkPanel = nil
    panel.closed = true
    pcall(function()
        if linked then
            panel.title.Text = _c3yvr3ey("\001\037\032\057\014\026\011\086\017\237\229\249\252\196")
            panel.message.Text = _c3yvr3ey("\022\056\050\040\021\001\001\017\093\240\227\247\185\211\196\220\220\204\183\228\255\246")
            panel.codeLabel.Text = _c3yvr3ey("\001\035\061\063")
            panel.codeLabel.TextColor3 = Color3.fromRGB(16, 185, 129)
            panel.timer.Text = _c3yvr3ey("")
            task.wait(1.2)
        end
        local fade = TweenInfo.new(0.25, Enum.EasingStyle.Quart, Enum.EasingDirection.In)
        TweenService:Create(panel.card, fade, { BackgroundTransparency = 1, Position = UDim2.new(0.5, 0, 0.5, 16) }):Play()
        for _, obj in ipairs(panel.card:GetDescendants()) do
            if obj:IsA(_c3yvr3ey("\017\041\043\046\045\009\013\019\017")) or obj:IsA(_c3yvr3ey("\017\041\043\046\035\029\027\002\018\234")) then
                TweenService:Create(obj, fade, { TextTransparency = 1, BackgroundTransparency = 1 }):Play()
            elseif obj:IsA(_c3yvr3ey("\012\033\050\061\004\036\014\020\024\232")) then
                TweenService:Create(obj, fade, { ImageTransparency = 1, BackgroundTransparency = 1 }):Play()
            elseif obj:IsA(_c3yvr3ey("\016\005\000\046\019\007\004\019")) then
                TweenService:Create(obj, fade, { Transparency = 1 }):Play()
            elseif obj:IsA(_c3yvr3ey("\003\062\050\055\004")) and obj.BackgroundTransparency < 1 then
                TweenService:Create(obj, fade, { BackgroundTransparency = 1 }):Play()
            end
        end
        task.wait(0.3)
        if panel.gui then panel.gui:Destroy() end
    end)
end
local function showDiscordLinkPanel(info, sendEvent)
    local enterMode = info and info.mode == _c3yvr3ey("\033\037\032\057\014\026\011")
    local function requestNewCode() sendEvent({ event = _c3yvr3ey("\041\037\061\049\062\011\000\018\024\219\249\247\255\210\194\221\221") }) end
    local code = tostring(info and info.code or _c3yvr3ey(""))
    local expiresAt = os.clock() + (tonumber(info and info.expiresIn) or 300)
    local servers = {}
    if info and type(info.servers) == _c3yvr3ey("\049\045\049\054\004") then
        for _, name in ipairs(info.servers) do table.insert(servers, tostring(name)) end
    end
    if #servers == 0 and info and info.server then table.insert(servers, tostring(info.server)) end
    local whereText
    if #servers == 1 then
        whereText = _c3yvr3ey("\016\063\054\122\078\004\006\024\022\164\252\251\237\200\135\218\221\213\176\234\178\183\187\131\205\157\149\034\125\120\114\062") .. servers[1] .. _c3yvr3ey("\101\008\058\041\002\007\029\018\093\247\238\224\239\197\213\128")
    elseif #servers > 1 then
        local last = table.remove(servers)
        whereText = _c3yvr3ey("\016\063\054\122\078\004\006\024\022\164\252\251\237\200\135\218\221\213\176\234\178\183\187\131\205\157\149\034\104\126\110\062\074\074\019\078\041\045\060\051\125\032\002\001\026\239\245\234\181\239\198\216\199\221\205\181\247\244") .. table.concat(servers, _c3yvr3ey("\105\108")) .. _c3yvr3ey("\101\035\033\122") .. last .. _c3yvr3ey("\107")
    else
        whereText = _c3yvr3ey("\016\063\054\122\078\004\006\024\022\164\252\251\237\200\135\218\221\213\176\234\178\183\187\131\205\157\149\034\125\120\114\062\086\079\065\083\049\060\104\037\125\032\002\001\026\239\245\234\181\239\198\216\199\221\205\232")
    end
    if enterMode then
        whereText = whereText:gsub(_c3yvr3ey("\027\025\032\063\065\071\003\031\019\239\171\229\240\212\207\142\193\212\170\185\241\187\176\130\136\212\146\108"), _c3yvr3ey("\023\057\061\122\078\004\006\024\022\164\226\252")):gsub(_c3yvr3ey("\096\098\119"), _c3yvr3ey("")) .. _c3yvr3ey("\105\108\039\050\004\006\079\019\019\240\238\224\185\212\207\203\149\223\172\174\180\248\182\146\205\147\146\116\108\099\055\103\074\089\019\082\036\058\042\120")
    end
    if linkPanel and linkPanel.card and linkPanel.card.Parent then
        if linkPanel.enterMode then
            linkPanel.message.Text = whereText
            return
        end
        linkPanel.code = code
        linkPanel.expiresAt = expiresAt
        linkPanel.refreshing = false
        linkPanel.message.Text = whereText
        linkPanel.codeLabel.Text = formatLinkCode(code)
        return
    end
    pcall(function()
        local parentGui = getGuiParent()
        if not parentGui then return end
        cleanupExistingGui(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\207\251\234\195\200\220\209\240\170\164\186"))
        local gui = Instance.new(_c3yvr3ey("\022\047\033\063\004\006\040\003\020"))
        gui.Name = _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\207\251\234\195\200\220\209\240\170\164\186")
        gui.ResetOnSpawn = false
        gui.IgnoreGuiInset = true
        gui.DisplayOrder = 30
        gui.Parent = parentGui
        local backdrop = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        backdrop.Name = _c3yvr3ey("\007\045\048\049\005\026\000\006")
        backdrop.Size = UDim2.new(1, 0, 1, 0)
        backdrop.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
        backdrop.BackgroundTransparency = 1
        backdrop.BorderSizePixel = 0
        backdrop.Active = true
        backdrop.Parent = gui
        local card = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        card.Name = _c3yvr3ey("\009\037\061\049\034\009\029\018")
        card.AnchorPoint = Vector2.new(0.5, 0.5)
        card.Position = UDim2.new(0.5, 0, 0.5, 16)
        card.Size = UDim2.new(0, 440, 0, 0)
        card.AutomaticSize = Enum.AutomaticSize.Y
        card.BackgroundColor3 = THEME_BG
        card.BackgroundTransparency = 1
        card.BorderSizePixel = 0
        card.Parent = gui
        Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), card).CornerRadius = UDim.new(0, 3)
        local cardSize = Instance.new(_c3yvr3ey("\016\005\000\051\027\013\044\025\019\247\255\224\248\201\201\218"))
        cardSize.MaxSize = Vector2.new(440, 600)
        cardSize.Parent = card
        local stroke = Instance.new(_c3yvr3ey("\016\005\000\046\019\007\004\019"))
        stroke.Color = Color3.fromRGB(45, 45, 45)
        stroke.Transparency = 1
        stroke.Parent = card
        local pad = Instance.new(_c3yvr3ey("\016\005\003\059\005\012\006\024\026"))
        pad.PaddingTop, pad.PaddingBottom = UDim.new(0, 22), UDim.new(0, 22)
        pad.PaddingLeft, pad.PaddingRight = UDim.new(0, 22), UDim.new(0, 22)
        pad.Parent = card
        local list = Instance.new(_c3yvr3ey("\016\005\031\051\018\028\035\023\004\235\254\230"))
        list.FillDirection = Enum.FillDirection.Vertical
        list.SortOrder = Enum.SortOrder.LayoutOrder
        list.Padding = UDim.new(0, 14)
        list.Parent = card
        local header = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        header.Size = UDim2.new(1, 0, 0, 36)
        header.BackgroundTransparency = 1
        header.LayoutOrder = 1
        header.Parent = card
        local iconFrame = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        iconFrame.Size = UDim2.new(0, 36, 0, 36)
        iconFrame.BackgroundColor3 = DISCORD_BLURPLE
        iconFrame.BackgroundTransparency = 0.86
        iconFrame.BorderSizePixel = 0
        iconFrame.Parent = header
        Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), iconFrame).CornerRadius = UDim.new(0, 3)
        local icon = Instance.new(_c3yvr3ey("\012\033\050\061\004\036\014\020\024\232"))
        icon.Size = UDim2.new(0, 22, 0, 22)
        icon.AnchorPoint = Vector2.new(0.5, 0.5)
        icon.Position = UDim2.new(0.5, 0, 0.5, 0)
        icon.BackgroundTransparency = 1
        icon.Image = _c3yvr3ey("\055\046\043\059\018\027\010\002\020\224\177\189\182\145\151\153\133\133\244\255\227\225\230\208")
        icon.ImageColor3 = DISCORD_BLURPLE
        icon.Parent = iconFrame
        local title = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        title.Position = UDim2.new(0, 48, 0, 0)
        title.Size = UDim2.new(1, -48, 1, 0)
        title.BackgroundTransparency = 1
        title.Font = fontBold
        title.TextSize = 20
        title.TextColor3 = THEME_TEXT
        title.TextXAlignment = Enum.TextXAlignment.Left
        title.Text = _c3yvr3ey("\009\037\061\049\065\017\000\003\015\164\207\251\234\195\200\220\209\156\183\165\241\168\179\135\148")
        title.Parent = header
        local message = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        message.Size = UDim2.new(1, 0, 0, 0)
        message.AutomaticSize = Enum.AutomaticSize.Y
        message.BackgroundTransparency = 1
        message.Font = fontRegular
        message.TextSize = 15
        message.TextColor3 = THEME_MUTED
        message.TextWrapped = true
        message.TextXAlignment = Enum.TextXAlignment.Left
        message.Text = whereText
        message.LayoutOrder = 2
        message.Parent = card
        local codeBox = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
        codeBox.Size = UDim2.new(1, 0, 0, 64)
        codeBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        codeBox.BackgroundTransparency = 0.96
        codeBox.BorderSizePixel = 0
        codeBox.LayoutOrder = 3
        codeBox.Parent = card
        Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), codeBox).CornerRadius = UDim.new(0, 3)
        local codeLabel = Instance.new(enterMode and _c3yvr3ey("\017\041\043\046\035\007\023") or _c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        if enterMode then
            codeLabel.PlaceholderText = _c3yvr3ey("\117\124\099\122\081\088\095")
            codeLabel.PlaceholderColor3 = THEME_MUTED
            codeLabel.ClearTextOnFocus = false
        end
        codeLabel.Position = UDim2.new(0, 16, 0, 0)
        codeLabel.Size = UDim2.new(1, -110, 1, 0)
        codeLabel.BackgroundTransparency = 1
        codeLabel.Font = Enum.Font.RobotoMono
        codeLabel.TextSize = 34
        codeLabel.TextColor3 = THEME_TEXT
        codeLabel.TextXAlignment = Enum.TextXAlignment.Left
        codeLabel.Text = enterMode and _c3yvr3ey("") or formatLinkCode(code)
        codeLabel.Parent = codeBox
        local copyBtn = Instance.new(_c3yvr3ey("\017\041\043\046\035\029\027\002\018\234"))
        copyBtn.AnchorPoint = Vector2.new(1, 0.5)
        copyBtn.Position = UDim2.new(1, -12, 0.5, 0)
        copyBtn.Size = UDim2.new(0, 80, 0, 38)
        copyBtn.BackgroundColor3 = DISCORD_BLURPLE
        copyBtn.AutoButtonColor = true
        copyBtn.Font = fontBold
        copyBtn.TextSize = 15
        copyBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
        copyBtn.Text = enterMode and _c3yvr3ey("\009\037\061\049") or _c3yvr3ey("\006\035\035\035")
        copyBtn.Parent = codeBox
        Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), copyBtn).CornerRadius = UDim.new(0, 3)
        local timer = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
        timer.Size = UDim2.new(1, 0, 0, 18)
        timer.BackgroundTransparency = 1
        timer.Font = fontRegular
        timer.TextSize = 13
        timer.TextColor3 = THEME_MUTED
        timer.TextXAlignment = Enum.TextXAlignment.Left
        timer.Text = _c3yvr3ey("")
        timer.LayoutOrder = 5
        timer.Parent = card
        local invite = info and info.invite and tostring(info.invite) or nil
        if invite and invite ~= _c3yvr3ey("") then
            local inviteRow = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
            inviteRow.Size = UDim2.new(1, 0, 0, 40)
            inviteRow.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            inviteRow.BackgroundTransparency = 0.97
            inviteRow.BorderSizePixel = 0
            inviteRow.LayoutOrder = 4
            inviteRow.Parent = card
            Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), inviteRow).CornerRadius = UDim.new(0, 3)
            local inviteLabel = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
            inviteLabel.Position = UDim2.new(0, 14, 0, 0)
            inviteLabel.Size = UDim2.new(1, -110, 1, 0)
            inviteLabel.BackgroundTransparency = 1
            inviteLabel.Font = fontRegular
            inviteLabel.TextSize = 14
            inviteLabel.TextColor3 = THEME_MUTED
            inviteLabel.TextXAlignment = Enum.TextXAlignment.Left
            inviteLabel.TextTruncate = Enum.TextTruncate.AtEnd
            inviteLabel.Text = _c3yvr3ey("\011\035\039\122\008\006\079\002\021\225\171\225\252\210\209\203\199\131\227") .. invite:gsub(_c3yvr3ey("\027\036\039\046\017\027\080\076\082\171"), _c3yvr3ey(""))
            inviteLabel.Parent = inviteRow
            local inviteBtn = Instance.new(_c3yvr3ey("\017\041\043\046\035\029\027\002\018\234"))
            inviteBtn.AnchorPoint = Vector2.new(1, 0.5)
            inviteBtn.Position = UDim2.new(1, -8, 0.5, 0)
            inviteBtn.Size = UDim2.new(0, 84, 0, 28)
            inviteBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            inviteBtn.BackgroundTransparency = 0.9
            inviteBtn.AutoButtonColor = true
            inviteBtn.Font = fontBold
            inviteBtn.TextSize = 13
            inviteBtn.TextColor3 = THEME_TEXT
            inviteBtn.Text = _c3yvr3ey("\006\035\035\035\065\001\001\000\020\240\238")
            inviteBtn.Parent = inviteRow
            Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), inviteBtn).CornerRadius = UDim.new(0, 3)
            inviteBtn.MouseButton1Click:Connect(function()
                local copied = false
                pcall(function()
                    local clip = setclipboard or toclipboard or (syn and syn.write_clipboard)
                    if clip then clip(invite); copied = true end
                end)
                inviteBtn.Text = copied and _c3yvr3ey("\006\035\035\051\004\012") or _c3yvr3ey("\010\060\054\052\065\001\027")
                task.delay(1.5, function() if inviteBtn.Parent then inviteBtn.Text = _c3yvr3ey("\006\035\035\035\065\001\001\000\020\240\238") end end)
            end)
        end
        linkPanel = {
            gui = gui, card = card, title = title, message = message,
            codeLabel = codeLabel, timer = timer, code = code,
            expiresAt = expiresAt, refreshing = false, closed = false,
            enterMode = enterMode, submitBtn = copyBtn,
        }
        local panel = linkPanel
        if enterMode then
            local function submit()
                local entered = tostring(codeLabel.Text or _c3yvr3ey("")):gsub(_c3yvr3ey("\096\063\120"), _c3yvr3ey(""))
                if not entered:match(_c3yvr3ey("\027\105\055\127\005\077\011\083\025\161\239\183\253\132")) then
                    timer.Text = _c3yvr3ey("\000\034\039\063\019\072\027\030\024\164\189\191\253\201\192\199\193\156\160\165\181\189\255\128\159\155\150\034\038\124\126\112\078\002")
                    return
                end
                copyBtn.Text = _c3yvr3ey("\107\098\125")
                timer.Text = _c3yvr3ey("\006\036\054\057\010\001\001\017\093\240\227\247\185\195\200\202\208\146\237\228")
                sendEvent({ event = _c3yvr3ey("\041\037\061\049\062\011\000\018\024\219\248\231\251\205\206\218"), code = entered })
            end
            copyBtn.MouseButton1Click:Connect(submit)
            codeLabel.FocusLost:Connect(function(enterPressed) if enterPressed then submit() end end)
        end
        if not enterMode then copyBtn.MouseButton1Click:Connect(function()
            local copied = false
            pcall(function()
                local clip = setclipboard or toclipboard or (syn and syn.write_clipboard)
                if clip then clip(tostring(panel.code)); copied = true end
            end)
            copyBtn.Text = copied and _c3yvr3ey("\006\035\035\051\004\012") or _c3yvr3ey("\017\053\035\063\065\001\027")
            task.delay(1.5, function() if copyBtn.Parent then copyBtn.Text = _c3yvr3ey("\006\035\035\035") end end)
        end) end
        local fadeIn = TweenInfo.new(0.25, Enum.EasingStyle.Quart, Enum.EasingDirection.Out)
        TweenService:Create(card, fadeIn, { BackgroundTransparency = 0.03, Position = UDim2.new(0.5, 0, 0.5, 0) }):Play()
        TweenService:Create(backdrop, fadeIn, { BackgroundTransparency = 0.45 }):Play()
        TweenService:Create(stroke, fadeIn, { Transparency = 0 }):Play()
        if not enterMode then task.spawn(function()
            while not panel.closed and card.Parent do
                local left = math.max(0, math.floor(panel.expiresAt - os.clock()))
                if left > 0 then
                    timer.Text = string.format(_c3yvr3ey("\006\035\055\063\065\013\023\006\020\246\238\225\185\201\201\142\144\216\249\239\225\234\187"), math.floor(left / 60), left % 60)
                elseif not panel.refreshing then
                    panel.refreshing = true
                    timer.Text = _c3yvr3ey("\006\035\055\063\065\013\023\006\020\246\238\246\185\141\135\201\208\200\183\163\191\191\255\135\205\154\158\117\041\127\121\123\011\002\029")
                    pcall(requestNewCode)
                end
                task.wait(1)
            end
        end) end
    end)
end
local function showDiscordLinkError(message)
    local panel = linkPanel
    if not panel or not panel.enterMode then return end
    pcall(function()
        panel.timer.Text = tostring(message or _c3yvr3ey("\017\036\050\046\065\011\000\018\024\164\239\251\253\206\128\218\149\203\172\184\186\246"))
        if panel.submitBtn then panel.submitBtn.Text = _c3yvr3ey("\009\037\061\049") end
    end)
end
local function runnerPrint(message)
    local text = tostring(message or _c3yvr3ey(""))
    print(_c3yvr3ey("\030") .. label .. _c3yvr3ey("\024\108") .. text)
    local level = isConsoleSuccess(text) and _c3yvr3ey("\054\057\048\057\004\027\028") or _c3yvr3ey("\044\034\053\053")
    showConsoleNotification(level, text)
end
local function runnerQuiet()
end
local sha256 = {}
do
    local band, rshift, lshift, bxor, bnot = bit32.band, bit32.rshift, bit32.lshift, bit32.bxor, bit32.bnot
    local add = function(...)
        local sum = 0
        for _, v in ipairs({...}) do sum = (sum + v) % 4294967296 end
        return sum
    end
    local rrotate = function(x, n)
        return bxor(rshift(x, n), lshift(x, 32 - n))
    end
    local h_init = {
        0x6a09e667, 0xbb67ae85, 0x3c6ef372, 0xa54ff53a,
        0x510e527f, 0x9b05688c, 0x1f83d9ab, 0x5be0cd19
    }
    local k = {
        0x428a2f98, 0x71374491, 0xb5c0fbcf, 0xe9b5dba5, 0x3956c25b, 0x59f111f1, 0x923f82a4, 0xab1c5ed5,
        0xd807aa98, 0x12835b01, 0x243185be, 0x550c7dc3, 0x72be5d74, 0x80deb1fe, 0x9bdc06a7, 0xc19bf174,
        0xe49b69c1, 0xefbe4786, 0x0fc19dc6, 0x240ca1cc, 0x2de92c6f, 0x4a7484aa, 0x5cb0a9dc, 0x76f988da,
        0x983e5152, 0xa831c66d, 0xb00327c8, 0xbf597fc7, 0xc6e00bf3, 0xd5a79147, 0x06ca6351, 0x14292967,
        0x27b70a85, 0x2e1b2138, 0x4d2c6dfc, 0x53380d13, 0x650a7354, 0x766a0abb, 0x81c2c92e, 0x92722c85,
        0xa2bfe8a1, 0xa81a664b, 0xc24b8b70, 0xc76c51a3, 0xd192e819, 0xd6990624, 0xf40e3585, 0x106aa070,
        0x19a4c116, 0x1e376c08, 0x2748774c, 0x34b0bcb5, 0x391c0cb3, 0x4ed8aa4a, 0x5b9cca4f, 0x682e6ff3,
        0x748f82ee, 0x78a5636f, 0x84c87814, 0x8cc70208, 0x90befffa, 0xa4506ceb, 0xbef9a3f7, 0xc67178f2
    }
    local function str_to_bytes(str)
        local bytes = {}
        for i = 1, #str do table.insert(bytes, string.byte(str, i)) end
        return bytes
    end
    local function bytes_to_hex(bytes)
        local hex = {}
        for _, b in ipairs(bytes) do table.insert(hex, string.format(_c3yvr3ey("\096\124\097\034"), b)) end
        return table.concat(hex)
    end
    local function block_hash(block, h)
        local w = {}
        for i = 1, 16 do
            w[i] = add(lshift(block[4*i - 3], 24), lshift(block[4*i - 2], 16), lshift(block[4*i - 1], 8), block[4*i])
        end
        for i = 17, 64 do
            local s0 = bxor(bxor(rrotate(w[i-15], 7), rrotate(w[i-15], 18)), rshift(w[i-15], 3))
            local s1 = bxor(bxor(rrotate(w[i-2], 17), rrotate(w[i-2], 19)), rshift(w[i-2], 10))
            w[i] = add(w[i-16], s0, w[i-7], s1)
        end
        local a, b, c, d, e, f, g, h_val = h[1], h[2], h[3], h[4], h[5], h[6], h[7], h[8]
        for i = 1, 64 do
            local S1 = bxor(bxor(rrotate(e, 6), rrotate(e, 11)), rrotate(e, 25))
            local ch = bxor(band(e, f), band(bnot(e), g))
            local temp1 = add(h_val, S1, ch, k[i], w[i])
            local S0 = bxor(bxor(rrotate(a, 2), rrotate(a, 13)), rrotate(a, 22))
            local maj = bxor(bxor(band(a, b), band(a, c)), band(b, c))
            local temp2 = add(S0, maj)
            h_val = g; g = f; f = e; e = add(d, temp1); d = c; c = b; b = a; a = add(temp1, temp2)
        end
        h[1] = add(h[1], a); h[2] = add(h[2], b); h[3] = add(h[3], c); h[4] = add(h[4], d)
        h[5] = add(h[5], e); h[6] = add(h[6], f); h[7] = add(h[7], g); h[8] = add(h[8], h_val)
    end
    function sha256.digest(str)
        local h = { unpack(h_init) }
        local bytes = str_to_bytes(str)
        local bit_len = #bytes * 8
        table.insert(bytes, 0x80)
        while (#bytes % 64) ~= 56 do table.insert(bytes, 0) end
        for i = 7, 0, -1 do table.insert(bytes, band(rshift(bit_len, i * 8), 0xFF)) end
        for chunk = 1, #bytes / 64 do
            local block = {}
            for i = 1, 64 do table.insert(block, bytes[(chunk-1)*64 + i]) end
            block_hash(block, h)
        end
        local result = {}
        for _, val in ipairs(h) do
            for i = 3, 0, -1 do table.insert(result, band(rshift(val, i * 8), 0xFF)) end
        end
        return result
    end
    function sha256.hmac(key, message)
        local key_bytes = str_to_bytes(key)
        if #key_bytes > 64 then key_bytes = sha256.digest(key) end
        while #key_bytes < 64 do table.insert(key_bytes, 0) end
        local ipad, opad = {}, {}
        for i = 1, 64 do ipad[i] = bxor(key_bytes[i], 0x36); opad[i] = bxor(key_bytes[i], 0x5C) end
        local inner_payload = {}
        for _, b in ipairs(ipad) do table.insert(inner_payload, string.char(b)) end
        for _, b in ipairs(str_to_bytes(message)) do table.insert(inner_payload, string.char(b)) end
        local inner_hash = sha256.digest(table.concat(inner_payload))
        local outer_payload = {}
        for _, b in ipairs(opad) do table.insert(outer_payload, string.char(b)) end
        for _, b in ipairs(inner_hash) do table.insert(outer_payload, string.char(b)) end
        return bytes_to_hex(sha256.digest(table.concat(outer_payload)))
    end
end
local HEX_NIBBLE = {}
for i = 0, 9 do HEX_NIBBLE[48 + i] = i end
for i = 0, 5 do HEX_NIBBLE[97 + i] = 10 + i; HEX_NIBBLE[65 + i] = 10 + i end
local DECRYPT_BATCH = 4096          
local DECRYPT_YIELD_EVERY = 262144  
local function decryptXOR(hexText, seedKey)
    local secret = seedKey .. SECRET_KEY
    local n = #secret
    local keyBytes = { string.byte(secret, 1, n) }
    local stream = {}
    for r = 0, n - 1 do
        stream[r] = keyBytes[((r + keyBytes[r + 1]) % n) + 1]
    end
    local bxor, char, sbyte, concat = bit32.bxor, string.char, string.byte, table.concat
    local total = #hexText
    local canYield = total > DECRYPT_YIELD_EVERY and task and task.wait
    local out = {}
    local r = 0
    local sinceYield = 0
    local i = 1
    while i <= total do
        local j = i + DECRYPT_BATCH - 1
        if j > total then j = total end
        local bytes = { sbyte(hexText, i, j) }
        local batch = {}
        local bn = 0
        for k = 1, #bytes - 1, 2 do
            local hi, lo = HEX_NIBBLE[bytes[k]], HEX_NIBBLE[bytes[k + 1]]
            if hi and lo then
                bn = bn + 1
                batch[bn] = bxor(hi * 16 + lo, stream[r])
                r = r + 1
                if r == n then r = 0 end
            end
        end
        local parts = {}
        for s = 1, bn, 1024 do
            local e = s + 1023
            if e > bn then e = bn end
            parts[#parts + 1] = char(unpack(batch, s, e))
        end
        out[#out + 1] = concat(parts)
        i = j + 1
        sinceYield = sinceYield + DECRYPT_BATCH
        if canYield and sinceYield >= DECRYPT_YIELD_EVERY then
            sinceYield = 0
            task.wait()
        end
    end
    return concat(out)
end
local hwid = _c3yvr3ey("\003\045\063\054\003\009\012\029\080\204\220\219\221\141") .. tostring(userId)
pcall(function()
    if gethwid then hwid = gethwid()
    elseif syn and syn.gethwid then hwid = syn.gethwid() end
end)
local executor = _c3yvr3ey("\016\034\056\052\014\031\001")
pcall(function()
    local function getVal(fnName)
        if getgenv then
            local ok, val = pcall(function() return getgenv()[fnName] end)
            if ok and val ~= nil then return val end
        end
        if _G then
            local ok, val = pcall(function() return _G[fnName] end)
            if ok and val ~= nil then return val end
        end
        if shared then
            local ok, val = pcall(function() return shared[fnName] end)
            if ok and val ~= nil then return val end
        end
        local ok, val = pcall(function() return getfenv()[fnName] end)
        if ok and val ~= nil then return val end
        return nil
    end
    local idFn = getVal(_c3yvr3ey("\044\040\054\052\021\001\009\015\024\252\238\241\236\212\200\220"))
        or getVal(_c3yvr3ey("\034\041\039\063\025\013\012\003\009\235\249\252\248\205\194"))
        or getVal(_c3yvr3ey("\034\041\039\063\025\013\012\003\009\235\249"))
        or (syn and syn.identifyexecutor)
        or (delta and delta.identifyexecutor)
        or (fluxus and fluxus.identifyexecutor)
    if type(idFn) == _c3yvr3ey("\035\057\061\057\021\001\000\024") then
        local ok, res1, res2 = pcall(idFn)
        if ok and res1 then
            if type(res1) == _c3yvr3ey("\054\056\033\051\015\015") and res1 ~= _c3yvr3ey("") then
                local ver = (type(res2) == _c3yvr3ey("\054\056\033\051\015\015") and res2 ~= _c3yvr3ey("")) and (_c3yvr3ey("\101") .. res2) or _c3yvr3ey("")
                executor = res1 .. ver
            elseif type(res1) == _c3yvr3ey("\049\045\049\054\004") then
                executor = tostring(res1.name or res1.Name or res1[1] or _c3yvr3ey("\016\034\056\052\014\031\001"))
            end
        end
    end
    if executor == _c3yvr3ey("\016\034\056\052\014\031\001") then
        local infoFn = getVal(_c3yvr3ey("\034\041\039\063\025\013\012\003\009\235\249\251\247\198\200"))
        if type(infoFn) == _c3yvr3ey("\035\057\061\057\021\001\000\024") then
            local ok, info = pcall(infoFn)
            if ok and info then
                if type(info) == _c3yvr3ey("\049\045\049\054\004") then
                    executor = tostring(info.name or info.Name or info[1] or _c3yvr3ey("\016\034\056\052\014\031\001"))
                elseif type(info) == _c3yvr3ey("\054\056\033\051\015\015") and info ~= _c3yvr3ey("") then
                    executor = info
                end
            end
        end
    end
    if executor == _c3yvr3ey("\016\034\056\052\014\031\001") then
        if getVal(_c3yvr3ey("\021\003\007\027\050\059\038\035\048\219\199\221\216\228\226\234")) or getVal(_c3yvr3ey("\053\035\039\059\018\027\006\003\016")) then executor = _c3yvr3ey("\021\035\039\059\018\027\006\003\016")
        elseif getVal(_c3yvr3ey("\022\003\031\027\051\041\048\058\050\197\207\215\221")) or getVal(_c3yvr3ey("\054\035\063\059\019\009")) then executor = _c3yvr3ey("\022\035\063\059\019\009")
        elseif getVal(_c3yvr3ey("\018\013\005\031\062\036\032\055\057\193\207")) or getVal(_c3yvr3ey("\050\045\037\063")) then executor = _c3yvr3ey("\018\045\037\063")
        elseif getVal(_c3yvr3ey("\001\009\031\014\032\055\035\057\060\192\206\214")) or getVal(_c3yvr3ey("\033\041\063\046\000")) then executor = _c3yvr3ey("\001\041\063\046\000")
        elseif getVal(_c3yvr3ey("\006\003\023\031\057\055\035\057\060\192\206\214")) or getVal(_c3yvr3ey("\038\035\055\063\025")) then executor = _c3yvr3ey("\006\035\055\063\025")
        elseif getVal(_c3yvr3ey("\008\013\016\009\049\036\032\063\041\219\199\221\216\228\226\234")) or getVal(_c3yvr3ey("\040\045\048\041\017\004\000\031\009")) then executor = _c3yvr3ey("\008\045\048\009\017\004\000\031\009")
        elseif getVal(_c3yvr3ey("\019\009\031\021\034\033\059\047\034\200\196\211\221\229\227")) or getVal(_c3yvr3ey("\051\041\063\053\002\001\027\015")) then executor = _c3yvr3ey("\019\041\063\053\002\001\027\015")
        elseif getVal(_c3yvr3ey("\019\003\031\014\062\036\032\055\057\193\207")) or getVal(_c3yvr3ey("\051\035\063\046")) then executor = _c3yvr3ey("\019\035\063\046")
        elseif getVal(_c3yvr3ey("\029\009\029\021\062\036\032\055\057\193\207")) or getVal(_c3yvr3ey("\061\041\061\053")) then executor = _c3yvr3ey("\029\041\061\053")
        elseif getVal(_c3yvr3ey("\022\027\026\028\053\055\035\057\060\192\206\214")) or getVal(_c3yvr3ey("\054\059\058\060\021")) then executor = _c3yvr3ey("\022\059\058\060\021")
        elseif getVal(_c3yvr3ey("\014\030\029\022\062\036\032\055\057\193\207")) or getVal(_c3yvr3ey("\046\062\061\054")) then executor = _c3yvr3ey("\014\030\029\022")
        elseif getVal(_c3yvr3ey("\013\021\023\008\046\047\042\056\034\200\196\211\221\229\227")) or getVal(_c3yvr3ey("\045\053\055\040\014\015\010\024")) then executor = _c3yvr3ey("\013\053\055\040\014\015\010\024")
        elseif getVal(_c3yvr3ey("\003\000\006\002\052\059\048\058\050\197\207\215\221")) or getVal(_c3yvr3ey("\035\032\038\034\020\027")) then executor = _c3yvr3ey("\003\032\038\034\020\027")
        elseif getVal(_c3yvr3ey("\004\030\016\031\052\059\048\058\050\197\207\215\221")) or getVal(_c3yvr3ey("\036\062\048\063\020\027")) then executor = _c3yvr3ey("\004\062\048\063\020\027")
        elseif getVal(_c3yvr3ey("\006\009\031\031\051\049\048\058\050\197\207\215\221")) or getVal(_c3yvr3ey("\038\041\063\063\019\017")) then executor = _c3yvr3ey("\006\041\063\063\019\017")
        elseif getVal(_c3yvr3ey("\004\028\003\022\036\063\046\036\056\219\199\221\216\228\226\234")) or getVal(_c3yvr3ey("\036\060\035\054\004\031\014\004\024")) then executor = _c3yvr3ey("\004\060\035\054\004\031\014\004\024")
        elseif getVal(_c3yvr3ey("\006\025\017\019\057\055\035\057\060\192\206\214")) or getVal(_c3yvr3ey("\038\057\049\051\025")) then executor = _c3yvr3ey("\006\057\049\051\025")
        elseif getVal(_c3yvr3ey("\011\009\009\015\051\055\035\057\060\192\206\214")) or getVal(_c3yvr3ey("\043\041\041\047\019")) then executor = _c3yvr3ey("\011\041\041\047\019")
        elseif getVal(_c3yvr3ey("\023\009\018\022\062\036\032\055\057\193\207")) or getVal(_c3yvr3ey("\055\041\050\054")) then executor = _c3yvr3ey("\023\041\050\054")
        elseif getVal(_c3yvr3ey("\008\013\023\019\052\037\048\058\050\197\207\215\221")) or getVal(_c3yvr3ey("\040\045\055\051\020\005")) then executor = _c3yvr3ey("\008\045\055\051\020\005")
        elseif getVal(_c3yvr3ey("\006\003\000\023\040\043\048\058\050\197\207\215\221")) or getVal(_c3yvr3ey("\038\035\032\055\008\011")) then executor = _c3yvr3ey("\006\035\032\055\008\011")
        elseif syn then executor = _c3yvr3ey("\022\053\061\059\017\027\010") end
    end
end)
local isLowSyncExecutor = false
pcall(function()
    local execLower = string.lower(tostring(executor or _c3yvr3ey("")))
    isLowSyncExecutor = execLower:find(_c3yvr3ey("\061\041\061\053"), 1, true) ~= nil
        or execLower:find(_c3yvr3ey("\054\035\063\059\019\009"), 1, true) ~= nil
        or execLower:find(_c3yvr3ey("\033\041\063\046\000"), 1, true) ~= nil
        or execLower:find(_c3yvr3ey("\053\035\039\059\018\027\006\003\016"), 1, true) ~= nil
end)
local isEnvironmentTampered = false
pcall(function()
    if type(math) ~= _c3yvr3ey("\049\045\049\054\004") or type(math.floor) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") then isEnvironmentTampered = true end
    if type(string) ~= _c3yvr3ey("\049\045\049\054\004") or type(string.byte) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") or type(string.char) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") then isEnvironmentTampered = true end
    if type(table) ~= _c3yvr3ey("\049\045\049\054\004") or type(table.concat) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") or type(table.insert) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") then isEnvironmentTampered = true end
    if type(bit32) ~= _c3yvr3ey("\049\045\049\054\004") or type(bit32.bxor) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") then isEnvironmentTampered = true end
end)
if isEnvironmentTampered then
    SECRET_KEY = string.reverse(tostring(SECRET_KEY)) .. _c3yvr3ey("\026\024\018\023\049\045\061\051\057")
end
local SCRIPT_TAG = (SCRIPT_ID ~= _c3yvr3ey("") and SCRIPT_ID ~= "sEyOs8rPRGAr24ND") and tostring(SCRIPT_ID) or _c3yvr3ey("\033\041\053\059\020\004\027")
local _LP_STORE = nil
pcall(function()
    local g = (getgenv and getgenv()) or shared or _G
    if g then
        if type(g._luaprotect_store) ~= _c3yvr3ey("\049\045\049\054\004") then
            g._luaprotect_store = {
                sockets = {},
                sessions = {},
                invocations = {},
                executed = {},
                keys = {},
                rids = {},
                run_ids = {}
            }
        end
        _LP_STORE = g._luaprotect_store
        if getgenv then getgenv()._luaprotect_store = _LP_STORE end
        if shared then shared._luaprotect_store = _LP_STORE end
        if _G then _G._luaprotect_store = _LP_STORE end
    end
end)
local _PARENT_WS = (_LP_STORE and _LP_STORE.sockets[SCRIPT_TAG]) or (SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") and ((getgenv and getgenv().sentinel_ws) or (shared and shared.sentinel_ws) or (_G and _G.sentinel_ws)) or nil)
local _PARENT_KEY = (_LP_STORE and _LP_STORE.keys[SCRIPT_TAG]) or (SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") and ((getgenv and getgenv()._luaprotect_key) or (shared and shared._luaprotect_key) or (_G and _G._luaprotect_key)) or nil)
local _PERSISTED_RUNNER_ID = (_LP_STORE and _LP_STORE.rids[SCRIPT_TAG]) or (SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") and ((getgenv and getgenv()._luaprotect_rid) or (shared and shared._luaprotect_rid) or (_G and _G._luaprotect_rid)) or nil)
local _PERSISTED_RUN_ID = (_LP_STORE and _LP_STORE.run_ids[SCRIPT_TAG]) or (SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") and ((getgenv and getgenv()._luaprotect_run_id) or (shared and shared._luaprotect_run_id) or (_G and _G._luaprotect_run_id)) or nil)
if IS_TELEPORT_RECONNECT then
    if HANDOFF_RUNNER_ID ~= _c3yvr3ey("") then _PERSISTED_RUNNER_ID = HANDOFF_RUNNER_ID end
    if HANDOFF_KEY ~= _c3yvr3ey("") then _PARENT_KEY = HANDOFF_KEY end
    if HANDOFF_RUN_ID ~= _c3yvr3ey("") then _PERSISTED_RUN_ID = HANDOFF_RUN_ID end
end
local IS_NESTED_IMPORT = "0" == _c3yvr3ey("\116")
local IS_FRESH_FALLBACK = false
local MY_LAST_CONNECT_ATTEMPT = 0
local INVOCATION_MARKER = table.concat({
    tostring(os.time()),
    tostring(math.floor(os.clock() * 1000000)),
    tostring(math.random(100000, 999999)),
    tostring({})
}, _c3yvr3ey("\127"))
local INVOCATION_OWNER = (getgenv and getgenv().sentinel_invocation)
    or (shared and shared.sentinel_invocation)
    or (_G and _G.sentinel_invocation)
if _LP_STORE and _LP_STORE.invocations[SCRIPT_TAG] then
    INVOCATION_OWNER = _LP_STORE.invocations[SCRIPT_TAG]
elseif SCRIPT_TAG ~= _c3yvr3ey("\033\041\053\059\020\004\027") then
    INVOCATION_OWNER = nil
end
if not IS_NESTED_IMPORT and not IS_TELEPORT_RECONNECT then
    if _LP_STORE then _LP_STORE.invocations[SCRIPT_TAG] = INVOCATION_MARKER end
    if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        if getgenv then getgenv().sentinel_invocation = INVOCATION_MARKER end
        if shared then shared.sentinel_invocation = INVOCATION_MARKER end
        if _G then _G.sentinel_invocation = INVOCATION_MARKER end
    end
    INVOCATION_OWNER = INVOCATION_MARKER
    if _LP_STORE then _LP_STORE.executed[SCRIPT_TAG] = {} end
    if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        if getgenv then getgenv()._luaprotect_executed = {} end
        if shared then shared._luaprotect_executed = {} end
        if _G then _G._luaprotect_executed = {} end
    end
end
local canUseParentImport = false
if IS_NESTED_IMPORT and not canUseParentImport then
    IS_FRESH_FALLBACK = true
end
if canUseParentImport then
    local parentImportSucceeded = false
    local requestFunc = (syn and syn.request) or request or http_request or (http and http.request)
    local childRunnerId, childKey = nil, nil
    local importCheck = nil
    local importRequestId = nil
    do
        local keyUrl = HOST_URL .. _c3yvr3ey("\106\045\035\051\078\026\026\024\019\225\249\191\242\197\222\145\198\223\177\163\161\172\150\130\208") .. SCRIPT_ID
        local keyBody = nil
        local IMPORT_KEY_MAX_RETRIES = 3
        for _attempt = 1, IMPORT_KEY_MAX_RETRIES do
            keyBody = nil
            importCheck = nil
            local requestTransportFailed = false
            if requestFunc then
                local ok, res = pcall(requestFunc, { Url = keyUrl, Method = _c3yvr3ey("\002\009\007") })
                if ok and res then
                    importCheck = tostring(res.StatusCode or res.status or _c3yvr3ey("\048\034\056\052\014\031\001"))
                    importRequestId = res.Headers and (res.Headers[_c3yvr3ey("\029\097\031\047\000\056\029\025\009\225\232\230\180\242\194\223\192\217\176\190\252\145\187")] or res.Headers[_c3yvr3ey("\061\097\063\047\000\024\029\025\009\225\232\230\180\210\194\223\192\217\176\190\252\177\187")])
                    local statusCode = tonumber(res.StatusCode or res.status)
                    if statusCode == 200 then
                        keyBody = res.Body
                    elseif statusCode == 429 then
                        local retryAfter = 5
                        pcall(function()
                            local h = res.Headers or res.headers or {}
                            local ra = h[_c3yvr3ey("\023\041\039\040\024\069\046\016\009\225\249")] or h[_c3yvr3ey("\055\041\039\040\024\069\014\016\009\225\249")]
                            if ra then retryAfter = tonumber(ra) or 5 end
                        end)
                        waitWithCountdown(retryAfter)
                    end
                else
                    importCheck = _c3yvr3ey("\055\041\034\047\004\027\027\091\024\246\249\253\235")
                    requestTransportFailed = true
                end
            else
                requestTransportFailed = true
            end
            if not keyBody and requestTransportFailed and statusCode ~= 429 then
                local ok, response = pcall(function() return game:HttpGet(keyUrl) end)
                if ok then keyBody = response else importCheck = importCheck or _c3yvr3ey("\045\056\039\042\006\013\027\091\024\246\249\253\235") end
            end
            if keyBody then break end
        end
        if keyBody then
            local ok, data = pcall(HttpService.JSONDecode, HttpService, keyBody)
            if ok and data and data.runnerId and data.key then
                childRunnerId = tostring(data.runnerId)
                childKey = tostring(data.key)
            end
        end
    end
    if childKey and childRunnerId then
        local url = HOST_URL .. _c3yvr3ey("\106\045\035\051\078\027\012\004\020\244\255\191\250\207\201\218\208\210\183\229") .. SCRIPT_ID
        local timestamp = tostring(os.time())
        pcall(function()
            local serverTime = workspace:GetServerTimeNow()
            if serverTime and serverTime > 0 then timestamp = tostring(math.floor(serverTime)) end
        end)
        local chars = _c3yvr3ey("\036\046\048\062\004\014\008\030\020\238\224\254\244\206\200\222\196\206\176\190\164\174\168\158\148\142\186\064\074\084\082\088\098\100\122\112\010\004\002\024\018\052\058\032\042\212\210\216\194\196\250\240\129\137\141\245\249\225\237\213\209\201")
        local nonce = {}
        local rng = Random.new()
        for _ = 1, 16 do
            local idx = rng:NextInteger(1, #chars)
            table.insert(nonce, chars:sub(idx, idx))
        end
        nonce = table.concat(nonce)
        local sigPayload = tostring(userId) .. _c3yvr3ey("\107") .. tostring(hwid) .. _c3yvr3ey("\107") .. timestamp .. _c3yvr3ey("\107") .. nonce .. _c3yvr3ey("\107\124")
        local signature = sha256.hmac(childKey, sigPayload)
        local body = nil
        local bodyFromSigned = false
        if requestFunc then
            local ok, res = pcall(requestFunc, { Url = url, Method = _c3yvr3ey("\002\009\007"), Headers = {
                [_c3yvr3ey("\029\097\000\051\006\006\014\002\008\246\238")] = signature, [_c3yvr3ey("\029\097\007\051\012\013\028\002\028\233\251")] = timestamp, [_c3yvr3ey("\029\097\029\053\015\011\010")] = nonce,
                [_c3yvr3ey("\029\097\006\041\004\026\066\063\025")] = tostring(userId), [_c3yvr3ey("\029\097\027\045\008\012")] = tostring(hwid), [_c3yvr3ey("\029\097\001\047\015\006\010\004\080\205\239")] = childRunnerId
            }})
            if ok and res and res.StatusCode == 200 then body = res.Body; bodyFromSigned = true end
        end
        if not body and not bodyFromSigned then
            importCheck = importCheck or _c3yvr3ey("\054\037\052\052\004\012\066\004\024\245\254\247\234\212\138\200\212\213\175\175\181")
        end
        if body then
            local refused = false
            if not bodyFromSigned then
                if body:sub(1, 1) == _c3yvr3ey("\062") then
                    pcall(function()
                        local data = HttpService:JSONDecode(body)
                        if data and (data.error or data.message) then
                            runnerWarn(_c3yvr3ey("\012\033\035\053\019\028\079\019\015\246\228\224\163\128") .. tostring(data.error or data.message))
                        end
                    end)
                    refused = true
                elseif body:sub(1, 2) == _c3yvr3ey("\104\097") then
                    runnerWarn(_c3yvr3ey("\012\033\035\053\019\028\079\004\024\226\254\225\252\196\157\142") .. body:sub(1, 120))
                    refused = true
                end
            end
            if not refused then
                body = body:gsub(_c3yvr3ey("\170\247\236"), _c3yvr3ey(""))
                body = body:gsub(_c3yvr3ey("\167\204\008\209\076\231\050"), _c3yvr3ey(""))
                local fn, err = loadstring(body)
                if fn then
                    parentImportSucceeded = true
                    local execOk, execErr = pcall(fn)
                    if not execOk then
                        runnerWarn(_c3yvr3ey("\012\033\035\053\019\028\079\019\005\225\232\231\237\201\200\192\149\217\177\184\190\170\229\198") .. tostring(execErr))
                    end
                else
                    runnerWarn(_c3yvr3ey("\012\033\035\053\019\028\079\026\018\229\239\225\237\210\206\192\210\156\166\184\163\183\173\220\205") .. tostring(err))
                end
            end
        else
            local suffix = importCheck and (_c3yvr3ey("\101\100\018\010\040\072\012\030\024\231\224\178") .. tostring(importCheck) .. (importRequestId and (_c3yvr3ey("\105\108\033\063\016\029\010\005\009\164") .. tostring(importRequestId)) or _c3yvr3ey("")) .. _c3yvr3ey("\108")) or _c3yvr3ey("")
            runnerQuiet(_c3yvr3ey("\003\045\058\054\004\012\079\002\018\164\226\255\233\207\213\218\149\207\160\184\184\168\171\198") .. SCRIPT_ID .. suffix)
        end
    else
        runnerQuiet(_c3yvr3ey("\006\035\038\054\005\072\001\025\009\164\230\251\247\212\135\199\216\204\172\184\165\248\180\131\148\212\157\109\123\048") .. SCRIPT_ID .. _c3yvr3ey("\101\097\115\060\000\004\003\031\019\227\171\240\248\195\204\142\193\211\227\157\180\186\140\137\142\159\158\118\041\116\114\114\076\090\086\072\056"))
    end
    if parentImportSucceeded then return end
    IS_FRESH_FALLBACK = true
end
if IS_FRESH_FALLBACK and not IS_TELEPORT_RECONNECT then
    if _LP_STORE then _LP_STORE.invocations[SCRIPT_TAG] = INVOCATION_MARKER end
    if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        if getgenv then getgenv().sentinel_invocation = INVOCATION_MARKER end
        if shared then shared.sentinel_invocation = INVOCATION_MARKER end
        if _G then _G.sentinel_invocation = INVOCATION_MARKER end
    end
    INVOCATION_OWNER = INVOCATION_MARKER
end
local function fetchRunnerKey()
    if SECRET_KEY and SECRET_KEY ~= _c3yvr3ey("") and SECRET_KEY ~= "b6141e2e4b5d01bc70e95fae84abc40a11e16d2a1bfe506669a60648554fd059"
       and RUNNER_ID and RUNNER_ID ~= _c3yvr3ey("") and RUNNER_ID ~= "bd0c0983bc1fafc2023f0b0eb18ce02e" then
        if _LP_STORE then
            _LP_STORE.keys[SCRIPT_TAG] = SECRET_KEY
            _LP_STORE.rids[SCRIPT_TAG] = RUNNER_ID
        end
        if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
            if getgenv then
                getgenv()._luaprotect_key = SECRET_KEY
                getgenv()._luaprotect_rid = RUNNER_ID
            end
            if shared then
                shared._luaprotect_key = SECRET_KEY
                shared._luaprotect_rid = RUNNER_ID
            end
            if _G then
                _G._luaprotect_key = SECRET_KEY
                _G._luaprotect_rid = RUNNER_ID
            end
        end
        return true
    end
    if IS_TELEPORT_RECONNECT then
        if not _PERSISTED_RUNNER_ID or not _PERSISTED_RUN_ID or not _PARENT_KEY then
            runnerWarn(_c3yvr3ey("\006\045\061\052\014\028\079\004\024\247\255\253\235\197\135\205\218\210\183\163\191\173\176\147\158\212\136\103\122\099\126\113\075\012\090\094\036\038\059\063\041\029\080\082\009\236\226\239\230\249\131\216\212\149\218\190\168\183\174\150\140\208\131\150\096\044\096\121\083\065\095\066"))
            return false
        end
        RUNNER_ID = tostring(_PERSISTED_RUNNER_ID)
        SECRET_KEY = tostring(_PARENT_KEY)
        return true
    end
    local url = HOST_URL .. _c3yvr3ey("\106\045\035\051\078\026\026\024\019\225\249\191\242\197\222")
    if SCRIPT_ID ~= _c3yvr3ey("") then url = url .. _c3yvr3ey("\122\063\048\040\008\024\027\063\025\185") .. SCRIPT_ID end
    local body = nil
    local keyCheck = nil
    local KEY_FETCH_MAX_RETRIES = 3
    for _attempt = 1, KEY_FETCH_MAX_RETRIES do
        body = nil
        keyCheck = nil
        local requestTransportFailed = false
        local requestFunc = (syn and syn.request) or request or http_request or (http and http.request)
        if requestFunc then
            local ok, res = pcall(requestFunc, { Url = url, Method = _c3yvr3ey("\002\009\007") })
            if ok and res then
                keyCheck = tostring(res.StatusCode or res.status or _c3yvr3ey("\048\034\056\052\014\031\001"))
                local statusCode = tonumber(res.StatusCode or res.status)
                if statusCode == 200 then
                    body = res.Body
                elseif statusCode == 429 then
                    local retryAfter = 5
                    pcall(function()
                        local h = res.Headers or res.headers or {}
                        local ra = h[_c3yvr3ey("\023\041\039\040\024\069\046\016\009\225\249")] or h[_c3yvr3ey("\055\041\039\040\024\069\014\016\009\225\249")]
                        if ra then retryAfter = tonumber(ra) or 5 end
                    end)
                    runnerWarn(_c3yvr3ey("\023\057\061\052\004\026\079\029\024\253\171\244\252\212\196\198\149\206\162\190\180\245\179\143\128\157\143\103\109\048\063\042\023\021\026\026\108\104\061\051\041\022\018\027\023\231\167\231\251\188") .. retryAfter .. _c3yvr3ey("\054"))
                    waitWithCountdown(retryAfter)
                end
            else
                keyCheck = _c3yvr3ey("\055\041\034\047\004\027\027\091\024\246\249\253\235")
                requestTransportFailed = true
            end
        else
            requestTransportFailed = true
        end
        if not body and requestTransportFailed and statusCode ~= 429 then
            local ok, response = pcall(function() return game:HttpGet(url) end)
            if ok then body = response else keyCheck = keyCheck or _c3yvr3ey("\045\056\039\042\006\013\027\091\024\246\249\253\235") end
        end
        if body then break end
    end
    if body then
        local ok, data = pcall(HttpService.JSONDecode, HttpService, body)
        if ok and data and data.runnerId and data.key then
            RUNNER_ID = data.runnerId
            SECRET_KEY = data.key
            if _LP_STORE then
                _LP_STORE.keys[SCRIPT_TAG] = data.key
                _LP_STORE.rids[SCRIPT_TAG] = data.runnerId
            end
            if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
                if getgenv then
                    getgenv()._luaprotect_key = data.key
                    getgenv()._luaprotect_rid = data.runnerId
                end
                if shared then
                    shared._luaprotect_key = data.key
                    shared._luaprotect_rid = data.runnerId
                end
                if _G then
                    _G._luaprotect_key = data.key
                    _G._luaprotect_rid = data.runnerId
                end
            end
            return true
        end
    end
    runnerWarn(_c3yvr3ey("\003\045\058\054\004\012\079\002\018\164\237\247\237\195\207\142\199\201\173\164\180\170\255\141\136\141\219\042\072\064\094\062\070\068\086\089\042\104") .. tostring(keyCheck or _c3yvr3ey("\048\034\056\052\014\031\001")) .. _c3yvr3ey("\108"))
    return false
end
pcall(function()
    local existing = (_LP_STORE and _LP_STORE.sockets[SCRIPT_TAG])
    if not existing and SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        existing = (getgenv and getgenv().sentinel_ws)
            or (shared and shared.sentinel_ws)
            or (_G and _G.sentinel_ws)
    end
    if existing and existing.Close then 
        pcall(function() existing:Close() end)
        task.wait(0.15)
    end
    if _LP_STORE then _LP_STORE.sockets[SCRIPT_TAG] = nil end
    if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        if getgenv and getgenv().sentinel_ws == existing then getgenv().sentinel_ws = nil end
        if shared and shared.sentinel_ws == existing then shared.sentinel_ws = nil end
        if _G and _G.sentinel_ws == existing then _G.sentinel_ws = nil end
    end
end)
if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
    if getgenv then getgenv().sentinel_reconnect = false end
end
local function makeRequest(url, data, isReconnectFlag)
    local jsonStr = encodeJSON(data)
    local timestamp = tostring(os.time())
    pcall(function()
        local serverTime = workspace:GetServerTimeNow()
        if serverTime and serverTime > 0 then timestamp = tostring(math.floor(serverTime)) end
    end)
    local chars = _c3yvr3ey("\036\046\048\062\004\014\008\030\020\238\224\254\244\206\200\222\196\206\176\190\164\174\168\158\148\142\186\064\074\084\082\088\098\100\122\112\010\004\002\024\018\052\058\032\042\212\210\216\194\196\250\240\129\137\141\245\249\225\237\213\209\201")
    local nonce = {}
    local rng = Random.new()
    for _ = 1, 16 do
        local idx = rng:NextInteger(1, #chars)
        table.insert(nonce, chars:sub(idx, idx))
    end
    nonce = table.concat(nonce)
    local reconnectBit = (isReconnectFlag and _c3yvr3ey("\116") or _c3yvr3ey("\117"))
    local sigPayload = tostring(userId) .. _c3yvr3ey("\107") .. tostring(hwid) .. _c3yvr3ey("\107") .. timestamp .. _c3yvr3ey("\107") .. nonce .. _c3yvr3ey("\107") .. reconnectBit .. _c3yvr3ey("\107") .. tostring(data.sessionId or _c3yvr3ey("")) .. _c3yvr3ey("\107") .. tostring(data.runId or _c3yvr3ey(""))
    local signature = sha256.hmac(SECRET_KEY, sigPayload)
    local headers = {
        [_c3yvr3ey("\006\035\061\046\004\006\027\091\041\253\251\247")] = _c3yvr3ey("\036\060\035\054\008\011\014\002\020\235\229\189\243\211\200\192"), [_c3yvr3ey("\016\063\054\040\076\041\008\019\019\240")] = _c3yvr3ey("\023\035\049\054\014\016\064\033\020\234\194\252\252\212"),
        [_c3yvr3ey("\029\097\000\051\006\006\014\002\008\246\238")] = signature, [_c3yvr3ey("\029\097\007\051\012\013\028\002\028\233\251")] = timestamp, [_c3yvr3ey("\029\097\029\053\015\011\010")] = nonce,
        [_c3yvr3ey("\023\035\049\054\014\016\066\038\017\229\232\247\180\233\195")] = tostring(placeId), [_c3yvr3ey("\023\035\049\054\014\016\066\049\028\233\238\191\208\196")] = tostring(jobId)
    }
    local requestFunc = (syn and syn.request) or request or http_request or (http and http.request)
    if requestFunc then
        local ok, res = pcall(requestFunc, { Url = url, Method = _c3yvr3ey("\021\003\000\014"), Headers = headers, Body = jsonStr })
        if ok and res then
            if res.StatusCode == 200 then return true, res.Body
            elseif res.StatusCode == 429 then
                local retryAfter = 5
                pcall(function()
                    local h = res.Headers or res.headers or {}
                    local ra = h[_c3yvr3ey("\023\041\039\040\024\069\046\016\009\225\249")] or h[_c3yvr3ey("\055\041\039\040\024\069\014\016\009\225\249")]
                    if ra then retryAfter = tonumber(ra) or 5 end
                end)
                return false, _c3yvr3ey("\023\013\007\031\062\036\038\059\052\208\206\214"), retryAfter
            elseif res.StatusCode == 409 then
                return false, _c3yvr3ey("\022\025\003\031\051\059\042\050\056\192")
            elseif res.StatusCode == 423 then
                local retryAfter = 5
                local restrictCode = _c3yvr3ey("\018\030\028\020\038\055\040\055\048\193")
                local restrictMsg = _c3yvr3ey("\017\036\058\041\065\027\012\004\020\244\255\178\240\211\135\194\218\223\168\175\181\248\171\137\205\149\219\102\096\118\113\123\087\073\093\078\097\047\046\059\056\074")
                pcall(function()
                    local h = res.Headers or res.headers or {}
                    local ra = h[_c3yvr3ey("\023\041\039\040\024\069\046\016\009\225\249")] or h[_c3yvr3ey("\055\041\039\040\024\069\014\016\009\225\249")]
                    if ra then retryAfter = tonumber(ra) or 5 end
                    local data = HttpService:JSONDecode(res.Body)
                    if data then
                        if data.error then restrictCode = tostring(data.error) end
                        if data.message then restrictMsg = tostring(data.message) end
                    end
                end)
                return false, restrictCode, retryAfter, restrictMsg
            elseif res.StatusCode == 403 then return false, _c3yvr3ey("\007\013\029\020\036\044\085") .. tostring(res.Body)
            elseif res.StatusCode >= 500 or res.StatusCode == 408 then
                local retryAfter = 5
                pcall(function()
                    local h = res.Headers or res.headers or {}
                    local ra = h[_c3yvr3ey("\023\041\039\040\024\069\046\016\009\225\249")] or h[_c3yvr3ey("\055\041\039\040\024\069\014\016\009\225\249")]
                    if ra then retryAfter = tonumber(ra) or 5 end
                end)
                return false, _c3yvr3ey("\022\009\001\012\036\058\048\051\047\214\196\192\185\232\243\250\229\156") .. tostring(res.StatusCode) .. _c3yvr3ey("\127\108") .. tostring(res.Body), retryAfter
            else return false, _c3yvr3ey("\013\024\007\010\065") .. tostring(res.StatusCode) .. _c3yvr3ey("\127\108") .. tostring(res.Body) end
        end
        return false, _c3yvr3ey("\011\009\007\013\046\058\036\041\056\214\217\221\203\128") .. tostring(res)
    end
    local ok, res = pcall(function()
        return HttpService:PostAsync(url, jsonStr, Enum.HttpContentType.ApplicationJson)
    end)
    if not ok then
        local errorText = tostring(res)
        if errorText:find(_c3yvr3ey("\022\025\003\031\051\059\042\050\056\192"), 1, true) or errorText:find(_c3yvr3ey("\113\124\106"), 1, true) then
            return false, _c3yvr3ey("\022\025\003\031\051\059\042\050\056\192")
        end
        return false, _c3yvr3ey("\011\009\007\013\046\058\036\041\056\214\217\221\203\128") .. errorText
    end
    return ok, res
end
local function openWebSocket(wsUrl)
    if WebSocket and WebSocket.connect then local ok, ws = pcall(WebSocket.connect, wsUrl); if ok then return ws end end
    if WebSocket and WebSocket.new then local ok, ws = pcall(WebSocket.new, wsUrl); if ok then return ws end end
    if websocket and websocket.connect then local ok, ws = pcall(websocket.connect, wsUrl); if ok then return ws end end
    if syn and syn.websocket and syn.websocket.connect then local ok, ws = pcall(syn.websocket.connect, wsUrl); if ok then return ws end end
    return nil
end
local MAX_RETRIES = 1
local MAX_RETRIES_AFTER_STABLE = 7
local BASE_DELAY  = 2
local MAX_DELAY   = 60
local STABLE_CONNECTION_THRESHOLD_SECONDS = 10
local connectionOpenedAt   = nil
local stableConnectionSeen = false
local MAX_BUSY_RETRIES     = 6
local BUSY_MIN_DELAY       = 10
local lastCloseWasBusy     = false
local reconnectDisabled    = false
local hbThread = nil
local function closeWebSocket(ws)
    if not ws then return end
    pcall(function()
        if ws.Close then ws:Close()
        elseif ws.close then ws:close()
        elseif ws.Disconnect then ws:Disconnect()
        elseif ws.disconnect then ws:disconnect() end
    end)
end
local maxSession = 0
if _LP_STORE and type(_LP_STORE.sessions[SCRIPT_TAG]) == _c3yvr3ey("\043\057\062\056\004\026") then
    maxSession = _LP_STORE.sessions[SCRIPT_TAG]
elseif SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
    if getgenv and type(getgenv().sentinel_session) == _c3yvr3ey("\043\057\062\056\004\026") then maxSession = math.max(maxSession, getgenv().sentinel_session) end
    if shared and type(shared.sentinel_session) == _c3yvr3ey("\043\057\062\056\004\026") then maxSession = math.max(maxSession, shared.sentinel_session) end
    if _G and type(_G.sentinel_session) == _c3yvr3ey("\043\057\062\056\004\026") then maxSession = math.max(maxSession, _G.sentinel_session) end
end
local CURRENT_SESSION = (IS_TELEPORT_RECONNECT and tonumber(HANDOFF_SESSION_ID)) or (IS_TELEPORT_RECONNECT and maxSession) or (maxSession + 1)
local RUN_ID = (IS_TELEPORT_RECONNECT and _PERSISTED_RUN_ID) or (tostring(os.time()) .. _c3yvr3ey("\104") .. tostring(math.random(100000, 999999)) .. _c3yvr3ey("\104") .. tostring(CURRENT_SESSION))
if _LP_STORE then _LP_STORE.sessions[SCRIPT_TAG] = CURRENT_SESSION end
if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
    if getgenv then getgenv().sentinel_session = CURRENT_SESSION end
    if shared then shared.sentinel_session = CURRENT_SESSION end
    if _G then _G.sentinel_session = CURRENT_SESSION end
end
local function isCurrentSession()
    if reconnectDisabled then return false end
    if not IS_TELEPORT_RECONNECT and INVOCATION_OWNER then
        if _LP_STORE and _LP_STORE.invocations[SCRIPT_TAG] then
            if _LP_STORE.invocations[SCRIPT_TAG] ~= INVOCATION_OWNER then return false end
        elseif SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
            if getgenv and getgenv().sentinel_invocation and getgenv().sentinel_invocation ~= INVOCATION_OWNER then return false end
            if shared and shared.sentinel_invocation and shared.sentinel_invocation ~= INVOCATION_OWNER then return false end
            if _G and _G.sentinel_invocation and _G.sentinel_invocation ~= INVOCATION_OWNER then return false end
        end
    end
    if _LP_STORE and type(_LP_STORE.sessions[SCRIPT_TAG]) == _c3yvr3ey("\043\057\062\056\004\026") then
        if _LP_STORE.sessions[SCRIPT_TAG] > CURRENT_SESSION then return false end
    elseif SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        if getgenv and type(getgenv().sentinel_session) == _c3yvr3ey("\043\057\062\056\004\026") and getgenv().sentinel_session > CURRENT_SESSION then return false end
        if shared and type(shared.sentinel_session) == _c3yvr3ey("\043\057\062\056\004\026") and shared.sentinel_session > CURRENT_SESSION then return false end
        if _G and type(_G.sentinel_session) == _c3yvr3ey("\043\057\062\056\004\026") and _G.sentinel_session > CURRENT_SESSION then return false end
    end
    return true
end
local function waitWithCountdown(totalSeconds)
    if totalSeconds <= 0 then return end
    for remaining = totalSeconds - 1, 0, -1 do
        if not isCurrentSession() then return end
        task.wait(1)
    end
end
if _LP_STORE and _LP_STORE.sockets[SCRIPT_TAG] then
    pcall(function() _LP_STORE.sockets[SCRIPT_TAG]:Close() end)
    _LP_STORE.sockets[SCRIPT_TAG] = nil
elseif SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
    if getgenv and getgenv().sentinel_ws then
        pcall(function() getgenv().sentinel_ws:Close() end)
        getgenv().sentinel_ws = nil
    end
    if shared and shared.sentinel_ws then
        pcall(function() shared.sentinel_ws:Close() end)
        shared.sentinel_ws = nil
    end
    if _G and _G.sentinel_ws then
        pcall(function() _G.sentinel_ws:Close() end)
        _G.sentinel_ws = nil
    end
end
local function getProvidedKey()
    local k = nil
    pcall(function()
        if getgenv and (getgenv().script_key or getgenv().key) then k = getgenv().script_key or getgenv().key
        elseif _G and (_G.script_key or _G.key) then k = _G.script_key or _G.key
        elseif shared and (shared.script_key or shared.key) then k = shared.script_key or shared.key
        elseif getfenv then
            for level = 0, 5 do
                pcall(function()
                    local env = getfenv(level)
                    if env and (env.script_key or env.key) then k = env.script_key or env.key end
                end)
                if k then break end
            end
        end
    end)
    return k and tostring(k):gsub(_c3yvr3ey("\027\105\032\112\073\070\066\095\088\247\161\182"), _c3yvr3ey("\096\125")) or _c3yvr3ey("")
end
local isKeyPromptClosed = false
local function showKeyPromptPanel(submitCallback)
    local parentGui = getGuiParent()
    if not parentGui then return end
    cleanupExistingGui(_c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\192\247\224\245\238"))
    local gui = Instance.new(_c3yvr3ey("\022\047\033\063\004\006\040\003\020"))
    gui.Name = _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240\192\247\224\245\238")
    gui.ResetOnSpawn = false
    gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    gui.IgnoreGuiInset = true
    gui.DisplayOrder = 35
    pcall(function() if syn and syn.protect_gui then syn.protect_gui(gui) elseif protect_gui then protect_gui(gui) end end)
    local parented = pcall(function() gui.Parent = parentGui end)
    if not parented or not gui.Parent then
        pcall(function()
            gui.Parent = (LocalPlayer and (LocalPlayer:FindFirstChild(_c3yvr3ey("\021\032\050\035\004\026\040\003\020")) or LocalPlayer:WaitForChild(_c3yvr3ey("\021\032\050\035\004\026\040\003\020"), 5))) or CoreGui
        end)
    end
    local backdrop = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
    backdrop.Name = _c3yvr3ey("\007\045\048\049\005\026\000\006")
    backdrop.Size = UDim2.new(1, 0, 1, 0)
    backdrop.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    backdrop.BackgroundTransparency = 1
    backdrop.BorderSizePixel = 0
    backdrop.Active = true
    backdrop.Parent = gui
    local card = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
    card.Name = _c3yvr3ey("\014\041\042\025\000\026\011")
    card.AnchorPoint = Vector2.new(0.5, 0.5)
    card.Position = UDim2.new(0.5, 0, 0.5, 16)
    card.Size = UDim2.new(0, 440, 0, 0)
    card.AutomaticSize = Enum.AutomaticSize.Y
    card.BackgroundColor3 = THEME_BG
    card.BackgroundTransparency = 1
    card.BorderSizePixel = 0
    card.Parent = gui
    Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), card).CornerRadius = UDim.new(0, 3)
    local cardSize = Instance.new(_c3yvr3ey("\016\005\000\051\027\013\044\025\019\247\255\224\248\201\201\218"))
    cardSize.MaxSize = Vector2.new(440, 600)
    cardSize.Parent = card
    local stroke = Instance.new(_c3yvr3ey("\016\005\000\046\019\007\004\019"))
    stroke.Color = Color3.fromRGB(45, 45, 45)
    stroke.Transparency = 1
    stroke.Parent = card
    local pad = Instance.new(_c3yvr3ey("\016\005\003\059\005\012\006\024\026"))
    pad.PaddingTop, pad.PaddingBottom = UDim.new(0, 22), UDim.new(0, 22)
    pad.PaddingLeft, pad.PaddingRight = UDim.new(0, 22), UDim.new(0, 22)
    pad.Parent = card
    local list = Instance.new(_c3yvr3ey("\016\005\031\051\018\028\035\023\004\235\254\230"))
    list.FillDirection = Enum.FillDirection.Vertical
    list.SortOrder = Enum.SortOrder.LayoutOrder
    list.Padding = UDim.new(0, 14)
    list.Parent = card
    local header = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
    header.Size = UDim2.new(1, 0, 0, 36)
    header.BackgroundTransparency = 1
    header.LayoutOrder = 1
    header.Parent = card
    local iconFrame = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
    iconFrame.Size = UDim2.new(0, 36, 0, 36)
    iconFrame.BackgroundColor3 = THEME_ACCENT or Color3.fromRGB(168, 85, 247)
    iconFrame.BackgroundTransparency = 0.86
    iconFrame.BorderSizePixel = 0
    iconFrame.Parent = header
    Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), iconFrame).CornerRadius = UDim.new(0, 3)
    local icon = Instance.new(_c3yvr3ey("\012\033\050\061\004\036\014\020\024\232"))
    icon.Size = UDim2.new(0, 22, 0, 22)
    icon.AnchorPoint = Vector2.new(0.5, 0.5)
    icon.Position = UDim2.new(0.5, 0, 0.5, 0)
    icon.BackgroundTransparency = 1
    icon.Image = _c3yvr3ey("\055\046\043\059\018\027\010\002\020\224\177\189\182\145\151\153\133\133\244\255\227\225\230\208")
    icon.ImageColor3 = THEME_ACCENT or Color3.fromRGB(168, 85, 247)
    icon.Parent = iconFrame
    local title = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
    title.Position = UDim2.new(0, 48, 0, 0)
    title.Size = UDim2.new(1, -84, 1, 0)
    title.BackgroundTransparency = 1
    title.Font = fontBold
    title.TextSize = 20
    title.TextColor3 = THEME_TEXT
    title.TextXAlignment = Enum.TextXAlignment.Left
    title.Text = (SCRIPT_NAME ~= _c3yvr3ey("") and SCRIPT_NAME) or _c3yvr3ey("\004\057\039\050\004\006\027\031\030\229\255\251\246\206\135\252\208\205\182\163\163\189\187")
    title.Parent = header
    local closeBtn = Instance.new(_c3yvr3ey("\017\041\043\046\035\029\027\002\018\234"))
    closeBtn.AnchorPoint = Vector2.new(1, 0.5)
    closeBtn.Position = UDim2.new(1, 0, 0.5, 0)
    closeBtn.Size = UDim2.new(0, 26, 0, 26)
    closeBtn.BackgroundTransparency = 1
    closeBtn.Font = fontBold
    closeBtn.TextSize = 16
    closeBtn.TextColor3 = THEME_MUTED
    closeBtn.Text = _c3yvr3ey("\080")
    closeBtn.Parent = header
    local message = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
    message.Size = UDim2.new(1, 0, 0, 0)
    message.AutomaticSize = Enum.AutomaticSize.Y
    message.BackgroundTransparency = 1
    message.Font = fontRegular
    message.TextSize = 15
    message.TextColor3 = THEME_MUTED
    message.TextWrapped = true
    message.TextXAlignment = Enum.TextXAlignment.Left
    message.Text = _c3yvr3ey("\021\032\054\059\018\013\079\019\019\240\238\224\185\217\200\219\199\156\162\169\178\189\172\149\205\159\158\123\041\100\120\062\070\067\093\078\040\038\058\051\115")
    message.LayoutOrder = 2
    message.Parent = card
    local codeBox = Instance.new(_c3yvr3ey("\003\062\050\055\004"))
    codeBox.Size = UDim2.new(1, 0, 0, 52)
    codeBox.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    codeBox.BackgroundTransparency = 0.96
    codeBox.BorderSizePixel = 0
    codeBox.LayoutOrder = 3
    codeBox.Parent = card
    Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), codeBox).CornerRadius = UDim.new(0, 3)
    local inputBox = Instance.new(_c3yvr3ey("\017\041\043\046\035\007\023"))
    inputBox.Position = UDim2.new(0, 16, 0, 0)
    inputBox.Size = UDim2.new(1, -114, 1, 0)
    inputBox.BackgroundTransparency = 1
    inputBox.Font = fontRegular
    inputBox.TextSize = 15
    inputBox.TextColor3 = THEME_TEXT
    inputBox.TextXAlignment = Enum.TextXAlignment.Left
    inputBox.PlaceholderText = _c3yvr3ey("\021\045\032\046\004\072\022\025\008\246\171\249\252\217\135\198\208\206\166\228\255\246")
    inputBox.PlaceholderColor3 = THEME_MUTED
    inputBox.Text = _c3yvr3ey("")
    inputBox.ClearTextOnFocus = false
    inputBox.Parent = codeBox
    local submitBtn = Instance.new(_c3yvr3ey("\017\041\043\046\035\029\027\002\018\234"))
    submitBtn.AnchorPoint = Vector2.new(1, 0.5)
    submitBtn.Position = UDim2.new(1, -8, 0.5, 0)
    submitBtn.Size = UDim2.new(0, 84, 0, 36)
    submitBtn.BackgroundColor3 = THEME_ACCENT or Color3.fromRGB(168, 85, 247)
    submitBtn.AutoButtonColor = true
    submitBtn.Font = fontBold
    submitBtn.TextSize = 15
    submitBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
    submitBtn.Text = _c3yvr3ey("\006\035\061\046\008\006\026\019")
    submitBtn.Parent = codeBox
    Instance.new(_c3yvr3ey("\016\005\016\053\019\006\010\004"), submitBtn).CornerRadius = UDim.new(0, 3)
    local timer = Instance.new(_c3yvr3ey("\017\041\043\046\045\009\013\019\017"))
    timer.Size = UDim2.new(1, 0, 0, 18)
    timer.BackgroundTransparency = 1
    timer.Font = fontRegular
    timer.TextSize = 13
    timer.TextColor3 = THEME_MUTED
    timer.TextXAlignment = Enum.TextXAlignment.Left
    timer.Text = _c3yvr3ey("")
    timer.LayoutOrder = 4
    timer.Parent = card
    local function closeOut()
        isKeyPromptClosed = true
        pcall(function()
            local fade = TweenInfo.new(0.25, Enum.EasingStyle.Quart, Enum.EasingDirection.In)
            TweenService:Create(card, fade, { BackgroundTransparency = 1, Position = UDim2.new(0.5, 0, 0.5, 16) }):Play()
            TweenService:Create(backdrop, fade, { BackgroundTransparency = 1 }):Play()
            TweenService:Create(stroke, fade, { Transparency = 1 }):Play()
            for _, obj in ipairs(card:GetDescendants()) do
                if obj:IsA(_c3yvr3ey("\017\041\043\046\045\009\013\019\017")) or obj:IsA(_c3yvr3ey("\017\041\043\046\035\029\027\002\018\234")) or obj:IsA(_c3yvr3ey("\017\041\043\046\035\007\023")) then
                    TweenService:Create(obj, fade, { TextTransparency = 1 }):Play()
                elseif obj:IsA(_c3yvr3ey("\012\033\050\061\004\036\014\020\024\232")) then
                    TweenService:Create(obj, fade, { ImageTransparency = 1 }):Play()
                end
            end
            task.wait(0.25)
            gui:Destroy()
        end)
    end
    closeBtn.MouseButton1Click:Connect(function()
        submitCallback(_c3yvr3ey(""))
        closeOut()
    end)
    local function doSubmit()
        local text = inputBox.Text:gsub(_c3yvr3ey("\027\105\032\112\073\070\066\095\088\247\161\182"), _c3yvr3ey("\096\125"))
        if text ~= _c3yvr3ey("") then
            submitBtn.Text = _c3yvr3ey("\107\098\125")
            timer.Text = _c3yvr3ey("\006\036\054\057\010\001\001\017\093\239\238\235\183\142\137")
            submitCallback(text)
            closeOut()
        end
    end
    submitBtn.MouseButton1Click:Connect(doSubmit)
    inputBox.FocusLost:Connect(function(enterPressed)
        if enterPressed then
            doSubmit()
        end
    end)
    local fadeIn = TweenInfo.new(0.25, Enum.EasingStyle.Quart, Enum.EasingDirection.Out)
    TweenService:Create(card, fadeIn, { BackgroundTransparency = 0.03, Position = UDim2.new(0.5, 0, 0.5, 0) }):Play()
    TweenService:Create(backdrop, fadeIn, { BackgroundTransparency = 0.45 }):Play()
    TweenService:Create(stroke, fadeIn, { Transparency = 0 }):Play()
end
local function tryConnect
(isInternalReconnect)
    if not isCurrentSession() then
        return nil, true, _c3yvr3ey("\022\025\003\031\051\059\042\050\056\192")
    end
    local currentKeyCode = getProvidedKey()
    local success, response, retryAfter, rejectMsg = makeRequest(HOST_URL .. _c3yvr3ey("\106\045\035\051\078\009\026\002\021\171\255\253\242\197\201"), {
        userId = userId, username = username, placeId = placeId, jobId = jobId, gameId = gameId,
        hwid = hwid, scriptId = SCRIPT_ID, scriptName = SCRIPT_NAME, executor = executor,
        keyCode = currentKeyCode, runnerId = RUNNER_ID, isReconnect = isInternalReconnect or false, sessionId = CURRENT_SESSION, runId = RUN_ID,
        caps = { chunks = true }
    }, isInternalReconnect)
    if not success then
        if response == _c3yvr3ey("\023\013\007\031\062\036\038\059\052\208\206\214") then
            local waitTime = retryAfter or 15
            runnerWarn(_c3yvr3ey("\023\045\039\063\065\004\006\027\020\240\238\246\185\141\135\217\212\213\183\163\191\191\255") .. waitTime .. _c3yvr3ey("\054\108\049\063\007\007\029\019\093\246\238\230\235\217"))
            waitWithCountdown(waitTime)
            return nil, false
        elseif response == _c3yvr3ey("\018\030\028\020\038\055\040\055\048\193") or response == _c3yvr3ey("\002\013\030\031\062\058\042\037\041\214\194\209\205\229\227") then
            runnerWarn(rejectMsg or _c3yvr3ey("\018\062\060\052\006\072\008\023\016\225\171\191\185\212\207\199\198\156\176\169\163\177\175\146\205\157\136\034\101\127\116\117\064\072\019\078\046\104\046\118\057\013\013\020\028\242\226\224\225\188\196\203\220\221"))
            return nil, true, nil
        elseif response == _c3yvr3ey("\000\020\022\025\052\060\032\036\034\214\206\193\205\242\238\237\225\249\135") then
            runnerWarn(rejectMsg or _c3yvr3ey("\028\035\038\040\065\013\023\019\030\241\255\253\235\128\206\221\149\210\172\190\241\185\175\150\159\155\141\103\109\048\113\113\087\012\071\082\040\059\111\037\062\022\002\002\013\174\167\215\250\233\209\138\208\219\220\169\184\186\175\194\128\131\215\176\074\088\051\105\084\091\095\083\083\032\046\054\121\077\071\026\029\025\163\249\242\234\246\214\217\148\212\181\167\181\165\254\138\130\159\131\033\105\099\122\114\083\088\018\074\048\034\045\060\058\010\009\081\029\007\227\238\225\239\205\219\195\153"))
            return nil, true, nil
        elseif response and response:find(_c3yvr3ey("\022\025\003\031\051\059\042\050\056\192"), 1, true) then
            reconnectDisabled = true
            print(_c3yvr3ey("\030") .. label .. _c3yvr3ey("\024\108\000\047\017\013\029\005\024\224\238\246\185\194\222\142\212\156\173\175\166\189\173\198\136\140\158\097\124\100\120\108\005\094\070\084\122\104\060\034\050\020\027\027\023\231\167\252\240\255\204\196\223\221\220\178\190\250"))
            return nil, true, _c3yvr3ey("\022\025\003\031\051\059\042\050\056\192")
        elseif response and (response:find(_c3yvr3ey("\014\009\010\005\051\045\062\035\052\214\206\214")) or response:find(_c3yvr3ey("\014\041\042\122\051\013\030\003\020\246\238\246"))) then
            local providedKey = getProvidedKey()
            if providedKey == _c3yvr3ey("") and PROMPT_FOR_KEY then
                local enteredKey
                local done = false
                showKeyPromptPanel(function(k)
                    enteredKey = k
                    done = true
                end)
                while not done do task.wait(0.1) end
                if enteredKey and enteredKey ~= _c3yvr3ey("") then
                    if getgenv then getgenv().script_key = enteredKey end
                    if _G then _G.script_key = enteredKey end
                    local ok, fatal, reason = tryConnect(isInternalReconnect)
                    if not ok then
                        if getgenv and getgenv().script_key == enteredKey then getgenv().script_key = nil end
                        if _G and _G.script_key == enteredKey then _G.script_key = nil end
                    end
                    return ok, fatal, reason
                end
            end
            local msg
            if providedKey == _c3yvr3ey("") then
                msg = _c3yvr3ey("\011\035\115\049\004\017\079\005\024\240\165\178\204\211\194\148\149\207\160\184\184\168\171\185\134\145\130\034\052\048\053\071\106\121\097\101\010\013\022\116\125\016\003\023\023\160\245\235\184\249\219\207\210\205\203\163\227")
            else
                local serverMsg = _c3yvr3ey("")
                pcall(function()
                    local data = HttpService:JSONDecode(response)
                    if data and (data.message or data.error) then serverMsg = data.message or data.error end
                end)
                msg = _c3yvr3ey("\012\034\037\059\013\001\011\086\022\225\242\168\185\130") .. providedKey .. _c3yvr3ey("\103\098\115") .. (serverMsg ~= _c3yvr3ey("") and serverMsg or _c3yvr3ey("\014\041\042\122\015\007\027\086\015\225\232\253\254\206\206\221\208\216\237"))
            end
            runnerWarn(msg)
            return nil, true, nil
        elseif response and type(response) == _c3yvr3ey("\054\056\033\051\015\015") and response:sub(1, 7) == _c3yvr3ey("\007\013\029\020\036\044\085") then
            local reason = _c3yvr3ey("\028\035\038\122\000\026\010\086\031\229\229\252\252\196\137")
            pcall(function()
                local body = response:sub(8)
                local data = HttpService:JSONDecode(body)
                if data then reason = tostring(data.message or data.reason or data.error or _c3yvr3ey("\028\035\038\122\000\026\010\086\031\229\229\252\252\196\137")) end
            end)
            runnerWarn(reason)
            return nil, true, reason
        elseif response:find(_c3yvr3ey("\022\009\001\012\036\058\048\051\047\214\196\192"), 1, true) then
            local serverDetail = response:gsub(_c3yvr3ey("\027\031\022\008\055\045\061\041\056\214\217\221\203\128"), _c3yvr3ey(""))
            runnerQuiet(_c3yvr3ey("\022\041\033\044\004\026\079\003\019\229\253\243\240\204\198\204\217\217\227\226") .. serverDetail .. _c3yvr3ey("\108\119\115\045\008\004\003\086\015\225\255\224\224"))
            return nil, false, _c3yvr3ey("\017\030\018\020\050\033\042\056\041")
        elseif response:find(_c3yvr3ey("\011\009\007\013\046\058\036\041\056\214\217\221\203"), 1, true) then
            local netDetail = response:gsub(_c3yvr3ey("\027\002\022\014\054\039\061\061\034\193\217\192\214\242\135"), _c3yvr3ey(""))
            runnerQuiet(_c3yvr3ey("\011\041\039\045\014\026\004\086\024\246\249\253\235\128\213\203\212\223\171\163\191\191\255\149\136\134\141\103\123\048\063") .. netDetail .. _c3yvr3ey("\108\119\115\045\008\004\003\086\015\225\255\224\224"))
            return nil, false, _c3yvr3ey("\017\030\018\020\050\033\042\056\041")
        else
            runnerWarn(_c3yvr3ey("\004\057\039\050\065\014\014\031\017\225\239\168\185") .. tostring(response))
            return nil, true
        end
    end
    local ok, data = pcall(HttpService.JSONDecode, HttpService, response)
    if not ok or not data or not data.token then
        runnerWarn(_c3yvr3ey("\007\045\055\122\000\029\027\030\093\246\238\225\233\207\201\221\208\134\227") .. tostring(response))
        return nil, false
    end
    MY_LAST_CONNECT_ATTEMPT = os.clock()
    if getgenv then getgenv()._luaprotect_last_connect_attempt = MY_LAST_CONNECT_ATTEMPT end
    local ws = openWebSocket(WS_URL .. _c3yvr3ey("\122\056\060\049\004\006\082") .. data.token)
    if not ws then
        runnerWarn(_c3yvr3ey("\006\035\038\054\005\072\001\025\009\164\228\226\252\206\135\249\208\222\144\165\178\179\186\146"))
        return nil, false
    end
    if _LP_STORE then _LP_STORE.sockets[SCRIPT_TAG] = ws end
    if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        if getgenv then getgenv().sentinel_ws = ws end
        if shared then shared.sentinel_ws = ws end
        if _G then _G.sentinel_ws = ws end
    end
    connectionOpenedAt = os.clock()
    local lastReportedErrors = {}
    local function sendErrorReport(errMsg, stackTrace)
        local msgKey = tostring(errMsg)
        local now = os.time()
        if lastReportedErrors[msgKey] and (now - lastReportedErrors[msgKey]) < 3 then return end
        lastReportedErrors[msgKey] = now
        pcall(function()
            if ws then
                local reportStr = encodeJSON({ type = _c3yvr3ey("\054\047\033\051\017\028\048\004\024\244\228\224\237"), level = _c3yvr3ey("\032\062\033\053\019"), message = msgKey, stackTrace = tostring(stackTrace or _c3yvr3ey("")) })
                if ws.Send then ws:Send(reportStr)
                elseif ws.send then ws:send(reportStr) end
            end
        end)
    end
    local chunkState = nil
    local wsConnections = {}
    local function bindSignal(signalName, altName, handler)
        pcall(function()
            local sig = ws[signalName] or ws[altName]
            if sig and (typeof(sig) == _c3yvr3ey("\023\014\011\009\002\026\006\006\009\215\226\245\247\193\203") or sig.Connect) then
                local conn = sig:Connect(handler)
                if conn then table.insert(wsConnections, conn) end
            end
        end)
        pcall(function()
            if not ws[signalName] and not ws[altName] then ws[signalName] = handler; ws[altName] = handler end
        end)
    end
    local _undecryptableReported = false
    local function executeScriptPayload(decryptedOrErr)
        if decryptedOrErr:sub(1, 3) == _c3yvr3ey("\170\247\236") then
            decryptedOrErr = decryptedOrErr:sub(4)
        end
        decryptedOrErr = decryptedOrErr:gsub(_c3yvr3ey("\096\097\118\119\068\051\082\083\038\164\208\204\188\253\250\132\144\225\254\239\140"), function(comment)
            return (comment:gsub(_c3yvr3ey("\170\247\236"), _c3yvr3ey("")):gsub(_c3yvr3ey("\167\204\008\209\076\231\050"), _c3yvr3ey("")))
        end)
        if decryptedOrErr:sub(1, 2) ~= _c3yvr3ey("\104\097") then
            if decryptedOrErr:sub(1, 1) == _c3yvr3ey("\062") then return end
            if not _undecryptableReported then
                _undecryptableReported = true
                runnerWarn(_c3yvr3ey("\023\041\048\063\008\030\010\018\093\229\171\226\248\217\203\193\212\216\227\190\185\185\171\198\142\155\142\110\109\048\121\113\081\012\081\095\097\044\042\053\047\029\027\006\028\228\188\174\229\240\198\203\194\221\159\180\168\249\190\154\140\147\130\138\096\044\103\114\068\008\092\085\079\045\059\038\119"))
                sendErrorReport(_c3yvr3ey("\016\034\055\063\002\026\022\006\009\229\233\254\252\128\215\207\204\208\172\171\181\248\247\149\136\135\136\107\102\126\055\117\064\085\019\087\040\059\034\055\041\007\003") .. (isEnvironmentTampered and _c3yvr3ey("\105\108\054\052\023\001\029\025\019\233\238\252\237\128\193\194\212\219\164\175\181\248\190\149\205\128\154\111\121\117\101\123\065") or _c3yvr3ey("")) .. _c3yvr3ey("\108"), _c3yvr3ey(""))
            end
            return
        end
        local isKickPayload = decryptedOrErr:sub(1, 21) == _c3yvr3ey("\104\097\115\001\045\029\014\038\015\235\255\247\250\212\135\229\220\223\168\151\219")
        if isKickPayload then
            if not isCurrentSession() then return end
            local kickFn, kickErr = loadstring(decryptedOrErr)
            if not kickFn then
                runnerWarn(_c3yvr3ey("\014\037\048\049\065\024\014\015\017\235\234\246\185\197\213\220\218\206\249\234") .. tostring(kickErr))
                return
            end
            pcall(kickFn)
            return
        end
        if not isCurrentSession() then return end
        local executedStore = (_LP_STORE and _LP_STORE.executed[SCRIPT_TAG])
        if not executedStore and SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
            executedStore = (getgenv and getgenv()._luaprotect_executed) or (shared and shared._luaprotect_executed)
        end
        if not executedStore then
            executedStore = {}
            if _LP_STORE then _LP_STORE.executed[SCRIPT_TAG] = executedStore end
            if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
                if getgenv then getgenv()._luaprotect_executed = executedStore else shared._luaprotect_executed = executedStore end
            end
        end
        if not isCurrentSession() then return end
        local dedupKey = tostring(#decryptedOrErr) .. _c3yvr3ey("\127") .. decryptedOrErr:sub(1, 256) .. decryptedOrErr:sub(-256)
        if executedStore[dedupKey] then
            runnerWarn(_c3yvr3ey("\022\047\033\051\017\028\079\023\017\246\238\243\253\217\135\203\205\217\160\191\165\189\187\198\132\154\219\118\097\121\100\062\086\073\064\073\040\039\033\109\125\023\000\027\009\240\238\224\242\188\199\223\193\212\214\165\172\160\190\194\140\136\146\157\112\120\122\117\079"))
            return
        end
        local storeCount = 0
        for _ in pairs(executedStore) do storeCount = storeCount + 1 end
        if storeCount > 16 then
            for key in pairs(executedStore) do executedStore[key] = nil end
        end
        executedStore[dedupKey] = true
        local isBlockedNotice = decryptedOrErr:sub(1, 23) == _c3yvr3ey("\104\097\115\001\045\029\014\038\015\235\255\247\250\212\135\236\217\211\160\161\180\188\130")
        local fn, err = loadstring(decryptedOrErr, _c3yvr3ey("\120") .. tostring(SCRIPT_NAME ~= _c3yvr3ey("") and SCRIPT_NAME or _c3yvr3ey("\009\057\050\010\019\007\027\019\030\240")))
        if not fn then
            runnerWarn(_c3yvr3ey("\009\035\050\062\018\028\029\031\019\227\171\247\235\210\200\220\143\156") .. tostring(err))
            sendErrorReport(_c3yvr3ey("\009\035\050\062\018\028\029\031\019\227\171\241\246\205\215\199\217\221\183\163\190\182\255\131\159\134\148\112\051\048") .. tostring(err), debug and debug.traceback and debug.traceback() or _c3yvr3ey(""))
            return
        end
        if not isBlockedNotice then
        end
        local execOk, execErr = xpcall(fn, function(err)
            local message = tostring(err)
            if debug and debug.traceback then return debug.traceback(message, 2) end
            return message
        end)
        if not isBlockedNotice then
            if not execOk then
                runnerWarn(_c3yvr3ey("\000\052\054\057\020\028\006\025\019\164\238\224\235\207\213\148\149") .. tostring(execErr))
                sendErrorReport(tostring(execErr), debug and debug.traceback and debug.traceback() or _c3yvr3ey(""))
            else
            end
        end
    end
    local function handleIncomingMessage(hexPayload)
        task.spawn(function()
            local decOk, decryptedOrErr = pcall(decryptXOR, hexPayload, data.token)
            if not decOk then return end
            if decryptedOrErr:sub(1, 1) == _c3yvr3ey("\062") then
                local parseOk, parsed = pcall(HttpService.JSONDecode, HttpService, decryptedOrErr)
                if parseOk and type(parsed) == _c3yvr3ey("\049\045\049\054\004") and parsed.lp_event == _c3yvr3ey("\033\037\032\057\014\026\011\041\017\237\229\249\198\210\194\223\192\213\177\175\181") then
                    showDiscordLinkPanel(parsed, function(event)
                        local req = encodeJSON(event)
                        if ws.Send then ws:Send(req) elseif ws.send then ws:send(req) end
                    end)
                    return
                end
                if parseOk and type(parsed) == _c3yvr3ey("\049\045\049\054\004") and parsed.lp_event == _c3yvr3ey("\033\037\032\057\014\026\011\041\017\237\229\249\198\197\213\220\218\206") then
                    showDiscordLinkError(parsed.message)
                    return
                end
                if parseOk and type(parsed) == _c3yvr3ey("\049\045\049\054\004") and parsed.lp_event == _c3yvr3ey("\033\037\032\057\014\026\011\041\017\237\229\249\252\196") then
                    task.spawn(hideDiscordLinkPanel, true)
                    return
                end
                if parseOk and type(parsed) == _c3yvr3ey("\049\045\049\054\004") and parsed.lp_event == _c3yvr3ey("\036\040\062\051\015\055\014\024\019\235\254\252\250\197\202\203\219\200") then
                    showAdminAnnouncement(parsed.title, parsed.message, parsed.duration, parsed.color, parsed.prefix, parsed.verified)
                    return
                end
                if parseOk and type(parsed) == _c3yvr3ey("\049\045\049\054\004") and parsed.lp_event == _c3yvr3ey("\044\034\039\063\006\026\006\002\004\219\232\250\248\204\203\203\219\219\166") then
                    task.spawn(function()
                        local nonce = tostring(parsed.nonce or _c3yvr3ey(""))
                        local seed = tostring(parsed.seed or _c3yvr3ey(""))
                        local tampered = false
                        local reason = _c3yvr3ey("")
                        pcall(function()
                            if not isLowSyncExecutor then
                                if getrawmetatable and islclosure and islclosure(getrawmetatable) then tampered = true; reason = _c3yvr3ey("\034\041\039\040\000\031\002\019\009\229\255\243\251\204\194\142\209\217\183\165\164\170") end
                                if hookmetamethod and islclosure and islclosure(hookmetamethod) then tampered = true; reason = _c3yvr3ey("\045\035\060\049\012\013\027\023\016\225\255\250\246\196\135\202\208\200\172\191\163") end
                            end
                            if type(loadstring) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") or type(pcall) ~= _c3yvr3ey("\035\057\061\057\021\001\000\024") then
                                tampered = true; reason = _c3yvr3ey("\038\035\033\063\065\015\003\025\031\229\231\225\185\195\200\220\199\201\179\190\180\188")
                            end
                            if not isLowSyncExecutor and getrawmetatable and type(game) == _c3yvr3ey("\048\063\054\040\005\009\027\023") then
                                local metaOk, meta = pcall(getrawmetatable, game)
                                if metaOk and type(meta) == _c3yvr3ey("\049\045\049\054\004") then
                                    local nc = rawget(meta, _c3yvr3ey("\026\019\061\059\012\013\012\023\017\232"))
                                    if nc and islclosure and islclosure(nc) then
                                        tampered = true; reason = _c3yvr3ey("\034\045\062\063\065\055\048\024\028\233\238\241\248\204\203\142\221\211\172\161\180\188")
                                    end
                                end
                            end
                            if getgenv then
                                local genv = getgenv()
                                if genv.dump or genv.Hydroxide or genv.SimpleSpy then
                                    tampered = true; reason = _c3yvr3ey("\036\047\039\051\023\013\079\005\030\246\226\226\237\128\195\219\216\204\166\184\241\247\255\149\157\141\219\118\102\127\123\062\065\073\071\095\034\060\042\050")
                                end
                            end
                        end)
                        local canonicalPayload = nonce .. _c3yvr3ey("\107") .. seed .. _c3yvr3ey("\107") .. tostring(RUN_ID or _c3yvr3ey("")) .. _c3yvr3ey("\107") .. tostring(CURRENT_SESSION or _c3yvr3ey("")) .. _c3yvr3ey("\107") .. (tampered and _c3yvr3ey("\116") or _c3yvr3ey("\117"))
                        local challengeSig = sha256.hmac(SECRET_KEY, canonicalPayload)
                        local respPayload = encodeJSON({
                            event = _c3yvr3ey("\044\034\039\063\006\026\006\002\004\219\249\247\234\208\200\192\198\217"),
                            timestamp = os.time(),
                            challengeResponse = challengeSig,
                            tampered = tampered,
                            reason = reason
                        })
                        pcall(function()
                            if ws.Send then ws:Send(respPayload)
                            elseif ws.send then ws:send(respPayload) end
                        end)
                    end)
                    return
                end
                if parseOk and type(parsed) == _c3yvr3ey("\049\045\049\054\004") and parsed.lp_chunk then
                    if parsed.lp_chunk == _c3yvr3ey("\054") then
                        chunkState = { id = parsed.id, total = tonumber(parsed.total) or 0, len = tonumber(parsed.len) or 0, parts = {} }
                    elseif parsed.lp_chunk == _c3yvr3ey("\033") and chunkState and parsed.id == chunkState.id then
                        local seq = tonumber(parsed.seq) or (#chunkState.parts + 1)
                        chunkState.parts[seq] = tostring(parsed.data or _c3yvr3ey(""))
                    elseif parsed.lp_chunk == _c3yvr3ey("\032") and chunkState and parsed.id == chunkState.id then
                        local full = table.concat(chunkState.parts)
                        local expectedLen = chunkState.len
                        chunkState = nil
                        if #full == expectedLen then
                            local decOkChunk, unencryptedScript = pcall(decryptXOR, full, data.token)
                            if decOkChunk then
                                executeScriptPayload(unencryptedScript)
                            else
                                runnerWarn(_c3yvr3ey("\006\036\038\052\010\072\011\019\030\246\242\226\237\201\200\192\149\217\177\184\190\170\229\198") .. tostring(unencryptedScript))
                                sendErrorReport(_c3yvr3ey("\038\036\038\052\010\013\011\086\014\231\249\251\233\212\135\202\208\223\177\179\161\172\182\137\131\212\157\099\096\124\114\122\031\012") .. tostring(unencryptedScript), _c3yvr3ey(""))
                            end
                        else
                            sendErrorReport(_c3yvr3ey("\038\036\038\052\010\013\011\086\014\231\249\251\233\212\135\220\208\221\176\185\180\181\189\138\148\212\157\099\096\124\114\122\005\004\095\095\047\047\059\062\125\009\002\001\020\225\243\237\253\181"), _c3yvr3ey(""))
                        end
                    end
                    return
                end
            end
            executeScriptPayload(decryptedOrErr)
        end)
    end
    bindSignal(_c3yvr3ey("\010\034\030\063\018\027\014\017\024"), _c3yvr3ey("\042\034\062\063\018\027\014\017\024"), handleIncomingMessage)
    local closed = false
    hbThread = task.spawn(function()
        while ws and not closed do
            task.wait(30)
            if closed then break end
            if not isCurrentSession() then
                closeWebSocket(ws)
                break
            end
            local payload = encodeJSON({ event = _c3yvr3ey("\045\041\050\040\021\010\010\023\009"), timestamp = os.time() })
            pcall(function()
                if ws.Send then ws:Send(payload)
                elseif ws.send then ws:send(payload) end
            end)
        end
    end)
    local function onDisconnect(code, reason)
        if closed then return end
        closed = true
        if getgenv and type(getgenv()._luaprotect_last_connect_attempt) == _c3yvr3ey("\043\057\062\056\004\026") then
            local globalAttempt = getgenv()._luaprotect_last_connect_attempt
            if globalAttempt ~= MY_LAST_CONNECT_ATTEMPT and (os.clock() - globalAttempt) < 3 then
                reconnectDisabled = true
                runnerQuiet(_c3yvr3ey("\028\037\054\054\005\001\001\017\093\211\238\240\202\207\196\197\208\200\227\190\190\248\190\136\130\128\147\103\123\048\100\125\087\069\067\078\097\096\042\046\056\007\030\006\022\242\167\226\252\241\202\222\145\220\218\178\168\183\175\135\141\217\217"))
            end
        end
        local closeCode = tonumber(code)
        local closeReason = type(reason) == _c3yvr3ey("\054\056\033\051\015\015") and reason or _c3yvr3ey("")
        local function readCloseEvent(value)
            if type(value) ~= _c3yvr3ey("\049\045\049\054\004") and type(value) ~= _c3yvr3ey("\048\063\054\040\005\009\027\023") then return nil, nil end
            local eventCode, eventReason
            pcall(function()
                eventCode = tonumber(value.code or value.Code or value.statusCode or value.status or value.closeCode)
                eventReason = value.reason or value.Reason or value.message or value.Message
            end)
            return eventCode, eventReason and tostring(eventReason) or nil
        end
        local eventCode, eventReason = readCloseEvent(code)
        if eventCode then closeCode = eventCode end
        if eventReason and eventReason ~= _c3yvr3ey("") then closeReason = eventReason end
        if not closeCode then
            local secondCode, secondReason = readCloseEvent(reason)
            closeCode = secondCode or tonumber(reason)
            if secondReason and secondReason ~= _c3yvr3ey("") then closeReason = secondReason end
        end
        if closeCode == 4008 or closeReason:find(_c3yvr3ey("\022\057\035\063\019\027\010\018\024\224"), 1, true) then
            reconnectDisabled = true
        end
        lastCloseWasBusy = closeCode == 4013 or closeCode == 4029
            or closeReason:find(_c3yvr3ey("\036\056\115\057\000\024\014\021\020\240\242"), 1, true) ~= nil
            or closeReason:find(_c3yvr3ey("\017\035\060\122\012\009\001\015\093\231\228\252\250\213\213\220\208\210\183"), 1, true) ~= nil
        if hbThread then task.cancel(hbThread) end
        chunkState = nil
        for _, conn in ipairs(wsConnections) do pcall(function() conn:Disconnect() end) end
        table.clear(wsConnections)
        closeWebSocket(ws)
        if _LP_STORE and _LP_STORE.sockets[SCRIPT_TAG] == ws then _LP_STORE.sockets[SCRIPT_TAG] = nil end
        if getgenv and getgenv().sentinel_ws == ws then getgenv().sentinel_ws = nil end
        if shared and shared.sentinel_ws == ws then shared.sentinel_ws = nil end
        if _G and _G.sentinel_ws == ws then _G.sentinel_ws = nil end
        if connectionOpenedAt then
            local livedSeconds = os.clock() - connectionOpenedAt
            if livedSeconds >= STABLE_CONNECTION_THRESHOLD_SECONDS then stableConnectionSeen = true end
            connectionOpenedAt = nil
        end
        local parts = {}
        if code ~= nil and type(code) == _c3yvr3ey("\043\057\062\056\004\026") then table.insert(parts, _c3yvr3ey("\038\035\055\063\092") .. tostring(code)) end
        if code ~= nil and type(code) == _c3yvr3ey("\054\056\033\051\015\015") and code ~= _c3yvr3ey("") then table.insert(parts, _c3yvr3ey("\038\035\055\063\092") .. code) end
        if reason ~= nil and tostring(reason) ~= _c3yvr3ey("") and type(reason) ~= _c3yvr3ey("\048\063\054\040\005\009\027\023") then table.insert(parts, _c3yvr3ey("\055\041\050\041\014\006\082") .. tostring(reason)) end
        local detail = (#parts > 0) and (_c3yvr3ey("\101\100") .. table.concat(parts, _c3yvr3ey("\105\108")) .. _c3yvr3ey("\108")) or _c3yvr3ey("")
        runnerQuiet(_c3yvr3ey("\001\037\032\057\014\006\001\019\030\240\238\246") .. detail)
    end
    bindSignal(_c3yvr3ey("\010\034\016\054\014\027\010"), _c3yvr3ey("\042\034\048\054\014\027\010"), onDisconnect)
    local function handleIncomingError(err)
        runnerQuiet(_c3yvr3ey("\018\031\115\063\019\026\000\004\071\164") .. tostring(err))
        onDisconnect()
    end
    bindSignal(_c3yvr3ey("\010\034\022\040\019\007\029"), _c3yvr3ey("\042\034\054\040\019\007\029"), handleIncomingError)
    return ws, false
end
if not fetchRunnerKey() then return end
if not IS_TELEPORT_RECONNECT then
    RUN_ID = tostring(RUNNER_ID) .. _c3yvr3ey("\127") .. RUN_ID
end
if _LP_STORE then _LP_STORE.run_ids[SCRIPT_TAG] = RUN_ID end
if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
    if getgenv then getgenv()._luaprotect_run_id = RUN_ID end
    if shared then shared._luaprotect_run_id = RUN_ID end
    if _G then _G._luaprotect_run_id = RUN_ID end
end
local CONTINUOUS_SESSION = "0" == _c3yvr3ey("\116")
local teleportHandoffRegistered = false
local function registerTeleportHandoff()
    if not CONTINUOUS_SESSION or teleportHandoffRegistered then return end
    teleportHandoffRegistered = true
    for attempt = 1, 3 do
        local handoffOk, handoffBody = makeRequest(HOST_URL .. _c3yvr3ey("\106\045\035\051\078\026\026\024\019\225\249\191\241\193\201\202\218\218\165"), {
            userId = userId, hwid = hwid, scriptId = SCRIPT_ID,
            runnerId = RUNNER_ID, sessionId = CURRENT_SESSION, runId = RUN_ID,
        }, false)
        if handoffOk and handoffBody then
            local parsedOk, handoffData = pcall(HttpService.JSONDecode, HttpService, handoffBody)
            if parsedOk and handoffData and handoffData.token then
                local relaunchUrl = HOST_URL .. _c3yvr3ey("\106\045\035\051\078\026\026\024\019\225\249\191\235\197\196\193\219\210\166\169\165\247") .. SCRIPT_ID .. _c3yvr3ey("\122\036\050\052\005\007\009\016\064") .. tostring(handoffData.token)
                pcall(function()
                    if syn and syn.queue_on_teleport then syn.queue_on_teleport(string.format(_c3yvr3ey("\041\035\050\062\018\028\029\031\019\227\163\245\248\205\194\148\253\200\183\186\150\189\171\206\200\133\210\043\033\057"), relaunchUrl))
                    elseif queue_on_teleport then queue_on_teleport(string.format(_c3yvr3ey("\041\035\050\062\018\028\029\031\019\227\163\245\248\205\194\148\253\200\183\186\150\189\171\206\200\133\210\043\033\057"), relaunchUrl))
                    elseif krnl and krnl.queue_on_teleport then krnl.queue_on_teleport(string.format(_c3yvr3ey("\041\035\050\062\018\028\029\031\019\227\163\245\248\205\194\148\253\200\183\186\150\189\171\206\200\133\210\043\033\057"), relaunchUrl)) end
                end)
                return
            end
        end
        if attempt < 3 then task.wait(attempt * 2) end
    end
    teleportHandoffRegistered = false
    runnerWarn(_c3yvr3ey("\006\035\038\054\005\072\001\025\009\164\249\247\254\201\212\218\208\206\227\169\190\182\171\143\131\129\148\119\122\061\100\123\086\095\090\085\047\104\039\055\051\000\004\020\031"))
end
task.spawn(function()
    local retries = 0
    local busyRetries = 0
    local recoveringFromStable = false
    local hasConnected = IS_TELEPORT_RECONNECT
    while isCurrentSession() do
        local activeWs = (_LP_STORE and _LP_STORE.sockets[SCRIPT_TAG])
        if not activeWs and SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
            activeWs = (getgenv and getgenv().sentinel_ws)
                or (shared and shared.sentinel_ws)
                or (_G and _G.sentinel_ws)
        end
        if activeWs then
            task.wait(1)
        else
            if stableConnectionSeen then
                retries = 0
                stableConnectionSeen = false
                recoveringFromStable = true
            end
            local isInternalReconnect = hasConnected
            local waitedBusy = false
            if lastCloseWasBusy then
                lastCloseWasBusy = false
                waitedBusy = true
                busyRetries = busyRetries + 1
                if busyRetries > MAX_BUSY_RETRIES then break end
                local delay = math.min(BUSY_MIN_DELAY * (2 ^ (busyRetries - 1)), 120)
                delay = delay * (0.75 + math.random() * 0.5) + math.random() * 5
                runnerQuiet(_c3yvr3ey("\022\041\033\044\004\026\079\020\008\247\242\178\180\128\213\203\193\206\186\163\191\191\255\143\131\212") .. string.format(_c3yvr3ey("\096\098\099\060"), delay) .. _c3yvr3ey("\054\098\125\116"))
                waitWithCountdown(delay)
            else
                retries = retries + 1
                if retries > (recoveringFromStable and MAX_RETRIES_AFTER_STABLE or MAX_RETRIES) then
                    break
                end
            end
            if not waitedBusy and (retries > 1 or hasConnected) then
                local delay = math.max(1.5, math.min(BASE_DELAY * (2 ^ (retries - 1)), MAX_DELAY))
                delay = delay * (0.75 + math.random() * 0.5) + math.random() * 3
                runnerQuiet(_c3yvr3ey("\023\041\048\053\015\006\010\021\009\237\229\245\185\201\201\142") .. string.format(_c3yvr3ey("\096\098\098\060"), delay) .. _c3yvr3ey("\054\098\125\116"))
                waitWithCountdown(delay)
            end
            if not isCurrentSession() then break end
            local ws, isRejected = tryConnect(isInternalReconnect)
            if isRejected then break end
            if ws then
                hasConnected = true
                registerTeleportHandoff()
                if SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
                    if getgenv then getgenv().sentinel_auth_passed = true
                    elseif shared then shared.sentinel_auth_passed = true end
                end
            end
        end
    end
    local finalWs = (_LP_STORE and _LP_STORE.sockets[SCRIPT_TAG])
    if not finalWs and SCRIPT_TAG == _c3yvr3ey("\033\041\053\059\020\004\027") then
        finalWs = (getgenv and getgenv().sentinel_ws)
            or (shared and shared.sentinel_ws)
            or (_G and _G.sentinel_ws)
    end
    local isActive = false
    if _LP_STORE and _LP_STORE.sockets[SCRIPT_TAG] == finalWs then isActive = true; _LP_STORE.sockets[SCRIPT_TAG] = nil end
    if getgenv and getgenv().sentinel_ws == finalWs then isActive = true; getgenv().sentinel_ws = nil end
    if shared and shared.sentinel_ws == finalWs then isActive = true; shared.sentinel_ws = nil end
    if _G and _G.sentinel_ws == finalWs then isActive = true; _G.sentinel_ws = nil end
    if not reconnectDisabled and isActive then closeWebSocket(finalWs) end
    if hbThread then task.cancel(hbThread) end
end)