local repo = "https://raw.githubusercontent.com/deividcomsono/Obsidian/refs/heads/main/"
local Library = loadstring(game:HttpGet(repo .. "Library.lua"))()

local Players           = game:GetService("Players")
local RunService        = game:GetService("RunService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace         = game:GetService("Workspace")
local LocalPlayer       = Players.LocalPlayer

local GrabEvents       = ReplicatedStorage:WaitForChild("GrabEvents", 10)
local MenuToys         = ReplicatedStorage:WaitForChild("MenuToys", 10)

local SetNetworkOwner  = GrabEvents and GrabEvents:WaitForChild("SetNetworkOwner", 10)
local DestroyGrabLine  = GrabEvents and GrabEvents:WaitForChild("DestroyGrabLine", 10)
local SpawnToyRemote   = MenuToys and MenuToys:WaitForChild("SpawnToyRemoteFunction", 10)
local DestroyToyRemote = MenuToys and MenuToys:WaitForChild("DestroyToy", 10)

local inv = Workspace:WaitForChild(LocalPlayer.Name .. "SpawnedInToys", 10)

local Window = Library:CreateWindow({
    Title  = "Kick Test",
    Footer = "test build",
    Icon   = "rbxassetid://125696751031713",
    Center = true,
    AutoShow = true,
    Resizable = true,
    EnableSidebarResize = true,
    EnableCompacting = true,
    SidebarCompacted = true,
    MinSidebarWidth = 200,
    SidebarCompactWidth = 56,
    NotifySide = "Right",
    ShowCustomCursor = false,
    Size = UDim2.fromOffset(925, 652),
})

Tabs = {
    Home = Window:AddTab("Homee>", "house"),
    Target   = Window:AddTab("Target", "crosshair"),
    Defense = Window:AddTab("Defense", "shield"),
    Visual = Window:AddTab("Visual", "eye"),
    Misc = Window:AddTab("Misc", "sliders-horizontal"),
    Settings = Window:AddTab("Settings", "settings"),
}

local Stats             = Stats             or game:GetService("Stats")
local Players           = Players           or game:GetService("Players")
local LocalPlayer       = LocalPlayer       or Players.LocalPlayer

tbl9 = tbl9 or {}
tbl9.StartTime  = tbl9.StartTime  or tick()
tbl9.BlackHoles = tbl9.BlackHoles or 0
tbl9.Version    = tbl9.Version    or "v1.0.1"


do
    local HomeTab = Tabs and Tabs.Home
    if not HomeTab then
        warn("[Statistics] Tabs.Home not found — skipped")
        return
    end

    local Statistics = HomeTab:AddRightGroupbox("Statistics", "chart-no-axes-combined")

    Statistics:AddLabel("CurrentTime", { Text = "Current time: 00:00", DoesWrap = true })
    Statistics:AddLabel("VerLabel", {
        Text = ("Current script version: <b>%*</b>"):format(tbl9.Version),
        DoesWrap = true,
    })
    Statistics:AddLabel("TogglesCurrentlyOn", { Text = "Toggles currently enabled: 0", DoesWrap = true })
    Statistics:AddDivider("Server Statistics")
    Statistics:AddLabel("SpentTime", { Text = "Elapsed time: 0 seconds", DoesWrap = true })
    Statistics:AddLabel("LabelHi", { Text = "Kicked players: 0", DoesWrap = true })
end

task.spawn(function()
    local lastTime     = nil
    local lastBlackHls = nil
    local lastElapsed  = nil

    while task.wait(0.25) do
        if flag11 then return end

        if not (Library and Library.Labels) then
        else
            local nowTime = os.date("%H:%M")

            if nowTime ~= lastTime then
                local lbl = Library.Labels.CurrentTime
                if lbl then
                    lbl:SetText(("Current time: <b>%*</b>"):format(nowTime))
                    lastTime = nowTime
                end
            end

            if tbl9.BlackHoles ~= lastBlackHls then
                local lbl = Library.Labels.LabelHi
                if lbl then
                    lbl:SetText(("Kicked players: <b>%*</b>"):format(tbl9.BlackHoles))
                    lastBlackHls = tbl9.BlackHoles
                end
            end

            local elapsed = math.floor(tick() - tbl9.StartTime)
            if elapsed ~= lastElapsed then
                local lbl = Library.Labels.SpentTime
                if lbl then
                    lbl:SetText(("Elapsed time: <b>%* seconds</b>"):format(elapsed))
                    lastElapsed = elapsed
                end
            end
        end
    end
end)

task.spawn(function()
    local function count()
        local n = 0
        if Library and Library.Toggles then
            for _, t in pairs(Library.Toggles) do
                if t and t.Value then n += 1 end
            end
        end
        if Library and Library.Labels and Library.Labels.TogglesCurrentlyOn then
            Library.Labels.TogglesCurrentlyOn:SetText(("Toggles currently on: <b>%*</b>"):format(n))
        end
        return n
    end

    task.wait(2)

    count()

    if Library and Library.Toggles then
        for _, t in pairs(Library.Toggles) do
            if t and t.OnChanged then
                t:OnChanged(count)
            end
        end
    end

    while task.wait(3) do
        if flag11 then return end
        count()
    end
end)

local Players           = Players           or game:GetService("Players")
local ReplicatedStorage = ReplicatedStorage or game:GetService("ReplicatedStorage")
local HttpService       = HttpService       or game:GetService("HttpService")
local TeleportService   = TeleportService   or game:GetService("TeleportService")
local LocalPlayer       = LocalPlayer       or Players.LocalPlayer

tbl7 = tbl7 or {}
tbl8 = tbl8 or {}
tbl9 = tbl9 or {}
tbl12 = tbl12 or {}

local placeId = game.PlaceId
local jobId   = game.JobId

local fn18 = fn18 or function(msg, title, soundId, duration)
    if _G.nLheNotify then
        _G.nLheNotify(title or "nLhe", tostring(msg), "info", duration or 4)
    elseif Library and Library.Notify then
        Library:Notify({
            Title = title or "nLhe",
            Description = tostring(msg),
            Duration = duration or 4,
        })
    else
        warn(("[%s] %s"):format(title or "nLhe", tostring(msg)))
    end
end

local flag11 = false

local queueOnTeleport = queue_on_teleport or queueonteleport or (syn and syn.queue_on_teleport)

reloadPath = reloadPath or nil

tbl7.ServerHop = tbl7.ServerHop or {}
local SH = tbl7.ServerHop
SH.Busy       = false
SH.Pending    = nil
SH.Retrying   = false
SH.Cancelled  = false
SH.Token      = 0
SH.AutoToken  = 0
SH.Rejected   = SH.Rejected or {}
SH.LastFetchError = nil
SH.LastCacheError = nil
SH.CachePath  = SH.CachePath or ("nLheServerHop_" .. tostring(placeId) .. ".json")
SH.CachedRegions = SH.CachedRegions or {}
SH.Regions    = SH.Regions or {}
SH.RegionNames = SH.RegionNames or {
    "Automatic", "EU", "North America", "South America", "Asia", "Oceania",
}
SH.AutomaticCountry = SH.AutomaticCountry or nil
SH.PlayerCoordinates = SH.PlayerCoordinates or nil
SH.ResolvedRegions = SH.ResolvedRegions or {}
SH.ContinentCountries = SH.ContinentCountries or {
    EU               = " AD AL AT AX BA BE BG BY CH CY CZ DE DK EE ES FI FO FR GB GG GI GR HR HU IE IM IS IT JE LI LT LU LV MC MD ME MK MT NL NO PL PT RO RS RU SE SI SJ SK SM TR UA VA XK ",
    ["North America"]= " AG AI AW BB BL BM BQ BS BZ CA CR CU CW DM DO GD GL GP GT HN HT JM KN KY LC MF MQ MS MX NI PA PM PR SV SX TC TT US VC VG VI ",
    ["South America"]= " AR BO BR CL CO EC FK GF GY PE PY SR UY VE ",
    Asia             = " AE AF AM AZ BD BH BN BT CN GE HK ID IL IN IQ IR JO JP KG KH KP KR KW KZ LA LB LK MM MN MO MV MY NP OM PH PK PS QA SA SG SY TH TJ TL TM TW UZ VN YE ",
    Oceania          = " AS AU CC CK CX FJ FM GU KI MH MP NC NF NR NU NZ PF PG PN PW SB TK TO TV UM VU WF WS ",
}
SH.CountryCoordinates = SH.CountryCoordinates or {
    AX = Vector2.new(60.18, 19.92),
    BQ = Vector2.new(12.18, -68.24),
    CW = Vector2.new(12.17, -68.99),
    BL = Vector2.new(17.90, -62.83),
    MF = Vector2.new(18.07, -63.05),
    SX = Vector2.new(18.04, -63.05),
    SS = Vector2.new(6.88, 31.31),
}

tbl9.ServerHopRegion     = tbl9.ServerHopRegion     or "Automatic"
tbl9.ServerHopSort       = tbl9.ServerHopSort       or "Closest Datacenter"
tbl9.ServerHopMinPlayers = tbl9.ServerHopMinPlayers or 0
tbl9.ServerHopMaxPlayers = tbl9.ServerHopMaxPlayers or Players.MaxPlayers
tbl9.AutoServerHopTime   = tbl9.AutoServerHopTime   or 30
tbl8.AutoServerHop       = tbl8.AutoServerHop       or false
tbl8.AutoRejoin          = tbl8.AutoRejoin          or false
tbl8.RejoinWithAntiLag   = tbl8.RejoinWithAntiLag   ~= false
tbl8.RejoinWithScript    = tbl8.RejoinWithScript    or false

tbl12.QueueTeleport = tbl12.QueueTeleport or function(antiLag, reload)
    if type(queueOnTeleport) ~= "function" then
        if reload then fn18("This executor does not support queue_on_teleport") end
        return false
    end
    if reload and not reloadPath then
        fn18("Local reload is unavailable: file persistence failed")
        return false
    end

    local source = string.format([[
repeat task.wait() until game:IsLoaded()
local player = game:GetService("Players").LocalPlayer
if not player then return end
local scripts = player:WaitForChild("PlayerScripts", 15)
if scripts then
    for _, name in ipairs({"CharacterAndBeamMove", "StickyPartsTouchDetection"}) do
        local item = scripts:WaitForChild(name, 10)
        if item then item.Enabled = not %s end
    end
end
if %s then
    local env = getgenv and getgenv() or _G
    env.ResonanceRunning = false
    env.ResonanceStarting = false
    local source = assert(readfile, "readfile unavailable")(%q)
    local run, message = loadstring(source, "@nLhe")
    assert(run, message)
    run()
end
]], tostring(antiLag == true), tostring(reload == true), reloadPath or "")

    local ok, err = pcall(queueOnTeleport, source)
    if not ok then fn18("Unable to queue teleport: " .. tostring(err)) end
    return ok
end

tbl12.Rejoin = tbl12.Rejoin or function(antiLag, reload)
    if not jobId or jobId == "" then
        fn18("Job ID not found! Couldn't rejoin")
        return
    end
    tbl12.QueueTeleport(antiLag, reload)

    if #Players:GetPlayers() <= 1 then
        LocalPlayer:Kick("\nRejoining...")
        task.wait()
        TeleportService:Teleport(placeId, LocalPlayer)
    else
        TeleportService:TeleportToPlaceInstance(placeId, jobId, LocalPlayer)
    end
end

tbl12.NormalizeServerHopServer = function(raw)
    if typeof(raw) ~= "table" then return end
    local id       = raw.Id or raw.id
    local playing  = tonumber(raw.Playing or raw.playing)
    local maxPl    = tonumber(raw.MaxPlayers or raw.maxPlayers)
    if type(id) ~= "string" or not playing or not maxPl or maxPl <= 0 then return end
    return {
        Id         = id,
        Playing    = math.max(0, playing),
        MaxPlayers = maxPl,
        Ping       = tonumber(raw.Ping or raw.ping),
        FPS        = tonumber(raw.FPS or raw.fps),
    }
end

tbl12.IsServerHopCandidate = function(server, okIds)
    if server.Id == jobId or SH.Rejected[server.Id] then return false end
    if okIds and not okIds[server.Id] then return false end
    local mn = math.min(tbl9.ServerHopMinPlayers, tbl9.ServerHopMaxPlayers)
    local mx = math.max(tbl9.ServerHopMinPlayers, tbl9.ServerHopMaxPlayers)
    if server.Playing < mn or server.Playing > mx then return false end
    if not tbl8.ServerHopIncludeFull and server.Playing >= server.MaxPlayers then return false end
    return true
end

tbl12.LoadServerHopCache = function()
    if not readfile or not isfile then return {}, nil, false, {} end
    if not isfile(SH.CachePath) then return {}, nil, false, {} end

    local ok, decoded = pcall(function()
        return HttpService:JSONDecode(readfile(SH.CachePath))
    end)
    if not ok or typeof(decoded) ~= "table" or decoded.PlaceId ~= placeId or decoded.Schema ~= 4 then
        return {}, nil, false, {}
    end

    local servers = {}
    for _, s in ipairs(decoded.Servers or {}) do
        local norm = tbl12.NormalizeServerHopServer(s)
        if norm and norm.Id ~= jobId then
            servers[#servers + 1] = norm
        end
    end

    local regions = {}
    for k, region in pairs(decoded.Regions or {}) do
        if type(k) == "string" and typeof(region) == "table" then
            regions[k] = {}
            for k2, v in pairs(region) do
                if type(k2) == "string" and v == true then regions[k][k2] = true end
            end
        end
    end

    local cachedAt = tonumber(decoded.CachedAt) or 0
    local age = os.time() - cachedAt
    return servers, cachedAt, age >= 0 and age <= 120, regions
end

tbl12.SaveServerHopCache = function(servers, cachedAt)
    SH.LastCacheError = nil
    if not writefile then
        SH.LastCacheError = "writefile is unavailable"
        return false
    end
    local ok, err = pcall(function()
        writefile(SH.CachePath, HttpService:JSONEncode({
            Schema   = 4,
            PlaceId  = placeId,
            CachedAt = cachedAt or os.time(),
            Servers  = servers,
            Regions  = SH.CachedRegions,
        }))
    end)
    if not ok then SH.LastCacheError = tostring(err) end
    return ok
end

tbl12.FetchServerHopPage = function(url, key, label)
    label = label or "Roblox"
    local ok, body = pcall(game.HttpGet, game, url, true)
    if not ok then return nil, tostring(body) end
    if type(body) ~= "string" or body == "" then
        return nil, label .. " returned an empty response"
    end
    local ok2, decoded = pcall(HttpService.JSONDecode, HttpService, body)
    if not ok2 or typeof(decoded) ~= "table" then
        return nil, label .. " returned invalid JSON"
    end
    if key and typeof(decoded[key]) ~= "table" then
        local err = decoded.errors and decoded.errors[1]
        return nil, err and tostring(err.message) or label .. " returned no server data"
    end
    return decoded
end

tbl12.GetServerHopContinent = function(country)
    if type(country) ~= "string" then return end
    local needle = " " .. country:upper() .. " "
    for _, region in ipairs(SH.RegionNames) do
        local list = SH.ContinentCountries[region]
        if list and list:find(needle, 1, true) then return region end
    end
end

tbl12.RefreshServerHopRegions = function()
    local data, err = tbl12.FetchServerHopPage(
        "https://apis.rovalra.com/v1/datacenters/list",
        nil, "RoValra"
    )
    if not data then return false, err end

    local names = SH.RegionNames
    local seen = {}
    local regions = {}
    for i = 2, #names do regions[names[i]] = {} end

    for _, entry in ipairs(data) do
        local loc = entry.location
        local country = loc and loc.country
        local city    = loc and loc.city
        local cc = type(country) == "string" and country:upper() or nil
        local key = cc and city and (cc .. "\0" .. city)
        local continent = tbl12.GetServerHopContinent(cc)

        if entry.inactive ~= true and key and continent and not seen[key] then
            seen[key] = true
            regions[continent][#regions[continent] + 1] = {
                Country   = cc,
                City      = city,
                Latitude  = tonumber(loc.latLong and loc.latLong[1]),
                Longitude = tonumber(loc.latLong and loc.latLong[2]),
            }
        end
    end

    if not next(seen) then return false, "RoValra returned no active datacenters" end

    SH.Regions = regions
    SH.AutomaticCountry = nil
    SH.PlayerCoordinates = nil
    table.clear(SH.ResolvedRegions)
    return true
end

tbl12.GetServerHopPlayerCoordinates = function()
    local LocalizationService = game:GetService("LocalizationService")
    local ok, country = pcall(LocalizationService.GetCountryRegionForPlayerAsync, LocalizationService, LocalPlayer)
    if not ok or type(country) ~= "string" or country == "" then return end

    local cc = country:upper()
    if SH.AutomaticCountry == cc then
        local pc = SH.PlayerCoordinates
        return pc and pc.X, pc and pc.Y, cc
    end

    local lat, lon
    for _, url in ipairs({
        "https://cdn.jsdelivr.net/gh/google/dspl@master/samples/google/canonical/countries.csv",
        "https://raw.githubusercontent.com/google/dspl/master/samples/google/canonical/countries.csv",
    }) do
        local ok2, body = pcall(game.HttpGet, game, url, true)
        if ok2 and type(body) == "string" then
            lat, lon = body:match("\n" .. cc .. ",([%d%.%-]+),([%d%.%-]+),")
            if lat then break end
        end
    end

    local numLat = tonumber(lat)
    local numLon = tonumber(lon)
    local fallback = SH.CountryCoordinates[cc]
    if (not numLat) and fallback then
        numLat = fallback.X
        numLon = fallback.Y
    end

    SH.AutomaticCountry = cc
    SH.PlayerCoordinates = (numLat and numLon) and Vector2.new(numLat, numLon) or nil
    table.clear(SH.ResolvedRegions)
    return numLat, numLon, cc
end

tbl12.GetServerHopRegions = function()
    if not next(SH.Regions) then
        local ok, err = tbl12.RefreshServerHopRegions()
        if not ok then return nil, err end
    end

    local region = tbl9.ServerHopRegion
    if region ~= "Automatic" and not SH.Regions[region] then
        tbl9.ServerHopRegion = "Automatic"
        region = "Automatic"
        if options and options.ServerHopRegion then
            options.ServerHopRegion:SetValue("Automatic")
        end
    end

    local lat, lon, cc = tbl12.GetServerHopPlayerCoordinates()
    local cacheKey = cc and (cc .. "\0" .. region)
    if cacheKey and SH.ResolvedRegions[cacheKey] then
        return SH.ResolvedRegions[cacheKey]
    end

    local latRad = lat and math.rad(lat)

    local function haversine(entry)
        if not (latRad and entry.Latitude and entry.Longitude) then return math.huge end
        local dLat = math.rad(entry.Latitude - lat)
        local dLon = math.rad(entry.Longitude - lon)
        local a = math.sin(dLat / 2) ^ 2
                  + math.cos(latRad) * math.cos(math.rad(entry.Latitude)) * math.sin(dLon / 2) ^ 2
        return a
    end

    if region == "Automatic" then
        region = tbl12.GetServerHopContinent(cc)
        if not region and lat then
            local best, bestD = nil, math.huge
            for i = 2, #SH.RegionNames do
                local name = SH.RegionNames[i]
                for _, entry in ipairs(SH.Regions[name] or {}) do
                    local d = haversine(entry)
                    if d < bestD then bestD = d; best = name end
                end
            end
            region = best
        end
    end

    local list = SH.Regions[region]
    if not list or #list == 0 then return end

    local sorted = table.clone(list)
    table.sort(sorted, function(a, b)
        local da = haversine(a)
        local db = haversine(b)
        if da == db then
            local aHome = a.Country == cc
            if aHome ~= (b.Country == cc) then return aHome end
            return tostring(a.City) < tostring(b.City)
        end
        return da < db
    end)

    if cacheKey then SH.ResolvedRegions[cacheKey] = sorted end
    return sorted
end

tbl12.FetchServerHopRegionIds = function(entry)
    local url = "https://apis.rovalra.com/v1/servers/region?place_id=" .. placeId
             .. "&country=" .. HttpService:UrlEncode(entry.Country)
             .. "&cursor=0"
    if entry.City then
        url ..= "&city=" .. HttpService:UrlEncode(entry.City)
    end

    local data, err = tbl12.FetchServerHopPage(url, "servers", "RoValra")
    if not data then return nil, err end

    local ids = {}
    for _, s in ipairs(data.servers) do
        local sid = s.server_id or s.id
        if type(sid) == "string" and sid ~= jobId then ids[sid] = true end
    end
    return ids
end

tbl12.FetchServerHopServersPage = function(cursor, token)
    local mn = math.min(tbl9.ServerHopMinPlayers, tbl9.ServerHopMaxPlayers)
    local order = (tbl9.ServerHopSort == "Highest Players" or mn >= Players.MaxPlayers / 2)
        and "Desc" or "Asc"

    local url = "https://games.roblox.com/v1/games/" .. placeId
             .. "/servers/Public?sortOrder=" .. order
             .. "&limit=100&excludeFullGames=" .. tostring(not tbl8.ServerHopIncludeFull)
    if type(cursor) == "string" and cursor ~= "" then
        url ..= "&cursor=" .. HttpService:UrlEncode(cursor)
    end

    local data, err
    repeat
        if flag11 or token ~= SH.Token then return end
        data, err = tbl12.FetchServerHopPage(url, "data", "Roblox")
        if flag11 or token ~= SH.Token then return end
        if not data then task.wait(0.25) end
    until data or flag11 or token ~= SH.Token

    if flag11 or token ~= SH.Token then return end
    if not data then SH.LastFetchError = err return end

    local servers = {}
    for _, raw in ipairs(data.data) do
        local norm = tbl12.NormalizeServerHopServer(raw)
        if norm and norm.Id ~= jobId then servers[#servers + 1] = norm end
    end
    return servers, data.nextPageCursor
end

tbl12.FilterServerHopServers = function(list, okIds)
    local out = {}
    for _, s in ipairs(list) do
        if tbl12.IsServerHopCandidate(s, okIds) then out[#out + 1] = s end
    end
    return out
end

tbl12.SelectServerHopServer = function(list)
    if #list == 0 then return end
    if tbl9.ServerHopSort == "Closest Datacenter" or tbl9.ServerHopSort == "Lowest Ping"
        or tbl9.ServerHopSort == "Random" then
        return list[math.random(1, #list)]
    end

    table.sort(list, function(a, b)
        local x, y
        if tbl9.ServerHopSort == "Lowest Players" then
            x, y = a.Playing, b.Playing
        elseif tbl9.ServerHopSort == "Highest Players" then
            x, y = -a.Playing, -b.Playing
        elseif tbl9.ServerHopSort == "Highest FPS" then
            x, y = -(a.FPS or 0), -(b.FPS or 0)
        else
            x, y = a.Ping or math.huge, b.Ping or math.huge
        end
        if x == y then return a.Id < b.Id end
        return x < y
    end)
    return list[1]
end

tbl12.UpdateServerHopButton = function()
    if not SH.Button then return end
    local busy = SH.Busy or SH.Pending or SH.Retrying
    SH.Button.DoubleClick = not busy
    SH.Button:SetText(busy and "Cancel Server Hop" or "Server-hop")
end

tbl12.CancelServerHop = function()
    SH.Token = SH.Token + 1
    SH.AutoToken = SH.AutoToken + 1
    local wasPending = SH.Pending
    SH.Busy       = false
    SH.Pending    = nil
    SH.Retrying   = false
    SH.Cancelled  = true

    if SH.Notification then
        SH.Notification:Destroy()
        SH.Notification = nil
    end
    tbl12.UpdateServerHopButton()

    if not flag11 then
        if wasPending then
            fn18("Server-hop retries cancelled. Roblox may still complete the teleport already requested.")
        end
        if tbl8.AutoServerHop then tbl12.ScheduleAutoServerHop() end
    end
end

tbl12.RetryFullServerHop = function()
    if flag11 or SH.Cancelled then return false end
    local pending = SH.Pending
    if not pending then return SH.Retrying == true end

    SH.Pending = nil
    SH.Rejected[pending.ServerId] = true
    SH.Busy = false
    SH.Retrying = true
    local token = SH.Token
    tbl12.UpdateServerHopButton()
    fn18("Server is full; trying another server in the selected region.")

    task.delay(1, function()
        if flag11 or token ~= SH.Token then return end
        SH.Retrying = false
        if not flag11 then
            tbl12.ServerHop(pending.AntiLag, pending.RestartScript)
        end
    end)
    return true
end

tbl12.ServerHop = function(antiLag, reload)
    if flag11 then return false end
    if SH.Busy or SH.Pending or SH.Retrying then
        fn18("A server-hop is already in progress.")
        return false
    end

    SH.Token = SH.Token + 1
    local token = SH.Token

    local function alive()
        return not flag11 and token == SH.Token
    end

    SH.Busy = true
    SH.Cancelled = false
    tbl12.UpdateServerHopButton()

    local notification
    if Library and Library.Notify then
        notification = Library:Notify({
            Title = "nLhe",
            Description = "Attempting to serverhop..",
            Persist = true,
            Time = math.huge,
            Duration = math.huge,
        })
    end
    if not alive() then
        if notification then notification:Destroy() end
        return false
    end
    SH.Notification = notification

    local ok, result = pcall(function()
        local regions, err = tbl12.GetServerHopRegions()
        if not alive() then return false end
        if not regions then
            fn18("Couldn't determine the server-hop region." .. (err and (" Error: " .. err) or ""))
            return false
        end

        local cached, cachedAt, fresh, cachedRegions = tbl12.LoadServerHopCache()
        if not alive() then return false end
        if not fresh then cached = {} end

        local candidates = {}
        local lastErr = nil
        local datacentersChecked = 0

        SH.CachedRegions = cachedRegions or {}
        SH.LastFetchError = nil

        local seenIds = {}
        for _, s in ipairs(cached) do seenIds[s.Id] = true end

        local function searchPool(pool)
            for _, entry in ipairs(regions) do
                if not alive() then return {} end
                local key = entry.Country .. "\0" .. tostring(entry.City or "")
                local ids = SH.CachedRegions[key]
                if not ids then
                    if datacentersChecked > 0 then task.wait(1) end
                    if not alive() then return {} end
                    ids, lastErr = tbl12.FetchServerHopRegionIds(entry)
                    if not alive() then return {} end
                    datacentersChecked += 1
                    if not ids then return {} end
                    SH.CachedRegions[key] = ids
                end
                local filtered = tbl12.FilterServerHopServers(pool, ids)
                if #filtered > 0 then return filtered end
            end
            return {}
        end

        if fresh and #tbl12.FilterServerHopServers(cached) > 0 then
            candidates = searchPool(cached)
        end

        if #candidates == 0 and not lastErr then
            table.clear(cached)
            table.clear(seenIds)
            local cursor = ""

            for i = 1, 10 do
                if i > 1 then task.wait(1) end
                if not alive() then return false end

                local servers, nextCursor = tbl12.FetchServerHopServersPage(cursor, token)
                if not alive() then return false end
                if not servers then break end
                cachedAt = os.time()

                for _, s in ipairs(servers) do
                    if not seenIds[s.Id] then
                        seenIds[s.Id] = true
                        cached[#cached + 1] = s
                    end
                end

                if #tbl12.FilterServerHopServers(servers) > 0 then
                    candidates = searchPool(servers)
                    if #candidates > 0 or lastErr then break end
                end

                if type(nextCursor) ~= "string" or nextCursor == "" then break end
                cursor = nextCursor
            end
        end

        if not alive() then return false end

        if #candidates == 0 then
            if lastErr then
                fn18("Region search failed. Error: " .. lastErr)
            elseif SH.LastFetchError then
                fn18("Roblox server search stopped. Error: " .. SH.LastFetchError)
            elseif #cached == 0 then
                fn18("Roblox didn't return any public servers. Try again in a few seconds.")
            else
                fn18(("Checked %d servers across %d datacenters, but none matched %d-%d players in %s.")
                    :format(#cached, datacentersChecked,
                        math.min(tbl9.ServerHopMinPlayers, tbl9.ServerHopMaxPlayers),
                        math.max(tbl9.ServerHopMinPlayers, tbl9.ServerHopMaxPlayers),
                        tbl9.ServerHopRegion))
            end
            if cachedAt then tbl12.SaveServerHopCache(cached, cachedAt) end
            return false
        end

        local picked = tbl12.SelectServerHopServer(candidates)
        for i = #cached, 1, -1 do
            if cached[i].Id == picked.Id then
                table.remove(cached, i)
                break
            end
        end

        local saved = tbl12.SaveServerHopCache(cached, cachedAt)
        if not alive() then return false end
        if not saved then
            fn18("Server cache couldn't be saved: " .. tostring(SH.LastCacheError))
        end

        tbl12.QueueTeleport(antiLag, reload)
        if not alive() then return false end

        SH.Pending = { ServerId = picked.Id, AntiLag = antiLag, RestartScript = reload }
        local ok2, err2 = pcall(TeleportService.TeleportToPlaceInstance,
            TeleportService, placeId, picked.Id, LocalPlayer)

        if not alive() then return false end
        if not ok2 then
            local msg = tostring(err2)
            if msg:lower():find("full", 1, true) then
                return tbl12.RetryFullServerHop()
            end
            SH.Pending = nil
            fn18("Server-hop failed: " .. msg)
        end
        return ok2
    end)

    if not alive() then return false end
    SH.Busy = false
    if notification then notification:Destroy() end
    SH.Notification = nil
    if not ok then SH.Pending = nil end

    tbl12.UpdateServerHopButton()
    if not ok then
        fn18("Server-hop failed: " .. tostring(result))
        return false
    end
    return result
end

tbl12.ScheduleAutoServerHop = function(delayTime)
    SH.AutoToken = SH.AutoToken + 1
    local autoToken = SH.AutoToken
    if flag11 or not tbl8.AutoServerHop then return end

    task.delay(delayTime or tbl9.AutoServerHopTime, function()
        if flag11 or autoToken ~= SH.AutoToken or not tbl8.AutoServerHop then return end
        if not tbl12.ServerHop(tbl8.RejoinWithAntiLag ~= false, tbl8.RejoinWithScript)
           and autoToken == SH.AutoToken and tbl8.AutoServerHop then
            tbl12.ScheduleAutoServerHop(math.min(15, tbl9.AutoServerHopTime))
        end
    end)
end

TeleportService.TeleportInitFailed:Connect(function(player, result, message, _id, info)
    if player ~= LocalPlayer or flag11 then return end
    if SH.Cancelled or (SH.Busy and not SH.Pending) then return end
    if SH.Pending and info and info.ServerInstanceId ~= "" and info.ServerInstanceId ~= SH.Pending.ServerId then
        return
    end

    local full = result == Enum.TeleportResult.GameFull
        or tostring(message):lower():find("full", 1, true)

    if full then
        if tbl12.RetryFullServerHop() then return end
    else
        SH.Pending = nil
    end

    tbl12.UpdateServerHopButton()
    if tbl8.AutoServerHop then tbl12.ScheduleAutoServerHop(10) end
end)


-- ============================================================
-- UI
-- ============================================================
do
    local HomeTab = Tabs and Tabs.Home
    if not HomeTab then
        warn("[Script] Tabs.Home not found — skipped")
        return
    end

    local Script = HomeTab:AddRightGroupbox("Script", "scroll")

    Script:AddButton({
        Text = "Unload Script",
        Func = function()
            if Library and Library.Unload then Library:Unload() end
        end,
        DoubleClick = true,
    })

    Script:AddButton({
        Text = "Rejoin",
        Func = function()
            tbl12.Rejoin(tbl8.RejoinWithAntiLag ~= false, tbl8.RejoinWithScript)
        end,
        DoubleClick = true,
    })

    SH.Button = Script:AddButton({
        Text = "Server-hop",
        Func = function()
            if SH.Busy or SH.Pending or SH.Retrying then
                tbl12.CancelServerHop()
            else
                task.defer(tbl12.ServerHop, tbl8.RejoinWithAntiLag ~= false, tbl8.RejoinWithScript)
            end
        end,
        DoubleClick = true,
    })

    Script:AddDivider("Options")

    Script:AddToggle("AutoRj", {
        Text = "Auto Rejoin",
        Tooltip = "Rejoins immediately as soon as you get kicked",
        Callback = function(autoRejoin) tbl8.AutoRejoin = autoRejoin end,
    })

    Script:AddToggle("RejoinWithAntiLag", {
        Text = "Join with Anti-Lag",
        Tooltip = "Queues anti-lag on next teleport (server-hop or rejoin)",
        Default = true,
        Callback = function(rejoinWithAntiLag) tbl8.RejoinWithAntiLag = rejoinWithAntiLag end,
    })

    Script:AddToggle("RejoinWithScript", {
        Text = "Join with script",
        Tooltip = "Executes the script for you after teleporting (server-hop or rejoin)",
        Callback = function(rejoinWithScript)
            if not reloadPath and rejoinWithScript then
                tbl8.RejoinWithScript = false
                task.defer(function() toggles.RejoinWithScript:SetValue(false) end)
                fn18("Local reload is unavailable: this executor must support readfile and writefile")
                return
            end
            tbl8.RejoinWithScript = rejoinWithScript
        end,
    })

    Script:AddDivider("Server-Hop Settings")

    Script:AddDropdown("ServerHopRegion", {
        Values = SH.RegionNames,
        Default = 1,
        Multi = false,
        Searchable = true,
        Text = "Preferred Region",
        Tooltip = "Automatic chooses closest continent first",
        Callback = function(region) tbl9.ServerHopRegion = region end,
    })

    Script:AddDropdown("ServerHopSort", {
        Values = { "Closest Datacenter", "Lowest Players", "Highest Players", "Highest FPS", "Random" },
        Default = 1, Multi = false, Text = "Selection",
        Callback = function(sort) tbl9.ServerHopSort = sort end,
    })

    Script:AddSlider("ServerHopMinPlayers", {
        Text = "Minimum Players", Default = 0, Min = 0, Max = Players.MaxPlayers,
        Rounding = 0, Compact = true,
        Callback = function(v) tbl9.ServerHopMinPlayers = v end,
    })

    Script:AddSlider("ServerHopMaxPlayers", {
        Text = "Maximum Players", Default = Players.MaxPlayers, Min = 0, Max = Players.MaxPlayers,
        Rounding = 0, Compact = true,
        Callback = function(v) tbl9.ServerHopMaxPlayers = v end,
    })
end

local TargetGroup = Tabs.Target:AddLeftGroupbox("Target Selector", "user")
local NoBlobGroup = Tabs.Target:AddRightGroupbox("No blobman methods", "axe")
local BlobGroup = Tabs.Target:AddRightGroupbox("Blob methods", "axe")

local function FWD(parent, childName, time)
    if not parent then return nil end
    return parent:FindFirstChild(childName) or parent:WaitForChild(childName, time or 5)
end

local function GetMagnitude(a, b)
    if not a or not b then return math.huge end
    return (a.Position - b.Position).Magnitude
end

local function CheckForPartOwner(part)
    if not part then return false end
    local po = part:FindFirstChild("PartOwner")
    return po and po.Value == LocalPlayer.Name
end

local function sno(part)
    if not part or not part.Parent then return end
    pcall(function()
        SetNetworkOwner:FireServer(part, part.CFrame)
    end)
end

local function unsno(part)
    if not part or not part.Parent then return end
    pcall(function()
        DestroyGrabLine:FireServer(part)
    end)
end

local function CFP(parent, name)
    return parent and parent:FindFirstChild(name) ~= nil
end

local function SpawnToy(toyName)
    local char = LocalPlayer.Character
    local hrp  = char and char:FindFirstChild("HumanoidRootPart")
    if not hrp then return nil end
    local spawnCF = hrp.CFrame * CFrame.new(0, 14, 20)
    local container = inv
    if not container then return nil end

    local spawnedObject = nil
    local conn
    conn = container.ChildAdded:Connect(function(child)
        if child.Name == toyName then
            spawnedObject = child
        end
    end)

    task.spawn(function()
        pcall(function()
            SpawnToyRemote:InvokeServer(toyName, spawnCF, Vector3.zero)
        end)
    end)

    local start = tick()
    repeat task.wait() until spawnedObject or (tick() - start) > 2.5
    if conn then conn:Disconnect() end
    return spawnedObject
end

local PS_Enabled  = false
local PS_Thread   = nil

local function PS_Start()
    if PS_Thread then
        task.cancel(PS_Thread)
        PS_Thread = nil
    end

    local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
    local hrp  = char:WaitForChild("HumanoidRootPart", 5)
    if not hrp then return end

    pcall(function() setfflag("S2PhysicsSenderRate", 1000) end)

    local cooldown = 0
    local syncing  = false

    PS_Thread = task.spawn(function()
        while PS_Enabled and LocalPlayer.Character == char and task.wait(1/240) do
            if syncing then
                task.wait()
                continue
            end

            if cooldown <= 0 then
                syncing = true
                pcall(sethiddenproperty, hrp, "PhysicsRepRootPart", nil)
                task.wait(0.1)
                pcall(sethiddenproperty, hrp, "PhysicsRepRootPart", hrp)
                syncing = false
                cooldown = 20
            else
                cooldown = cooldown - 1
                pcall(sethiddenproperty, hrp, "PhysicsRepRootPart", hrp)
            end
        end
    end)
end

local function PS_Stop()
    PS_Enabled = false
    if PS_Thread then
        task.cancel(PS_Thread)
        PS_Thread = nil
    end
    pcall(function() setfflag("S2PhysicsSenderRate", 20) end)
end

selectedPlrName = nil
local _lastListStr = ""

local function getPlayerList()
    local list = {}
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= LocalPlayer then
            table.insert(list, p.DisplayName .. " (@" .. p.Name .. ")")
        end
    end
    return list
end

local function getPlayerByName(value)
    if not value or value == "" then return nil end
    local username = value:match("@([^)]+)")
    if username then return Players:FindFirstChild(username) end
    return Players:FindFirstChild(value)
end

local function refreshList(force)
    if not Options or not Options.TargetPlayer then return end
    local list = getPlayerList()
    local newStr = table.concat(list, "|")
    if not force and newStr == _lastListStr then return end
    _lastListStr = newStr

    pcall(function()
        Options.TargetPlayer:SetValues(list)
    end)

    if selectedPlrName and not Players:FindFirstChild(selectedPlrName) then
        selectedPlrName = nil
        pcall(function()
            Options.TargetPlayer:SetValue("")
        end)
        Library:Notify({Title = "Target", Description = "Target left the game", Time = 3})
    end
end

function getSelectedPlayer()
    if not selectedPlrName then return nil end
    return Players:FindFirstChild(selectedPlrName)
end

TargetGroup:AddDropdown("TargetPlayer", {
    Text = "Target",
    Values = getPlayerList(),
    Default = "",
    Multi = false,
    Callback = function(value)
        local plr = getPlayerByName(value)
        selectedPlrName = plr and plr.Name or nil
        Library:Notify({
            Title = "Target",
            Description = plr and ("Selected: " .. plr.DisplayName) or "Cleared",
            Time = 2,
        })
    end,
})

TargetGroup:AddButton({
    Text = "Refresh List",
    Func = function()
        _lastListStr = ""
        refreshList(true)
        Library:Notify({Title = "Target", Description = "Refreshed", Time = 2})
    end,
})

Players.PlayerAdded:Connect(function()
    task.wait(0.5)
    _lastListStr = ""
    refreshList(true)
end)

Players.PlayerRemoving:Connect(function()
    task.wait(0.1)
    _lastListStr = ""
    refreshList(true)
end)

task.spawn(function()
    while true do
        task.wait(3)
        refreshList()
    end
end)

NoBlobGroup:AddToggle("AntiBlobSeatToggle", {
    Text = "Don't Give Chance to Seat on Blob",
    Default = false,
    Callback = function(v)
        _G._AntiBlobSeatEnabled = v and true or false

        if _G._AntiBlobSeatThread then
            task.cancel(_G._AntiBlobSeatThread)
            _G._AntiBlobSeatThread = nil
        end

        if v then
            local Players = game:GetService("Players")
            local RS = game:GetService("ReplicatedStorage")
            local plr = Players.LocalPlayer
            local SetNetworkOwner = RS:WaitForChild("GrabEvents"):WaitForChild("SetNetworkOwner")

            local function sno(part)
                pcall(function() SetNetworkOwner:FireServer(part, part.CFrame) end)
            end

            _G._AntiBlobSeatThread = task.spawn(function()
                while _G._AntiBlobSeatEnabled do
                    task.wait(0.1)

                    local target = getSelectedPlayer()
                    if not target or not target.Character or not target.Character:FindFirstChild("Humanoid") then
                        continue
                    end

                    local char = plr.Character
                    local hrp = char and char:FindFirstChild("HumanoidRootPart")
                    if not hrp then continue end

                    local targetHum = target.Character:FindFirstChild("Humanoid")
                    if targetHum and targetHum.SeatPart ~= nil then
                        local oldCF = hrp.CFrame
                        task.wait(0.1)
                        local targetRoot = target.Character:FindFirstChild("HumanoidRootPart")
                        if not targetRoot then continue end
                        hrp.CFrame = targetRoot.CFrame * CFrame.new(0, 5, 5)
                        task.wait(0.2)
                        local targetHead = target.Character:FindFirstChild("Head")
                        if targetHead then sno(targetHead) end
                        hrp.CFrame = oldCF
                        task.wait(0.5)
                    end
                end
            end)
        end
    end,
})

NoBlobGroup:AddButton({
    Text = "Check For Friend Here",
    Func = function()
        local Players = game:GetService("Players")
        local target = getSelectedPlayer()
        if not target then
            Library:Notify({ Title = "Error!", Description = "Player not found!", Time = 3 })
            return
        end

        local suc, friendsList = pcall(function()
            return Players:GetFriendsAsync(target.UserId)
        end)

        if not suc or not friendsList then
            Library:Notify({ Title = "Error!", Description = "Failed to get friends list", Time = 3 })
            return
        end

        local friends = {}
        for _, fr in pairs(friendsList:GetCurrentPage()) do
            table.insert(friends, fr.Username)
        end

        local foundAny = false
        for _, v in pairs(Players:GetPlayers()) do
            for _, friendName in pairs(friends) do
                if v.Name == friendName then
                    foundAny = true
                    Library:Notify({
                        Title = "Friend found",
                        Description = v.Name .. " (" .. v.DisplayName .. ")",
                        Time = 5,
                    })
                end
            end
        end

        if not foundAny then
            Library:Notify({
                Title = "No friends here",
                Description = "None of " .. target.Name .. "'s friends are on this server",
                Time = 5,
            })
        end
    end,
})

local LocalPlayer = game:GetService("Players").LocalPlayer
local RunService   = game:GetService("RunService")

local loopGrabKick   = false
local loopGrabThread = nil
local RagdollKickToggle = nil

local function Huge()
    return math.huge, math.huge, math.huge
end

local function GetMagnitude(a, b)
    return (a.Position - b.Position).Magnitude
end

local function FWD(parent, name, timeout)
    return parent:FindFirstChild(name) or parent:WaitForChild(name, timeout or 5)
end

local function CFP(parent, name)
    return parent:FindFirstChild(name) ~= nil
end

local function RenameInShop(Instance, OriginalName, ToRename)
    local index = nil
    local ToCheckName = Instance.Name or Instance
    for i, v in pairs(inv:GetChildren()) do
        if v.Name == ToCheckName then index = i end
    end
    if index == nil then return end
    local contents = LocalPlayer.PlayerGui.MenuGui.Menu.TabContents.ToyDestroy.Contents
    for i, v in ipairs(contents:GetChildren()) do
        if v.Name == OriginalName and i == index then
            local view = v.ViewItemButton
            view.Text = ToRename
            view.TextScaled = true
            view.LowResImage.Image = ""
        end
    end
end

local function RunRagdollKick()
    local char = LocalPlayer.Character
    local hrp  = char and char:FindFirstChild("HumanoidRootPart")
    if not char or not hrp then return end

    local TargetPLR, Head, Root, Hum
    local Pallete

    local function SpawnPallete()
        Pallete = SpawnToy("PalletLightBrown")
        if not Pallete then return end
        local SoundPart = FWD(Pallete, "SoundPart")
        repeat sno(SoundPart) task.wait(0.05) until CFP(SoundPart, "PartOwner") or not loopGrabKick
        for _, v in pairs(Pallete:GetDescendants()) do
            if v:IsA("BasePart") then
                v.CanCollide   = false
                v.Transparency = 0.8
            end
        end
        Pallete.Name = "RagdollPalete"
        task.delay(1, RenameInShop, Pallete, "PalletLightBrown", "Ragdoll")
        local bv = Instance.new("BodyVelocity")
        bv.MaxForce = Vector3.new(0, math.huge, 0)
        bv.Velocity = Vector3.new(0, 900, 0)
        bv.Parent   = Pallete.SoundPart
        return Pallete
    end

    TargetPLR = getSelectedPlayer()
    Head = TargetPLR and TargetPLR.Character and TargetPLR.Character:FindFirstChild("Head")
    Root = TargetPLR and TargetPLR.Character and TargetPLR.Character:FindFirstChild("HumanoidRootPart")

    Pallete = inv:FindFirstChild("RagdollPalete")
    if not Pallete then
        Pallete = SpawnPallete()
    end

    while loopGrabKick and RunService.PreSimulation:Wait() do
        TargetPLR = getSelectedPlayer()
        if not TargetPLR then continue end

        Head = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Head")
        Root = TargetPLR.Character and TargetPLR.Character:FindFirstChild("HumanoidRootPart")
        Hum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")

        local BodyPos = Root and Root:FindFirstChild("BodyPosition")

        if (Head and Hum and Root and Hum.Health ~= 0) and GetMagnitude(hrp, Root) <= 30 then
            if not BodyPos then
                BodyPos = Instance.new("BodyPosition")
                BodyPos.MaxForce = Vector3.new(Huge())
                BodyPos.Parent   = Root
                BodyPos.P        = 75000
                BodyPos.D        = 12000
                BodyPos.Position = hrp.Position + Vector3.new(0, 15, 0)
            end
            BodyPos.Position = hrp.Position + Vector3.new(0, 15, 0)

            if (Root.Position.Y <= hrp.Position.Y + 15) and TargetPLR.IsHeld.Value then
                for _, v in pairs(TargetPLR.Character:GetChildren()) do
                    if v:IsA("Part") then
                        v.CFrame = hrp.CFrame * CFrame.new(0, 15, 0)
                    end
                end
            end

            Root.AssemblyAngularVelocity, Root.AssemblyLinearVelocity = Vector3.zero, Vector3.zero
            Hum.PlatformStand = true

            sno(Root)
            RunService.RenderStepped:Wait()
            sno(Root)
            unsno(Root)
            RunService.RenderStepped:Wait()
            sno(Root)

            Pallete = inv:FindFirstChild("RagdollPalete")
            if not Pallete then
                Pallete = SpawnPallete()
            end
            if CFP(Hum, "Ragdolled") and not Hum.Ragdolled.Value then
                Pallete.SoundPart.Position = Root.Position
            end

            RunService.RenderStepped:Wait()
            unsno(Root)

        else
            if not Head or not Hum or Hum.Health == 0 then
                TargetPLR.CharacterAdded:Wait()
                Head = FWD(TargetPLR.Character, "Head", 5)
                Hum  = FWD(TargetPLR.Character, "Humanoid", 5)
                BodyPos = Instance.new("BodyPosition")
                BodyPos.MaxForce = Vector3.new(Huge())
                BodyPos.Parent   = Root
                BodyPos.P        = 75000
                BodyPos.D        = 12000
                BodyPos.Position = hrp.Position + Vector3.new(0, 15, 0)
            end

            local oldCF = hrp.CFrame
            while (Head and Hum and Hum.Health ~= 0) and loopGrabKick do
                RunService.PreSimulation:Wait()
                TargetPLR = getSelectedPlayer()
                if not TargetPLR then break end
                if TargetPLR.InPlot.Value then continue end
                Head = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Head")
                Hum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")
                if not Head or not Hum then break end
                char:PivotTo(Head.CFrame * CFrame.new(0, 10, 0))
                sno(Head)
                if CheckForPartOwner(Head) then break end
            end
            hrp.CFrame = oldCF

            if Head and CheckForPartOwner(Head) then
                for _, v in pairs(TargetPLR.Character:GetChildren()) do
                    if v:IsA("BasePart") then
                        v.CFrame = hrp.CFrame * CFrame.new(0, 15, 0)
                    end
                end
            end
        end
    end

    if Root then
        for _, v in pairs(Root:GetChildren()) do
            if v.Name == "BodyPosition" then
                v:Destroy()
            end
        end
    end
end

RagdollKickToggle = NoBlobGroup:AddToggle("RagdollKick", {
    Text    = "RagdollKick",
    Default = false,
    Callback = function(value)
        loopGrabKick = value
        if value then
            if not getSelectedPlayer() then
                Library:Notify({Title = "RagdollKick", Description = "цели нету хд", Duration = 3})
                loopGrabKick = false
                if RagdollKickToggle then RagdollKickToggle:Set(false) end
                return
            end
            loopGrabThread = task.spawn(RunRagdollKick)
        else
            if loopGrabThread then
                task.cancel(loopGrabThread)
                loopGrabThread = nil
            end
            local t = getSelectedPlayer()
            local r = t and t.Character and t.Character:FindFirstChild("HumanoidRootPart")
            if r then
                for _, v in pairs(r:GetChildren()) do
                    if v.Name == "BodyPosition" then v:Destroy() end
                end
            end
        end
    end,
})

-- ============================================================
-- ==== LoopGrab V4 — Ragdoll-only (группа NoBlobGroup) ====
-- ============================================================

local LocalPlayer = game:GetService("Players").LocalPlayer
local RunService   = game:GetService("RunService")

local loopGrabV4      = false
local loopGrabThread  = nil
local LoopGrabV4Toggle = nil

local function Huge()
    return math.huge, math.huge, math.huge
end

local function GetMagnitude(a, b)
    return (a.Position - b.Position).Magnitude
end

local function FWD(parent, name, timeout)
    return parent:FindFirstChild(name) or parent:WaitForChild(name, timeout or 5)
end

local function CFP(parent, name)
    return parent:FindFirstChild(name) ~= nil
end

local function RunLoopGrabV4()
    local char = LocalPlayer.Character
    local hrp  = char and char:FindFirstChild("HumanoidRootPart")
    if not char or not hrp then return end

    local TargetPLR, Head, Root, Hum

    while loopGrabV4 and RunService.PreSimulation:Wait() do
        TargetPLR = getSelectedPlayer()
        if not TargetPLR then continue end

        Head = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Head")
        Root = TargetPLR.Character and TargetPLR.Character:FindFirstChild("HumanoidRootPart")
        Hum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")

        local BodyPos = Root and Root:FindFirstChild("BodyPosition")

        -- Дистанция входа в удержание: 26
        if (Head and Hum and Root and Hum.Health ~= 0) and GetMagnitude(hrp, Root) <= 26 then
            if not BodyPos then
                BodyPos = Instance.new("BodyPosition")
                BodyPos.MaxForce = Vector3.new(Huge())
                BodyPos.Parent   = Root
                BodyPos.P        = 75000
                BodyPos.D        = 6000
                BodyPos.Position = hrp.Position + Vector3.new(0, 21, 0)
            end
            BodyPos.Position = hrp.Position + Vector3.new(0, 21, 0)

            if (Root.Position.Y <= hrp.Position.Y + 15) and TargetPLR.IsHeld.Value then
                for _, v in pairs(TargetPLR.Character:GetChildren()) do
                    if v:IsA("Part") then
                        v.CFrame = hrp.CFrame * CFrame.new(0, 21, 0)
                    end
                end
            end

            Root.AssemblyAngularVelocity, Root.AssemblyLinearVelocity = Vector3.zero, Vector3.zero
            Hum.PlatformStand = true

            sno(Root)
            sno(Root)
            unsno(Root)
            sno(Root)
            unsno(Root)

        else
            if not Head or not Hum or Hum.Health == 0 then
                TargetPLR.CharacterAdded:Wait()
                Head = FWD(TargetPLR.Character, "Head", 5)
                Hum  = FWD(TargetPLR.Character, "Humanoid", 5)
                BodyPos = Instance.new("BodyPosition")
                BodyPos.MaxForce = Vector3.new(Huge())
                BodyPos.Parent   = Root
                BodyPos.P        = 75000
                BodyPos.D        = 6000
                BodyPos.Position = hrp.Position + Vector3.new(0, 21, 0)
            end

            local oldCF = hrp.CFrame
            while (Head and Hum and Hum.Health ~= 0) and loopGrabV4 do
                RunService.PreSimulation:Wait()
                TargetPLR = getSelectedPlayer()
                if not TargetPLR then break end
                if TargetPLR.InPlot.Value then continue end
                Head = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Head")
                Hum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")
                Root = TargetPLR.Character and TargetPLR.Character:FindFirstChild("HumanoidRootPart")
                if not Head or not Hum then break end

                -- ТЕЛЕПОРТ ПОД ЦЕЛЬ (-11)
                char:PivotTo(Head.CFrame * CFrame.new(0, -11, 0))
                sno(Head)
                if Root then sno(Root) end

                if CheckForPartOwner(Head) then break end
            end
            hrp.CFrame = oldCF

            if Head and CheckForPartOwner(Head) then
                for _, v in pairs(TargetPLR.Character:GetChildren()) do
                    if v:IsA("BasePart") then
                        v.CFrame = hrp.CFrame * CFrame.new(0, 21, 0)
                    end
                end
            end
        end
    end

    if Root then
        for _, v in pairs(Root:GetChildren()) do
            if v.Name == "BodyPosition" then
                v:Destroy()
            end
        end
    end
end

LoopGrabV4Toggle = NoBlobGroup:AddToggle("LoopGrabV4", {
    Text    = "Loop Grab V4",
    Default = false,
    Callback = function(value)
        loopGrabV4 = value
        if value then
            if not getSelectedPlayer() then
                Library:Notify({Title = "Loop Grab V4", Description = "цели нету хд", Duration = 3})
                loopGrabV4 = false
                if LoopGrabV4Toggle then LoopGrabV4Toggle:Set(false) end
                return
            end
            loopGrabThread = task.spawn(RunLoopGrabV4)
        else
            if loopGrabThread then
                task.cancel(loopGrabThread)
                loopGrabThread = nil
            end
            local t = getSelectedPlayer()
            local r = t and t.Character and t.Character:FindFirstChild("HumanoidRootPart")
            if r then
                for _, v in pairs(r:GetChildren()) do
                    if v.Name == "BodyPosition" then v:Destroy() end
                end
            end
        end
    end,
})

-- ============================================================
-- ==== LoopGrab V5 — Ragdoll-only (гибрид: удержание V2 + догон V4) ====
-- ============================================================

local LocalPlayer = game:GetService("Players").LocalPlayer
local RunService   = game:GetService("RunService")

local loopGrabV5       = false
local loopGrabThreadV5 = nil
local LoopGrabV5Toggle = nil

local function Huge()
    return math.huge, math.huge, math.huge
end

local function GetMagnitude(a, b)
    return (a.Position - b.Position).Magnitude
end

local function FWD(parent, name, timeout)
    return parent:FindFirstChild(name) or parent:WaitForChild(name, timeout or 5)
end

local function CFP(parent, name)
    return parent:FindFirstChild(name) ~= nil
end

local function RunLoopGrabV5()
    local char = LocalPlayer.Character
    local hrp  = char and char:FindFirstChild("HumanoidRootPart")
    if not char or not hrp then return end

    local TargetPLR, Head, Root, Hum

    while loopGrabV5 and RunService.PreSimulation:Wait() do
        TargetPLR = getSelectedPlayer()
        if not TargetPLR then continue end

        Head = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Head")
        Root = TargetPLR.Character and TargetPLR.Character:FindFirstChild("HumanoidRootPart")
        Hum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")

        local BodyPos = Root and Root:FindFirstChild("BodyPosition")

        -- Дистанция входа в удержание: 26
        if (Head and Hum and Root and Hum.Health ~= 0) and GetMagnitude(hrp, Root) <= 26 then
            if not BodyPos then
                BodyPos = Instance.new("BodyPosition")
                BodyPos.MaxForce = Vector3.new(Huge())
                BodyPos.Parent   = Root
                BodyPos.P        = 75000
                BodyPos.D        = 6000
                BodyPos.Position = hrp.Position + Vector3.new(0, 21, 0)
            end
            BodyPos.Position = hrp.Position + Vector3.new(0, 21, 0)

            if (Root.Position.Y <= hrp.Position.Y + 15) and TargetPLR.IsHeld.Value then
                for _, v in pairs(TargetPLR.Character:GetChildren()) do
                    if v:IsA("Part") then
                        v.CFrame = hrp.CFrame * CFrame.new(0, 21, 0)
                    end
                end
            end

            Root.AssemblyAngularVelocity, Root.AssemblyLinearVelocity = Vector3.zero, Vector3.zero
            Hum.PlatformStand = true

            -- ==== УДЕРЖАНИЕ ИЗ V2 (с RenderStepped:Wait) ====
            sno(Root)
            RunService.RenderStepped:Wait()
            sno(Root)
            unsno(Root)
            RunService.RenderStepped:Wait()
            sno(Root)
            RunService.RenderStepped:Wait()
            unsno(Root)

        else
            if not Head or not Hum or Hum.Health == 0 then
                TargetPLR.CharacterAdded:Wait()
                Head = FWD(TargetPLR.Character, "Head", 5)
                Hum  = FWD(TargetPLR.Character, "Humanoid", 5)
                BodyPos = Instance.new("BodyPosition")
                BodyPos.MaxForce = Vector3.new(Huge())
                BodyPos.Parent   = Root
                BodyPos.P        = 75000
                BodyPos.D        = 6000
                BodyPos.Position = hrp.Position + Vector3.new(0, 21, 0)
            end

            local oldCF = hrp.CFrame
            while (Head and Hum and Hum.Health ~= 0) and loopGrabV5 do
                RunService.PreSimulation:Wait()
                TargetPLR = getSelectedPlayer()
                if not TargetPLR then break end
                if TargetPLR.InPlot.Value then continue end
                Head = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Head")
                Hum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")
                Root = TargetPLR.Character and TargetPLR.Character:FindFirstChild("HumanoidRootPart")
                if not Head or not Hum then break end

                -- ==== ДОГОН ИЗ V4 (-11 под цель) ====
                char:PivotTo(Head.CFrame * CFrame.new(0, -11, 0))
                sno(Head)
                if Root then sno(Root) end

                if CheckForPartOwner(Head) then break end
            end
            hrp.CFrame = oldCF

            if Head and CheckForPartOwner(Head) then
                for _, v in pairs(TargetPLR.Character:GetChildren()) do
                    if v:IsA("BasePart") then
                        v.CFrame = hrp.CFrame * CFrame.new(0, 21, 0)
                    end
                end
            end
        end
    end

    if Root then
        for _, v in pairs(Root:GetChildren()) do
            if v.Name == "BodyPosition" then
                v:Destroy()
            end
        end
    end
end

LoopGrabV5Toggle = NoBlobGroup:AddToggle("LoopGrabV5", {
    Text    = "Loop Grab V5",
    Default = false,
    Callback = function(value)
        loopGrabV5 = value
        if value then
            if not getSelectedPlayer() then
                Library:Notify({Title = "Loop Grab V5", Description = "цели нету хд", Duration = 3})
                loopGrabV5 = false
                if LoopGrabV5Toggle then LoopGrabV5Toggle:Set(false) end
                return
            end
            loopGrabThreadV5 = task.spawn(RunLoopGrabV5)
        else
            if loopGrabThreadV5 then
                task.cancel(loopGrabThreadV5)
                loopGrabThreadV5 = nil
            end
            local t = getSelectedPlayer()
            local r = t and t.Character and t.Character:FindFirstChild("HumanoidRootPart")
            if r then
                for _, v in pairs(r:GetChildren()) do
                    if v.Name == "BodyPosition" then v:Destroy() end
                end
            end
        end
    end,
})

NoBlobGroup:AddToggle("PhysicsSync", {
    Text    = "Physics Sync (faster net)",
    Default = false,
    Callback = function(value)
        PS_Enabled = value
        if value then
            PS_Start()
            Library:Notify({
                Title = "Physics Sync",
                Description = "+",
                Time = 3,
            })
        else
            PS_Stop()
            Library:Notify({
                Title = "Physics Sync",
                Description = "-",
                Time = 3,
            })
        end
    end,
})

LocalPlayer.CharacterAdded:Connect(function()
    if PS_Enabled then
        task.wait(0.5)
        PS_Start()
    end
end)

-- ============================================================
-- ==== BlobGroup: LoopKill [BLOB] (Obsidian, debug) ====
-- ============================================================

local blobKillActive = false
local blobKillThread = nil
local BlobKillToggle = nil

local function getHRP_BK(char)
    return char and char:FindFirstChild("HumanoidRootPart")
end

local function ForceDeathNotG_BK(hum)
    hum.BreakJointsOnDeath = false
    hum:ChangeState(Enum.HumanoidStateType.Dead)
    hum.Sit  = false
    hum.Jump = true
end

-- ==== Заглушки для отсутствующих глобалов ====
local _FindBlob = FindBlob or function()
    local char = LocalPlayer.Character
    local hum  = char and char:FindFirstChild("Humanoid")
    if not hum or not hum.SeatPart then return nil end
    return hum.SeatPart:FindFirstAncestor("CreatureBlobman")
end

local _IsAboveLimit = _G.IsAboveLimit or function(plr)
    if plr and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
        return plr.Character.HumanoidRootPart.Position.Y > 10000
    end
    return true
end

local _isnetworkowner = isnetworkowner or function(part)
    return part and part:FindFirstChild("PartOwner") and part.PartOwner.Value == LocalPlayer.Name
end

local function RunBlobKill()
    local char = LocalPlayer.Character
    local hrp  = char and char:FindFirstChild("HumanoidRootPart")
    if not char or not hrp then
        warn("[BlobKill] нет char/hrp")
        return
    end

    local TargetPLR = getSelectedPlayer()
    if not TargetPLR then
        warn("[BlobKill] нет цели")
        return
    end

    print("[BlobKill] старт, цель:", TargetPLR.Name)

    local oldCF = char:GetPivot()
    local blob  = _FindBlob() or SpawnToy("CreatureBlobman")
    print("[BlobKill] blob:", blob)

    if not blob then
        warn("[BlobKill] не удалось спавнить/найти CreatureBlobman")
        return
    end

    local humSelf = char:FindFirstChild("Humanoid")
    if not humSelf then
        warn("[BlobKill] нет Humanoid")
        return
    end

    local seat = FWD(blob, "VehicleSeat")
    if not seat then
        warn("[BlobKill] нет VehicleSeat в блобе")
        return
    end

    seat:Sit(humSelf)

    local sitTimeout = tick() + 2
    while not humSelf.SeatPart and blobKillActive and tick() < sitTimeout do task.wait() end
    if not humSelf.SeatPart then
        warn("[BlobKill] не сел на блоба за 2 сек")
        return
    end

    local CreatureGrab    = FWD(FWD(blob, "BlobmanSeatAndOwnerScript"), "CreatureGrab")
    local CreatureRelease = FWD(FWD(blob, "BlobmanSeatAndOwnerScript"), "CreatureRelease")
    local RightDetector   = FWD(blob, "RightDetector")
    local RightWeld       = RightDetector and FWD(RightDetector, "RightWeld")

    print("[BlobKill] CreatureGrab:", CreatureGrab, "RightDetector:", RightDetector, "RightWeld:", RightWeld)

    while blobKillActive and RunService.Heartbeat:Wait() do
        oldCF = char:GetPivot()
        TargetPLR = getSelectedPlayer()
        if not TargetPLR then continue end

        local tRoot = getHRP_BK(TargetPLR.Character)
        local tHum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")
        if not tRoot or not tHum then continue end
        if _IsAboveLimit(TargetPLR) then continue end
        if tHum.Health == 0 then continue end

        while not RightWeld.Attachment0 and blobKillActive do
            task.wait(0.05)
            tRoot = getHRP_BK(TargetPLR.Character)
            tHum  = TargetPLR.Character and TargetPLR.Character:FindFirstChild("Humanoid")
            if not tRoot or not tHum then break end
            if _IsAboveLimit(TargetPLR) then char:PivotTo(oldCF) break end
            if tHum.Health == 0 then char:PivotTo(oldCF) break end

            if not humSelf.SeatPart then
                local invBlob = workspace:FindFirstChild(LocalPlayer.Name .. "SpawnedInToys")
                if invBlob and invBlob:FindFirstChild("CreatureBlobman") then
                    invBlob.CreatureBlobman.VehicleSeat:Sit(humSelf)
                end
            end

            char:PivotTo(tRoot.CFrame)
            hrp.AssemblyLinearVelocity  = Vector3.zero
            hrp.AssemblyAngularVelocity = Vector3.zero
            CreatureGrab:FireServer(RightDetector, tRoot, RightWeld)
        end

        CreatureRelease:FireServer(RightWeld, tRoot)
        char:PivotTo(tRoot.CFrame)

        for _ = 1, 10 do
            hrp.AssemblyLinearVelocity  = Vector3.zero
            hrp.AssemblyAngularVelocity = Vector3.zero
            CreatureGrab:FireServer(RightDetector, tRoot, RightWeld)
            CreatureRelease:FireServer(RightWeld, tRoot)
            if _isnetworkowner(tRoot) then
                ForceDeathNotG_BK(tHum)
            end
            task.wait()
        end

        char:PivotTo(oldCF)
        hrp.AssemblyLinearVelocity  = Vector3.zero
        hrp.AssemblyAngularVelocity = Vector3.zero
    end

    print("[BlobKill] остановлен")
end

BlobKillToggle = BlobGroup:AddToggle("LoopKillBlob", {
    Text    = "blob  kill",
    Default = false,
    Tooltip = "blob kill",
    Callback = function(value)
        blobKillActive = value
        if value then
            if not getSelectedPlayer() then
                Library:Notify({Title = "LoopKill [BLOB]", Description = "цели нету хд", Time = 3})
                blobKillActive = false
                if BlobKillToggle then BlobKillToggle:Set(false) end
                return
            end
            blobKillThread = task.spawn(function()
                local ok, err = pcall(RunBlobKill)
                if not ok then
                    warn("[LoopKill BLOB] ошибка: " .. tostring(err))
                    Library:Notify({Title = "LoopKill [BLOB]", Description = "Ошибка: " .. tostring(err), Time = 5})
                    blobKillActive = false
                    if BlobKillToggle then BlobKillToggle:Set(false) end
                end
            end)
        else
            if blobKillThread then
                task.cancel(blobKillThread)
                blobKillThread = nil
            end
        end
    end,
})

do
    local SettingsGroup = Tabs.Target:AddGroupbox({
        Side = "Right",
        Name = "Settings",
        IconName = "settings",
    })

    bmSpinRadius    = bmSpinRadius    or 25
    bmSpinSpeed     = bmSpinSpeed     or 0.25
    bmSpinKickHeight = bmSpinKickHeight or 20

    SettingsGroup:AddSlider("SpinKickRadius", {
        Text = "Spin Radius",
        Default = 25,
        Min = 5,
        Max = 50,
        Rounding = 0,
        Compact = false,
        Tooltip = "Rotation radius around target",
        Callback = function(v)
            bmSpinRadius = v
        end,
    })

    SettingsGroup:AddSlider("SpinKickSpeed", {
        Text = "Spin Speed",
        Default = 0.25,
        Min = 0.05,
        Max = 1,
        Rounding = 2,
        Compact = false,
        Tooltip = "Rotation speed (higher = faster)",
        Callback = function(v)
            bmSpinSpeed = v
        end,
    })

    SettingsGroup:AddSlider("SpinKickHeight", {
        Text = "Spin Height",
        Default = 20,
        Min = 5,
        Max = 100,
        Rounding = 0,
        Compact = false,
        Tooltip = "Height at which target rotates above you",
        Callback = function(v)
            bmSpinKickHeight = v
        end,
    })
end

local Players      = game:GetService("Players")
local RunService   = game:GetService("RunService")
local Workspace    = game:GetService("Workspace")
local RS           = game:GetService("ReplicatedStorage")
local LocalPlayer  = Players.LocalPlayer

Options = Library.Options
Toggles = Library.Toggles

SpawnToyRemote = RS:WaitForChild("MenuToys"):WaitForChild("SpawnToyRemoteFunction")

do
    local Blob2Group = Tabs.Target:AddGroupbox({
        Side = "Right",
        Name = "Blobman meth",
        IconName = "loop",
    })

    local bmSitBusy = false

    local function bmSitOnBlobman()
        if bmSitBusy then return false end
        bmSitBusy = true

        local char = LocalPlayer.Character
        local hum = char and char:FindFirstChildOfClass("Humanoid")
        local hrp = char and char:FindFirstChild("HumanoidRootPart")
        if not hum or not hrp or hum.Health <= 0 then
            bmSitBusy = false
            return false
        end

        if hum.Sit and hum.SeatPart and hum.SeatPart.Parent and hum.SeatPart.Parent.Name == "CreatureBlobman" then
            bmSitBusy = false
            return true
        end

        local folderName = LocalPlayer.Name .. "SpawnedInToys"
        local folder = Workspace:FindFirstChild(folderName)
        local blob = folder and folder:FindFirstChild("CreatureBlobman")

        if not blob then
            local canSpawn = LocalPlayer:FindFirstChild("CanSpawnToy")
            if canSpawn and not canSpawn.Value then
                local t = tick()
                while not canSpawn.Value and tick() - t < 2 do
                    task.wait(0.05)
                end
            end

            task.spawn(function()
                pcall(function()
                    SpawnToyRemote:InvokeServer(
                        "CreatureBlobman",
                        hrp.CFrame * CFrame.new(0, 5, 5),
                        Vector3.zero
                    )
                end)
            end)

            local t0 = tick()
            repeat
                task.wait(0.05)
                folder = Workspace:FindFirstChild(folderName)
                blob = folder and folder:FindFirstChild("CreatureBlobman")
            until blob or tick() - t0 > 3
        end

        if not blob then
            bmSitBusy = false
            return false
        end

        local seat = blob:FindFirstChild("VehicleSeat")
            or blob:FindFirstChildWhichIsA("VehicleSeat", true)
            or blob:WaitForChild("VehicleSeat", 1)
        if not seat then
            bmSitBusy = false
            return false
        end

        hrp.CFrame = seat.CFrame + Vector3.new(0, 2, 0)
        hrp.AssemblyLinearVelocity = Vector3.zero
        hrp.AssemblyAngularVelocity = Vector3.zero
        task.wait(0.02)
        pcall(function() seat:Sit(hum) end)

        local t0 = tick()
        while seat.Occupant ~= hum and tick() - t0 < 0.8 do
            task.wait(0.02)
        end

        bmSitBusy = false
        return seat.Occupant == hum
    end

    bmSpinAngle = 0
    bmKickingInProgress = false

    local function bmSpinKickTarget(targetName, keepGoing, reacquire, maxSeconds)
        local myChar = LocalPlayer.Character
        local myRoot = myChar and myChar:FindFirstChild("HumanoidRootPart")
        if not myRoot then return end

        local fnStart = tick()
        bmKickingInProgress = true

        local myHum = myChar and myChar:FindFirstChildOfClass("Humanoid")
        local seat = myHum and myHum.SeatPart
        if not (seat and seat.Parent and seat.Parent.Name == "CreatureBlobman") then
            if not bmSitOnBlobman() then
                Library:Notify({ Title = "Spin Kick", Description = "Blobman sit failed", Duration = 3 })
                bmKickingInProgress = false
                return
            end
            task.wait(0.3)
        end

        local GE = RS:FindFirstChild("GrabEvents")
        if not GE then
            Library:Notify({ Title = "Spin Kick", Description = "GrabEvents not found", Duration = 3 })
            bmKickingInProgress = false
            return
        end

        local savedPos = myRoot.CFrame
        local spinAngle = 0
        local dragging = false
        local grabStartTime = 0
        local spinRadius = bmSpinRadius or 25
        local spinSpeed = bmSpinSpeed or 0.25
        local customKickHeight = bmSpinKickHeight or 20

        myChar = LocalPlayer.Character
        myRoot = myChar and myChar:FindFirstChild("HumanoidRootPart")

        while keepGoing() do
            if maxSeconds and (tick() - fnStart) > maxSeconds then break end

            local target = Players:FindFirstChild(targetName)
            if not target or not target.Parent or not target.Character then
                if not reacquire then break end
                dragging = false
                grabStartTime = 0
                RunService.Heartbeat:Wait()
            else
                local tChar = target.Character
                local tRoot = tChar:FindFirstChild("HumanoidRootPart")
                local tHum = tChar:FindFirstChild("Humanoid")

                seat = myChar and myChar.Humanoid and myChar.Humanoid.SeatPart

                if tRoot and tHum and tHum.Health > 0 then
                    tRoot.AssemblyLinearVelocity = Vector3.zero
                    tRoot.Velocity = Vector3.zero

                    if seat then
                        local blobman = seat.Parent
                        local remoteFolder = blobman:FindFirstChild("BlobmanSeatAndOwnerScript")
                        local grab = remoteFolder and remoteFolder:FindFirstChild("CreatureGrab")
                        local drop = remoteFolder and remoteFolder:FindFirstChild("CreatureDrop")

                        local L_Det = blobman:FindFirstChild("LeftDetector")
                        local R_Det = blobman:FindFirstChild("RightDetector")
                        local L_Weld = L_Det and (L_Det:FindFirstChild("LeftWeld") or L_Det:FindFirstChild("RigidConstraint"))
                        local R_Weld = R_Det and (R_Det:FindFirstChild("RightWeld") or R_Det:FindFirstChild("RigidConstraint"))

                        if grab and drop and L_Weld and R_Weld then
                            pcall(function()
                                grab:FireServer(L_Det, tRoot, L_Weld)
                                grab:FireServer(R_Det, tRoot, R_Weld)
                                drop:FireServer(L_Weld, tRoot)
                                drop:FireServer(R_Weld, tRoot)
                            end)
                        end
                    end

                    if not dragging then
                        spinAngle = spinAngle + spinSpeed
                        if spinAngle > 6.28 then spinAngle = 0 end

                        local x = math.cos(spinAngle) * spinRadius
                        local z = math.sin(spinAngle) * spinRadius

                        myRoot.CFrame = tRoot.CFrame * CFrame.new(x, 0, z)

                        if GE then
                            pcall(function()
                                tHum.PlatformStand = true
                                if GE.SetNetworkOwner then GE.SetNetworkOwner:FireServer(tRoot, myRoot.CFrame) end
                                if GE.CreateGrabLine then GE.CreateGrabLine:FireServer(tRoot, Vector3.zero, tRoot.Position, false) end
                            end)
                        end

                        if grabStartTime == 0 then grabStartTime = tick() end
                        if tick() - grabStartTime > 0.3 then
                            dragging = true
                            grabStartTime = 0
                        end
                    else
                        spinAngle = spinAngle + spinSpeed
                        if spinAngle > 6.28 then spinAngle = 0 end

                        local x = math.cos(spinAngle) * spinRadius
                        local z = math.sin(spinAngle) * spinRadius

                        myRoot.CFrame = tRoot.CFrame * CFrame.new(x, 0, z)

                        local lockPos = savedPos * CFrame.new(0, customKickHeight, 0)
                        tRoot.CFrame = lockPos

                        if GE then
                            pcall(function()
                                tHum.PlatformStand = true
                                if GE.SetNetworkOwner then GE.SetNetworkOwner:FireServer(tRoot, lockPos) end
                                if GE.DestroyGrabLine then GE.DestroyGrabLine:FireServer(tRoot) end
                                if GE.CreateGrabLine then GE.CreateGrabLine:FireServer(tRoot, Vector3.zero, tRoot.Position, false) end
                            end)
                        end
                    end
                else
                    dragging = false
                    grabStartTime = 0
                end
            end

            RunService.Heartbeat:Wait()
        end

        if myRoot and savedPos then
            myRoot.CFrame = savedPos
        end
        bmKickingInProgress = false
    end

    local function bmLoopKickOnce(targetPlayer, duration)
        duration = duration or 6
        local myChar = LocalPlayer.Character
        local myRoot = myChar and myChar:FindFirstChild("HumanoidRootPart")
        if not myRoot then return end

        local myHum = myChar:FindFirstChildOfClass("Humanoid")
        local seat = myHum and myHum.SeatPart
        if not (seat and seat.Parent and seat.Parent.Name == "CreatureBlobman") then
            if not bmSitOnBlobman() then
                Library:Notify({ Title = "Loop Kick", Description = "Blobman sit failed", Duration = 3 })
                return
            end
            task.wait(0.3)
        end

        local GE = RS:FindFirstChild("GrabEvents")
        local kickHeight = 25
        local savedPos = myRoot.CFrame
        local dragging = false
        local grabStartTime = 0
        local startT = tick()

        while tick() - startT < duration do
            local target = targetPlayer
            if not target or not target.Parent or not target.Character then
                dragging = false
                grabStartTime = 0
                RunService.Heartbeat:Wait()
            else
                local tRoot = target.Character:FindFirstChild("HumanoidRootPart")
                local tHum = target.Character:FindFirstChild("Humanoid")

                myChar = LocalPlayer.Character
                myRoot = myChar and myChar:FindFirstChild("HumanoidRootPart")
                seat = myChar and myChar.Humanoid and myChar.Humanoid.SeatPart

                if tRoot and tHum and tHum.Health > 0 and myRoot then
                    tRoot.AssemblyLinearVelocity = Vector3.zero
                    tRoot.Velocity = Vector3.zero

                    if seat then
                        local blobman = seat.Parent
                        local remoteFolder = blobman:FindFirstChild("BlobmanSeatAndOwnerScript")
                        local grab = remoteFolder and remoteFolder:FindFirstChild("CreatureGrab")
                        local drop = remoteFolder and remoteFolder:FindFirstChild("CreatureDrop")
                        local L_Det = blobman:FindFirstChild("LeftDetector")
                        local R_Det = blobman:FindFirstChild("RightDetector")
                        local L_Weld = L_Det and (L_Det:FindFirstChild("LeftWeld") or L_Det:FindFirstChild("RigidConstraint"))
                        local R_Weld = R_Det and (R_Det:FindFirstChild("RightWeld") or R_Det:FindFirstChild("RigidConstraint"))

                        if grab and drop and L_Weld and R_Weld then
                            pcall(function()
                                grab:FireServer(L_Det, tRoot, L_Weld)
                                grab:FireServer(R_Det, tRoot, R_Weld)
                                drop:FireServer(L_Weld, tRoot)
                                drop:FireServer(R_Weld, tRoot)
                            end)
                        end
                    end

                    if not dragging then
                        myRoot.CFrame = tRoot.CFrame
                        if GE then
                            pcall(function()
                                tHum.PlatformStand = true
                                if GE.SetNetworkOwner then GE.SetNetworkOwner:FireServer(tRoot, myRoot.CFrame) end
                                if GE.CreateGrabLine then GE.CreateGrabLine:FireServer(tRoot, Vector3.zero, tRoot.Position, false) end
                            end)
                        end
                        if grabStartTime == 0 then grabStartTime = tick() end
                        if tick() - grabStartTime > 0.3 then
                            dragging = true
                            grabStartTime = 0
                        end
                    else
                        local lockPos = savedPos * CFrame.new(0, kickHeight, 0)
                        myRoot.CFrame = savedPos
                        tRoot.CFrame = lockPos
                        if GE then
                            pcall(function()
                                tHum.PlatformStand = true
                                if GE.SetNetworkOwner then GE.SetNetworkOwner:FireServer(tRoot, lockPos) end
                                if GE.DestroyGrabLine then GE.DestroyGrabLine:FireServer(tRoot) end
                                if GE.CreateGrabLine then GE.CreateGrabLine:FireServer(tRoot, Vector3.zero, tRoot.Position, false) end
                            end)
                        end
                    end
                else
                    dragging = false
                    grabStartTime = 0
                end
            end

            RunService.Heartbeat:Wait()
        end

        if myRoot and savedPos then
            myRoot.CFrame = savedPos
        end
    end

    local function bmApplyMethodOnce(targetPlayer)
        if not targetPlayer or not targetPlayer.Parent or not targetPlayer.Character then
            Library:Notify({ Title = "Blobman", Description = "No target", Duration = 2 })
            return
        end

        local selected = Options.BlobmanSelectedMethod and Options.BlobmanSelectedMethod.Value or {}
        local methods = {}
        for k, v in pairs(selected) do
            if v == true then table.insert(methods, k) end
        end
        if #methods == 0 then
            Library:Notify({ Title = "Blobman", Description = "No method selected", Duration = 2 })
            return
        end

        for _, m in ipairs(methods) do
            task.spawn(function()
                if m == "Loop Kick" then
                    bmLoopKickOnce(targetPlayer, 6)
                elseif m == "Spin Kick" then
                    bmSpinKickTarget(targetPlayer.Name, function() return true end, false, 6)
                end
            end)
        end
    end

    local AutoSitToggle = Blob2Group:AddToggle("AutoSitBlobman", {
        Text = "Auto Sit Blob",
        Default = false,
        Callback = function(Value)
            if Value then
                if not bmSitOnBlobman() then
                    Library:Notify({ Title = "Auto Sit Blob", Description = "Failed to sit", Duration = 2 })
                end
            end
        end,
    })

    AutoSitToggle:AddKeyPicker("AutoSitBlobmanKey", {
        Text = "Auto Sit Keybind",
        Default = "Z",
        Mode = "Toggle",
        SyncToggleState = true,
        NoUI = false,
    })

    Blob2Group:AddDropdown("BlobmanSelectedMethod", {
        Text = "Selected Method",
        Values = { "Loop Kick", "Spin Kick" },
        Default = { "Loop Kick" },
        Multi = true,
    })

    Blob2Group:AddButton({
        Text = "Apply Method Once",
        Func = function()
            local target = getSelectedPlayer()
            if not target then
                Library:Notify({ Title = "Blobman", Description = "Select a target first", Duration = 2 })
                return
            end
            bmApplyMethodOnce(target)
        end,
    })

    local loopAppleActive = false

    Blob2Group:AddToggle("LoopAppleMethod", {
        Text = "Loop Apple Method",
        Default = false,
        Callback = function(Value)
            loopAppleActive = Value
            if not Value then return end

            task.spawn(function()
                while loopAppleActive do
                    local target = getSelectedPlayer()
                    if target and target.Parent and target.Character then
                        bmApplyMethodOnce(target)
                    end
                    task.wait(6.5)
                end
            end)
        end,
    })
end

-- ============================================================
-- Grab Stick v4 — режимы Noclip/Kick + Stick/Unstick
--                       через ToolPencil, логика XOCU
-- ============================================================
local GrabStickGroup = Tabs.Target:AddLeftGroupbox("Grab Stick")

local STICK_ITEM   = "ToolPencil"     -- всегда карандаш
local GrabStickMode = "Noclip"        -- "Noclip" | "Kick"

local currentStickShuriken = nil
local currentStickHighlight = nil
local stickSessionId = 0
local stickLoopActive = false

-- ремоуты
local XOCU_SpawnToyRemote  = ReplicatedStorage:WaitForChild("MenuToys"):WaitForChild("SpawnToyRemoteFunction")
local XOCU_DestroyToy      = ReplicatedStorage:WaitForChild("MenuToys"):WaitForChild("DestroyToy")
local XOCU_SetNetworkOwner = ReplicatedStorage:WaitForChild("GrabEvents"):WaitForChild("SetNetworkOwner")
local XOCU_DestroyGrabLine = ReplicatedStorage:WaitForChild("GrabEvents"):WaitForChild("DestroyGrabLine")
local XOCU_StickyPartEvent = ReplicatedStorage:WaitForChild("PlayerEvents"):WaitForChild("StickyPartEvent")

-- ============================================================
-- Папка (plot или SpawnedInToys) — 1-в-1 из XOCU
-- ============================================================
local function XOCU_GetFolder()
    local inPlot = LocalPlayer:FindFirstChild("InPlot")
    if inPlot and inPlot.Value then
        local plots = workspace:FindFirstChild("Plots")
        if plots then
            for i = 1, 5 do
                local p = plots:FindFirstChild("Plot"..i)
                if p and p:FindFirstChild("PlotSign") then
                    local sign = p.PlotSign
                    for _, name in ipairs({"ThisPlotsOwners","ThisPlotsOwner","ThisPlotOwners"}) do
                        local c = sign:FindFirstChild(name)
                        if c then
                            local owner = c:IsA("StringValue") and c or c:FindFirstChildOfClass("StringValue")
                            if owner and owner.Value == LocalPlayer.Name then
                                return workspace.PlotItems:FindFirstChild("Plot"..i)
                            end
                        end
                    end
                end
            end
        end
    end
    return workspace:FindFirstChild(LocalPlayer.Name .. "SpawnedInToys")
end

-- ============================================================
-- Скрыть pencil
-- ============================================================
local function XOCU_HideShuriken(shuriken)
    pcall(function()
        for _, v in ipairs(shuriken:GetDescendants()) do
            if v:IsA("BasePart") then
                v.CanTouch  = false
                v.CanCollide = false
                v.CanQuery  = false
                v.Transparency = 1
            end
        end
    end)
end

-- ============================================================
-- Ждать новый pencil
-- ============================================================
local function XOCU_WaitForNewShuriken(timeout, activeCheck, existing)
    timeout = timeout or 5
    local folder = XOCU_GetFolder()
    if not folder then return nil end

    local result = nil
    local conn = folder.ChildAdded:Connect(function(child)
        if child.Name == STICK_ITEM and not result and not (existing and existing[child]) then
            result = child
        end
    end)

    local start = tick()
    while not result and (tick() - start < timeout) do
        if activeCheck and not activeCheck() then
            conn:Disconnect()
            return nil
        end
        task.wait()
    end
    conn:Disconnect()
    return result
end

-- ============================================================
-- Спавн pencil (CFrame/Vector3 — оригинал XOCU, не менять)
-- ============================================================
local function XOCU_SpawnShuriken()
    local hrp = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
    if not hrp then return end
    task.spawn(function()
        local cf = hrp.CFrame * CFrame.Angles(-0.605224, -0.321753, 0)
        pcall(function()
            XOCU_SpawnToyRemote:InvokeServer(STICK_ITEM, cf, Vector3.new(0, 25.02, 0))
        end)
    end)
end

-- ============================================================
-- Создать + забрать ownership
-- ============================================================
local function XOCU_CreateAndOwnShuriken(activeCheck)
    local folder = XOCU_GetFolder()
    local existing = {}
    if folder then
        for _, v in ipairs(folder:GetChildren()) do
            if v.Name == STICK_ITEM then existing[v] = true end
        end
    end

    while activeCheck == nil or activeCheck() do
        XOCU_SpawnShuriken()
        local shuriken = XOCU_WaitForNewShuriken(4, activeCheck, existing)
        if not shuriken then
            if activeCheck and not activeCheck() then return nil end
            task.wait(0.25)
            continue
        end

        task.wait(0.08)
        XOCU_HideShuriken(shuriken)

        local soundPart = shuriken:FindFirstChild("SoundPart") or shuriken:FindFirstChildOfClass("BasePart")
        if not soundPart then
            pcall(function() XOCU_DestroyToy:FireServer(shuriken) end)
            task.wait(0.2)
            continue
        end

        pcall(function()
            XOCU_SetNetworkOwner:FireServer(soundPart, soundPart.CFrame)
        end)
        task.wait(0.12)

        if activeCheck and not activeCheck() then
            pcall(function() XOCU_DestroyToy:FireServer(shuriken) end)
            return nil
        end

        local owner = soundPart:FindFirstChild("PartOwner")
        if owner and owner.Value == LocalPlayer.Name then
            return shuriken
        else
            pcall(function() XOCU_DestroyToy:FireServer(shuriken) end)
            task.wait(0.25)
        end
    end
    return nil
end

-- ============================================================
-- Стик pencil к цели (NaN CFrame — оригинал XOCU)
-- ============================================================
local function XOCU_StickShurikenToTarget(shuriken, target, cf)
    local stickyPart = shuriken:FindFirstChild("StickyPart") or shuriken:FindFirstChildOfClass("BasePart")
    if not stickyPart or not target then return end
    pcall(function()
        XOCU_DestroyGrabLine:FireServer(shuriken:FindFirstChildOfClass("BasePart"))
    end)
    pcall(function()
        XOCU_StickyPartEvent:FireServer(stickyPart, target, cf or CFrame.new(0/0, 0/0, 0/0))
    end)
end

-- ============================================================
-- Получить схваченную часть (1-в-1 из XOCU)
-- ============================================================
local function XOCU_GetGrabbedPart()
    local g = workspace:FindFirstChild("GrabParts")
    if not g then return nil end
    local gp = g:FindFirstChild("GrabPart")
    if not gp then return nil end
    local weld = gp:FindFirstChild("WeldConstraint") or gp:FindFirstChild("Weld")
    if not weld then return nil end
    return weld.Part1 or nil
end

-- ============================================================
-- Обводка бело-серая
-- ============================================================
local function XOCU_ClearHighlight()
    if currentStickHighlight then
        pcall(function() currentStickHighlight:Destroy() end)
        currentStickHighlight = nil
    end
end

local function XOCU_MakeHighlight(target)
    XOCU_ClearHighlight()
    if not target then return end
    local hl = Instance.new("SelectionBox")
    hl.Adornee = target
    hl.Color3          = Color3.fromRGB(255, 255, 255)   -- белый контур
    hl.SurfaceColor3   = Color3.fromRGB(200, 200, 200)   -- серый фон
    hl.LineThickness   = 0.05
    hl.SurfaceTransparency = 0.7
    hl.Transparency    = 0.2
    hl.Parent = target
    currentStickHighlight = hl
end

-- ============================================================
-- KICK MODE: PlatformStand + BodyPosition
-- ============================================================
local function XOCU_ApplyKickMode(target)
    if not target then return end
    local model = target:FindFirstAncestorOfClass("Model")
    if not model then return end
    local hum  = model:FindFirstChildOfClass("Humanoid")
    local root = model:FindFirstChild("HumanoidRootPart")

    if hum then
        pcall(function()
            hum.PlatformStand = true
            hum.Sit = false
            hum:ChangeState(Enum.HumanoidStateType.Physics)
        end)
    end
    if root then
        task.spawn(function()
            local bp = root:FindFirstChild("NLheStickBP")
            if not bp then
                bp = Instance.new("BodyPosition")
                bp.Name = "NLheStickBP"
                bp.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                bp.P = 75000
                bp.D = 12000
                bp.Position = root.Position
                bp.Parent = root
            end
            while stickLoopActive and bp.Parent do
                task.wait(0.05)
            end
            pcall(function() bp:Destroy() end)
        end)
    end
end

local function XOCU_RemoveKickMode(target)
    if not target then return end
    local model = target:FindFirstAncestorOfClass("Model")
    if not model then return end
    local hum  = model:FindFirstChildOfClass("Humanoid")
    local root = model:FindFirstChild("HumanoidRootPart")
    if hum then
        pcall(function()
            hum.PlatformStand = false
            hum:ChangeState(Enum.HumanoidStateType.GettingUp)
        end)
    end
    if root then
        local bp = root:FindFirstChild("NLheStickBP")
        if bp then pcall(function() bp:Destroy() end) end
    end
end

-- ============================================================
-- Stick: ждёт граба → стикает pencil
-- ============================================================
local function GrabStickOnce()
    Library:Notify({ Title = "Grab Stick", Description = "Возьми что-нибудь сейчас...", Time = 4 })

    -- 1) ждём граба (до 15 сек)
    local grabbed = nil
    local start = tick()
    while tick() - start < 15 do
        grabbed = XOCU_GetGrabbedPart()
        if grabbed then break end
        task.wait(0.05)
    end

    if not grabbed then
        Library:Notify({ Title = "Grab Stick", Description = "Не взял ничего за 15 сек", Time = 3 })
        return
    end

    -- 2) обводка
    XOCU_MakeHighlight(grabbed)

    -- 3) создать pencil + ownership
    stickSessionId = stickSessionId + 1
    local mySession = stickSessionId
    stickLoopActive = true

    local shuriken = XOCU_CreateAndOwnShuriken(function()
        return stickLoopActive and stickSessionId == mySession
    end)
    if not shuriken then
        XOCU_ClearHighlight()
        stickLoopActive = false
        Library:Notify({ Title = "Grab Stick", Description = "Не удалось создать pencil", Time = 3 })
        return
    end

    currentStickShuriken = shuriken

    -- 4) стикаем с NaN CFrame (оригинал XOCU)
    XOCU_StickShurikenToTarget(shuriken, grabbed, CFrame.new(0/0, 0/0, 0/0))
    XOCU_HideShuriken(shuriken)

    -- 5) Kick-режим — применить PlatformStand
    if GrabStickMode == "Kick" then
        XOCU_ApplyKickMode(grabbed)
    end

    Library:Notify({
        Title = "Grab Stick",
        Description = "Stuck to: " .. grabbed.Name .. " [" .. GrabStickMode .. "]",
        Time = 3,
    })
end

-- ============================================================
-- Unstick
-- ============================================================
local function GrabStickUnstick()
    stickLoopActive = false
    stickSessionId = stickSessionId + 1

    if currentStickHighlight and currentStickHighlight.Adornee then
        XOCU_RemoveKickMode(currentStickHighlight.Adornee)
    end

    if currentStickShuriken and currentStickShuriken.Parent then
        pcall(function() XOCU_DestroyToy:FireServer(currentStickShuriken) end)
        pcall(function() currentStickShuriken:Destroy() end)
    end
    currentStickShuriken = nil

    XOCU_ClearHighlight()
    Library:Notify({ Title = "Grab Stick", Description = "Unstuck", Time = 2 })
end

-- ============================================================
-- UI
-- ============================================================
GrabStickGroup:AddDropdown("GrabStickModeDropdown", {
    Text    = "Mode",
    Values  = { "Noclip", "Kick" },
    Default = "Noclip",
    Multi   = false,
    Tooltip = "Noclip — обычный стик карандашом (как в XOCU).\nKick — PlatformStand + фиксация цели.",
    Callback = function(v)
        GrabStickMode = tostring(v or "Noclip")
    end,
})

GrabStickGroup:AddButton({
    Text = "Stick",
    Tooltip = "Нажми — затем возьми что-нибудь. Карандаш прицепится.",
    Func = function()
        task.spawn(GrabStickOnce)
    end,
})

GrabStickGroup:AddButton({
    Text = "Unstick",
    Tooltip = "Убирает карандаш + обводку + Kick-режим.",
    Func = function()
        task.spawn(GrabStickUnstick)
    end,
})

-- сброс при респавне
LocalPlayer.CharacterAdded:Connect(function()
    stickLoopActive = false
    stickSessionId = stickSessionId + 1
    XOCU_ClearHighlight()
    currentStickShuriken = nil
end)

        r32 = Tabs.Target:AddLeftGroupbox("idk")

-- Хранилище настроек
_G._PacketLagEnabled = false
_G._PacketLagThread  = nil
_G._PacketLagSizeMB  = 0.1
_G._PacketLagChunk   = "metaballs metaballs metaballs metaballs metaballs metaballs metaballs metaballs"

-- === 1. Input: сообщение ===
r32:AddInput("PacketLagMessage", {
    Text = "Packet Message",
    Default = "💖💖💖sex💖💖💖sex💖💖💖sex💖💖💖sex💖💖💖sex💖💖💖sex💖💖💖sex💖💖💖sex💖💖💖sex💖💖💖sex",
    Placeholder = "текст для спама",
    Numeric = false,
    Finished = true,
    Callback = function(v)
        local s = tostring(v or "")
        if s ~= "" then
            _G._PacketLagChunk = s
        end
    end,
})

-- === 2. Slider: размер в МБ ===
r32:AddSlider("PacketLagSize", {
    Text = "Packet Size (MB)",
    Min = 0.01, Max = 9.8, Default = 2.0, Rounding = 2,
    Callback = function(v) _G._PacketLagSizeMB = v end,
})

-- === 3. Toggle: отправка ===
r32:AddToggle("PacketLagToggle", {
    Text = "Packet Lag Server",
    Default = false,
    Callback = function(v)
        _G._PacketLagEnabled = v and true or false

        if _G._PacketLagThread then
            task.cancel(_G._PacketLagThread)
            _G._PacketLagThread = nil
        end

        if v then
            local RS = game:GetService("ReplicatedStorage")
            local ExtendGrabLine = RS:WaitForChild("GrabEvents"):WaitForChild("ExtendGrabLine")

            _G._PacketLagThread = task.spawn(function()
                while _G._PacketLagEnabled do
                    task.wait(0.1)

                    local chunk = _G._PacketLagChunk or ""
                    local chunkLen = #chunk
                    if chunkLen <= 0 then
                        chunk = "A"
                        chunkLen = 1
                    end

                    local targetBytes = (_G._PacketLagSizeMB or 0.1) * 1024 * 1024
                    local repeats = math.max(1, math.floor(targetBytes / chunkLen))

                    pcall(function()
                        ExtendGrabLine:FireServer(string.rep(chunk, repeats))
                    end)
                end
            end)
        end
    end,
})

-- ============================================================
-- ANTI GRAB (порт из Wourld Hub, самодостаточный)
-- ============================================================
do
    local AG_Players    = game:GetService("Players")
    local AG_RS         = game:GetService("ReplicatedStorage")
    local AG_RunService = game:GetService("RunService")
    local AG_Local      = AG_Players.LocalPlayer

    local AG = {
        active   = false,
        conn     = nil,
        struggle = {},
        busy     = false,
    }

    local function isHeadOwnedByOther(head)
        local po = head and head:FindFirstChild("PartOwner")
        if not po then return false end
        local v = tostring(po.Value or "")
        return v ~= "" and v ~= AG_Local.Name
    end

    local function setLimbs(char, on)
        if not char then return end
        for _, p in ipairs(char:GetChildren()) do
            if p:IsA("BasePart")
                and p.Name ~= "Head"
                and p.Name ~= "HumanoidRootPart"
                and p:FindFirstChild("BallSocketConstraint")
            then
                p.BallSocketConstraint.Enabled = not on
                local rlp = p:FindFirstChild("RagdollLimbPart")
                local wc  = rlp and rlp:FindFirstChild("WeldConstraint")
                if wc then wc.Enabled = not on end
            end
        end
    end

    local function releaseAnchors(char)
        if not char then return end
        for _, p in ipairs(char:GetChildren()) do
            if p:IsA("BasePart") and p.Anchored then
                p.Anchored = false
            end
        end
    end

    local function recover(char)
        if AG.busy then return end
        AG.busy = true

        task.spawn(function()
            local ev       = AG_RS:FindFirstChild("CharacterEvents")
            local struggle = ev and ev:FindFirstChild("Struggle")
            local ragdoll  = ev and ev:FindFirstChild("RagdollRemote")
            local isHeld   = AG_Local:FindFirstChild("IsHeld")
            local t0       = tick()

            while AG.active do
                local c    = (char and char.Parent and char) or AG_Local.Character
                local hum  = c and c:FindFirstChildOfClass("Humanoid")
                local hrp  = c and c:FindFirstChild("HumanoidRootPart")
                local head = c and c:FindFirstChild("Head")

                if not c or not hum or not hrp or hum.Health <= 0 then break end

                local held  = isHeld and isHeld.Value
                local owned = isHeadOwnedByOther(head)

                if not held and not owned and tick() - t0 > 0.22 then break end

                setLimbs(c, true)

                hum.PlatformStand = false
                hum.Sit           = false
                hum.AutoRotate    = true
                hum.Jump          = true

                if struggle then pcall(function() struggle:FireServer(AG_Local) end) end
                if ragdoll  then pcall(function() ragdoll:FireServer(hrp, 0) end) end

                local v = hrp.AssemblyLinearVelocity
                hrp.AssemblyLinearVelocity = Vector3.new(0, math.max(v.Y, 16), 0)

                if hum.MoveDirection.Magnitude > 0.05 then
                    hrp.CFrame = hrp.CFrame + hum.MoveDirection.Unit * 0.32
                end

                if tick() - t0 > 2.8 then break end
                task.wait(0.03)
            end

            AG.busy = false
        end)
    end

    local function bind(char)
        if AG.conn then
            AG.conn:Disconnect()
            AG.conn = nil
        end
        for _, c in pairs(AG.struggle) do
            if c and c.Disconnect then c:Disconnect() end
        end
        AG.struggle = {}

        if not char then return end

        local head = char:WaitForChild("Head", 2)
        local hum  = char:WaitForChild("Humanoid", 2)
        local hrp  = char:WaitForChild("HumanoidRootPart", 2)
        if not head or not hum or not hrp then return end

        setLimbs(char, true)

        table.insert(AG.struggle, head.ChildAdded:Connect(function(c)
            if AG.active and c and c.Name == "PartOwner" then
                recover(char)
            end
        end))

        local rag = hum:FindFirstChild("Ragdolled")
        if rag then
            table.insert(AG.struggle, rag.Changed:Connect(function()
                if AG.active then recover(char) end
            end))
        end

        local isHeld = AG_Local:FindFirstChild("IsHeld")
        if isHeld then
            table.insert(AG.struggle, isHeld.Changed:Connect(function(v)
                if AG.active and v then recover(char) end
            end))
        end

        if isHeadOwnedByOther(head) or (isHeld and isHeld.Value) then
            recover(char)
        end
    end

    local function setState(on)
        AG.active = on and true or false

        for _, c in pairs(AG.struggle) do
            if c and c.Disconnect then c:Disconnect() end
        end
        AG.struggle = {}

        if AG.conn then
            AG.conn:Disconnect()
            AG.conn = nil
        end

        if on then
            bind(AG_Local.Character)
            AG.conn = AG_Local.CharacterAdded:Connect(function(c)
                task.wait(0.15)
                bind(c)
            end)
        else
            local c = AG_Local.Character
            if c then
                setLimbs(c, false)
                releaseAnchors(c)
            end
        end
    end

    -- ===== UI =====
    if not DefGroup then
        DefGroup = Tabs.Defense:AddLeftGroupbox("Anti Grab")
    end

    DefGroup:AddToggle("AntiGrab", {
        Text = "Anti Grab",
        Default = false,
        Callback = function(v) setState(v) end,
    })
end

-- ============================================================
-- BREAD ANTI KICK (порт из Wourld Hub, кнопка, держится)
-- ============================================================
do
    local BAK_Players = game:GetService("Players")
    local BAK_RS      = game:GetService("ReplicatedStorage")
    local BAK_Local   = BAK_Players.LocalPlayer

    -- один активный bread на клиенте
    BAK_Active = nil
    BAK_Task   = nil
    BAK_Stop   = false

    local function getContainer()
        return workspace:FindFirstChild(BAK_Local.Name .. "SpawnedInToys")
    end

    local function getMenuRemotes()
        local m = BAK_RS:FindFirstChild("MenuToys")
        if not m then return nil, nil end
        return m:FindFirstChild("SpawnToyRemoteFunction"),
               m:FindFirstChild("DestroyToy")
    end

    -- убрать старый bread + очистить состояние
    local function clearOld()
        BAK_Stop = true
        if BAK_Task then
            task.cancel(BAK_Task)
            BAK_Task = nil
        end
        local destroy = select(2, getMenuRemotes())
        local c = getContainer()
        if c then
            for _, t in ipairs(c:GetChildren()) do
                if t.Name == "FoodBread" then
                    if destroy then pcall(function() destroy:FireServer(t) end) end
                    pcall(function() t:Destroy() end)
                end
            end
        end
        BAK_Active = nil
    end

    -- быстрый спавн: ждём сразу в контейнере без 2.6s
    local function spawnBread(cf)
        local spawnRF = getMenuRemotes()
        if not spawnRF then return nil end
        local c = getContainer()
        if not c then return nil end

        local before = {}
        for _, t in ipairs(c:GetChildren()) do
            before[t] = true
        end

        pcall(function()
            spawnRF:InvokeServer("FoodBread", cf or CFrame.new(0, 10, 16), Vector3.zero)
        end)

        -- очень быстрый poll — 1.2s max, шаг 0.02
        local t0 = tick() + 1.2
        repeat
            c = getContainer()
            if c then
                for _, t in ipairs(c:GetChildren()) do
                    if not before[t] and t.Name == "FoodBread" then
                        return t
                    end
                end
            end
            task.wait(0.02)
        until tick() > t0
        return nil
    end

    -- ownership: быстро, до 0.4s, шаг 0.02
    local function claimOwnership(part)
        local ge = BAK_RS:FindFirstChild("GrabEvents")
        local setOwner = ge and ge:FindFirstChild("SetNetworkOwner")
        if not setOwner then return false end
        local t0 = tick() + 0.4
        repeat
            pcall(function() setOwner:FireServer(part, part.CFrame) end)
            local po = part:FindFirstChild("PartOwner")
            if po and po.Value == BAK_Local.Name then return true end
            task.wait(0.02)
        until tick() > t0
        local po = part:FindFirstChild("PartOwner")
        return po and po.Value == BAK_Local.Name
    end

    local function setNoCollide(model)
        if not model then return end
        for _, p in ipairs(model:GetDescendants()) do
            if p:IsA("BasePart") then
                p.CanCollide = false
                p.CanTouch = false
                p.CanQuery = false
            end
        end
    end

    -- жёстко держим bread на FirePlayerPart через BodyMovers
    local function attachBodyMovers(part)
        if not part then return end
        -- BodyPosition
        local bp = part:FindFirstChild("BAK_BP") or Instance.new("BodyPosition")
        bp.Name = "BAK_BP"
        bp.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
        bp.P = 2e5
        bp.D = 250
        bp.Position = part.Position
        bp.Parent = part

        -- BodyGyro
        local bg = part:FindFirstChild("BAK_BG") or Instance.new("BodyGyro")
        bg.Name = "BAK_BG"
        bg.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
        bg.P = 2e5
        bg.D = 250
        bg.CFrame = part.CFrame
        bg.Parent = part
    end

    local function runBread()
        clearOld()
        BAK_Stop = false

        local char = BAK_Local.Character
        if not char then return false end
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if not hrp then return false end

        -- спавним ПРЯМО у ног, чтобы быстрее долетело
        local bread = spawnBread(hrp.CFrame * CFrame.new(0, 2, 0))
        if not bread then return false end
        BAK_Active = bread

        local sp = bread:FindFirstChild("SoundPart")
            or bread:FindFirstChildWhichIsA("BasePart", true)
        if not sp then clearOld() return false end

        -- сразу забрать ownership
        claimOwnership(sp)

        setNoCollide(bread)
        attachBodyMovers(sp)

        -- периодически забираем ownership и держим bread при персонаже
        BAK_Task = task.spawn(function()
            local lastClaim = 0
            while not BAK_Stop and bread.Parent and sp.Parent do
                local c = BAK_Local.Character
                local h = c and c:FindFirstChild("HumanoidRootPart")
                local fp = h and (h:FindFirstChild("FirePlayerPart") or h)
                if fp then
                    local target = fp.CFrame * CFrame.Angles(math.rad(90), 0, 0)
                    -- bp.Position держит позицию, bg.CFrame держит ориентацию
                    local bp = sp:FindFirstChild("BAK_BP")
                    local bg = sp:FindFirstChild("BAK_BG")
                    if bp then bp.Position = target.Position end
                    if bg then bg.CFrame = target end
                    -- обнуляем скорость, чтобы не улетал
                    sp.AssemblyLinearVelocity = Vector3.zero
                    sp.AssemblyAngularVelocity = Vector3.zero
                end

                -- перезахват ownership каждые 0.3s, если потеряли
                local now = tick()
                if now - lastClaim > 0.3 then
                    lastClaim = now
                    local po = sp:FindFirstChild("PartOwner")
                    if not po or po.Value ~= BAK_Local.Name then
                        claimOwnership(sp)
                    end
                end

                task.wait()
            end

            -- bread пропал — попробуем переспавнить (пока не стопнули)
            if not BAK_Stop then
                task.wait(0.15)
                if not BAK_Stop then
                    local c = getContainer()
                    local has = c and c:FindFirstChild("FoodBread")
                    if not has then
                        -- авто-респавн: вызываем ещё раз
                        local char2 = BAK_Local.Character
                        local hrp2 = char2 and char2:FindFirstChild("HumanoidRootPart")
                        if hrp2 then
                            local nb = spawnBread(hrp2.CFrame * CFrame.new(0, 2, 0))
                            if nb then
                                local nsp = nb:FindFirstChild("SoundPart")
                                    or nb:FindFirstChildWhichIsA("BasePart", true)
                                if nsp then
                                    claimOwnership(nsp)
                                    setNoCollide(nb)
                                    attachBodyMovers(nsp)
                                    -- рестарт цикла
                                    BAK_Active = nb
                                    BAK_Task = task.spawn(function()
                                        local lastClaim2 = 0
                                        while not BAK_Stop and nb.Parent and nsp.Parent do
                                            local cc = BAK_Local.Character
                                            local hh = cc and cc:FindFirstChild("HumanoidRootPart")
                                            local fp2 = hh and (hh:FindFirstChild("FirePlayerPart") or hh)
                                            if fp2 then
                                                local tgt = fp2.CFrame * CFrame.Angles(math.rad(90), 0, 0)
                                                local bp2 = nsp:FindFirstChild("BAK_BP")
                                                local bg2 = nsp:FindFirstChild("BAK_BG")
                                                if bp2 then bp2.Position = tgt.Position end
                                                if bg2 then bg2.CFrame = tgt end
                                                nsp.AssemblyLinearVelocity = Vector3.zero
                                                nsp.AssemblyAngularVelocity = Vector3.zero
                                            end
                                            local now2 = tick()
                                            if now2 - lastClaim2 > 0.3 then
                                                lastClaim2 = now2
                                                local po2 = nsp:FindFirstChild("PartOwner")
                                                if not po2 or po2.Value ~= BAK_Local.Name then
                                                    claimOwnership(nsp)
                                                end
                                            end
                                            task.wait()
                                        end
                                    end)
                                end
                            end
                        end
                    end
                end
            end
        end)

        return true
    end

    -- ===== UI =====
    if not DefGroup then
        DefGroup = Tabs.Defense:AddLeftGroupbox("Anti Grab")
    end

    DefGroup:AddButton({
        Text = "Bread Anti Kick",
        Func = function() runBread() end,
        DoubleClick = false,
    })
end

-- ============================================================
-- DISABLE RAGDOLL BLUR
-- ============================================================
do
    local _dbEnabled = false
    local _dbSaved   = setmetatable({}, { __mode = "k" }) -- [blur] = origEnabled
    local _dbConns   = {}

    local function _dbFind()
        local list = {}
        local cam = workspace.CurrentCamera
        if cam then
            for _, ch in ipairs(cam:GetChildren()) do
                if ch:IsA("BlurEffect") then table.insert(list, ch) end
            end
        end
        local camObj = workspace:FindFirstChild("Camera")
        if camObj and camObj ~= cam then
            for _, ch in ipairs(camObj:GetChildren()) do
                if ch:IsA("BlurEffect") then table.insert(list, ch) end
            end
        end
        return list
    end

    local function _dbDisable()
        for _, b in ipairs(_dbFind()) do
            if _dbSaved[b] == nil then
                _dbSaved[b] = b.Enabled
            end
            b.Enabled = false
        end
    end

    local function _dbRestore()
        for b, orig in pairs(_dbSaved) do
            if b and b.Parent then
                pcall(function() b.Enabled = orig end)
            end
        end
        _dbSaved = setmetatable({}, { __mode = "k" })
    end

    local function _dbStart()
        if #_dbConns > 0 then return end
        _dbDisable()

        local cam = workspace.CurrentCamera
        if cam then
            table.insert(_dbConns, cam.ChildAdded:Connect(function(ch)
                if not _dbEnabled then return end
                if ch:IsA("BlurEffect") then
                    _dbSaved[ch] = ch.Enabled
                    ch.Enabled = false
                end
            end))
        end

        table.insert(_dbConns, workspace:GetPropertyChangedSignal("CurrentCamera"):Connect(function()
            if not _dbEnabled then return end
            task.wait(0.05)
            _dbDisable()
            local newCam = workspace.CurrentCamera
            if newCam then
                table.insert(_dbConns, newCam.ChildAdded:Connect(function(ch)
                    if not _dbEnabled then return end
                    if ch:IsA("BlurEffect") then
                        _dbSaved[ch] = ch.Enabled
                        ch.Enabled = false
                    end
                end))
            end
        end))
    end

    local function _dbStop()
        for _, c in ipairs(_dbConns) do
            pcall(function() c:Disconnect() end)
        end
        _dbConns = {}
        _dbRestore()
    end

        DefGroup:AddToggle("DisableRagdollBlur", {
            Text = "Disable Ragdoll Blur",
            Default = false,
            Callback = function(v)
                _dbEnabled = v
                if v then _dbStart() else _dbStop() end
            end,
        })
    end

-- ============================================================
-- Anti Kick — Tabbox (Anti Kicks / Config)
-- ============================================================
local r32 = Tabs.Defense:AddGroupbox({
    Side = "Right",
    Name = "Anti Kick",
    IconName = "ban",
})

local AK_Tabbox = r32:AddTabbox({ Side = "Right" })
local AK_Main   = AK_Tabbox:AddTab("Anti Kicks", "swords")
local AK_Config = AK_Tabbox:AddTab("Config", "settings")

-- ============================================================
-- ГЛОБАЛЬНЫЕ ПЕРЕМЕННЫЕ
-- ============================================================
AntiKick             = "NinjaShuriken"      -- для "Anti Kick"
AntiKickItem         = "JapaneseLantern"    -- для "Anti Kick [ITEM]"

AntiKickRotationX    = 90
AntiKickRotationY    = 111
AntiKickRotationZ    = 0
AntiKickOffsetX      = 0
AntiKickOffsetY      = 0
AntiKickOffsetZ      = 0.1
AntiKickTransparency = 0

-- ============================================================
-- МАППИНГИ (только для Anti Kick [ITEM])
-- ============================================================
local AntiKickItemItems = {
    ["Japanese Lantern"] = "JapaneseLantern",
    ["Spray Can"]        = "SprayCanWD",
    ["Spooky Candle"]    = "SpookyCandle1",
    ["Alarm Clock"]      = "ClockAlarm",
}

local function sortedKeys(t)
    local keys = {}
    for k in pairs(t) do table.insert(keys, k) end
    table.sort(keys)
    return keys
end

-- ============================================================
-- CONFIG TAB
-- ============================================================
AK_Config:AddDropdown("AntiKickDropdown", {
    Text    = "Anti Kick Item",
    Values  = {
        "NinjaShuriken",
        "NinjaKunai",
        "NinjaKatana",
        "ToolCleaver",
        "ToolPickaxe",
        "ToolPencil",
        "ToolDiggingForkRusty",
    },
    Default = "NinjaShuriken",
    Multi   = false,
    Searchable = true,
    Callback = function(v)
        AntiKick = v
        local inv = workspace:FindFirstChild(
            game:GetService("Players").LocalPlayer.Name .. "SpawnedInToys"
        )
        if inv then
            local old = inv:FindFirstChild("AntiKick")
            if old then
                pcall(function()
                    game:GetService("ReplicatedStorage").MenuToys.DestroyToy:FireServer(old)
                end)
            end
        end
    end,
})

AK_Config:AddDropdown("AntiKickItemDropdown", {
    Text    = "Anti Kick [ITEM]",
    Values  = sortedKeys(AntiKickItemItems),
    Default = "Japanese Lantern",
    Multi   = false,
    Callback = function(v)
        if AntiKickItemItems[v] then
            AntiKickItem = AntiKickItemItems[v]
        end
    end,
})

AK_Config:AddDivider()

AK_Config:AddInput("AntiKickRotationXInput", {
    Text = "Rotation X",
    Default = "90",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) AntiKickRotationX = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickRotationYInput", {
    Text = "Rotation Y",
    Default = "111",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) AntiKickRotationY = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickRotationZInput", {
    Text = "Rotation Z",
    Default = "0",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) AntiKickRotationZ = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickOffsetXInput", {
    Text = "Offset X",
    Default = "0",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) AntiKickOffsetX = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickOffsetYInput", {
    Text = "Offset Y",
    Default = "0",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) AntiKickOffsetY = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickOffsetZInput", {
    Text = "Offset Z",
    Default = "0.1",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) AntiKickOffsetZ = tonumber(arg) or 0 end,
})

AK_Config:AddSlider("AntiKickTransparencySlider", {
    Text     = "Shuriken Transparency",
    Default  = 0,
    Min      = 0,
    Max      = 1,
    Rounding = 2,
    Compact  = true,
    Callback = function(arg) AntiKickTransparency = arg end,
})

-- ============================================================
-- ANTI KICKS TAB — Break PCLD
-- ============================================================
do
    local _pEnabled = false
    local _pTask    = nil
    local _pRunning = false

    local LP = game:GetService("Players").LocalPlayer
    local RS = game:GetService("ReplicatedStorage")
    local RunService = game:GetService("RunService")

    local function notify(title, desc)
        if Library and Library.Notify then
            Library:Notify({ Title = title or "Anti Kick", Description = desc or "", Duration = 3 })
        else
            warn(("[%s] %s"):format(title or "Anti Kick", tostring(desc)))
        end
    end

    local function _pKillLoop(hum, cond)
        repeat
            pcall(function() hum.Health = 0 end)
            pcall(function() hum:ChangeState(Enum.HumanoidStateType.Dead) end)
            RunService.Heartbeat:Wait()
        until cond() or not _pEnabled
    end

    local function _pBreakSequence()
        if _pRunning then return end
        _pRunning = true

        local char = LP.Character
        local hum  = char and char:FindFirstChildOfClass("Humanoid")

        if hum and hum.Health <= 0 then
            notify("PCLD Breaker", "Detected death, breaking PCLD again...")
        else
            notify("PCLD Breaker", "Starting PCLD Break...")
        end

        local first = nil
        if hum and hum.Health > 0 then
            task.spawn(_pKillLoop, hum, function() return first ~= nil end)
        end
        first = LP.CharacterAdded:Wait()
        local h1 = first:WaitForChild("Humanoid", 5)
        if not h1 then _pRunning = false; return end

        local second = nil
        task.spawn(_pKillLoop, h1, function() return second ~= nil end)
        second = LP.CharacterAdded:Wait()
        local h2 = second:WaitForChild("Humanoid", 5)
        if not h2 then _pRunning = false; return end

        h2:SetAttribute("BrokenPCLD", true)
        notify("PCLD Breaker", "Done!")
        _pRunning = false
    end

    local function _pLoop()
        while _pEnabled do
            task.wait(0.2)
            if not _pEnabled then break end

            local char = LP.Character
            local hum  = char and char:FindFirstChildOfClass("Humanoid")
            if hum and not _pRunning then
                local broken = hum:GetAttribute("BrokenPCLD")
                if not broken or hum.Health <= 0 then
                    _pBreakSequence(hum)
                end
            end
        end
    end

    AK_Main:AddToggle("BreakPCLD", {
        Text = "Break PCLD",
        Default = false,
        Callback = function(v)
            _pEnabled = v
            if v then
                if _pTask then task.cancel(_pTask) end
                _pTask = task.spawn(_pLoop)
                notify("PCLD Breaker", "Enabled")
            else
                if _pTask then task.cancel(_pTask); _pTask = nil end
                notify("PCLD Breaker", "Disabled")
            end
        end,
    })
end

-- ============================================================
-- ANTI KICKS TAB — Anti Kick (SAK)
-- ============================================================
do
    local AK_Players     = game:GetService("Players")
    local AK_RS          = game:GetService("ReplicatedStorage")
    local AK_LocalPlayer = AK_Players.LocalPlayer

    local function fixAKChar(char)
        if not char then return end
        local hum = char:FindFirstChild("Humanoid")
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if hum and hrp then
            hum.AutoRotate = true
            hum.Sit = false
            for _, part in pairs(char:GetChildren()) do
                if part:IsA("BasePart") then
                    part.CanCollide = true
                    part.CanTouch = true
                    part.CanQuery = true
                    part.Velocity = Vector3.zero
                    part.AssemblyLinearVelocity = Vector3.zero
                    part.AssemblyAngularVelocity = Vector3.zero
                end
            end
            hum:ChangeState(Enum.HumanoidStateType.Running)
        end
    end

    local function clearAntiKick()
        local inv = workspace:FindFirstChild(AK_LocalPlayer.Name .. "SpawnedInToys")
        local destroyrem = AK_RS:FindFirstChild("MenuToys") and AK_RS.MenuToys:FindFirstChild("DestroyToy")
        if inv and destroyrem then
            for _, v in pairs(inv:GetChildren()) do
                if v.Name == "AntiKick" or v.Name == AntiKick then
                    pcall(function() destroyrem:FireServer(v) end)
                end
            end
        end
    end

    local akActive = false
    local akTask = nil

    local function startAKLoop()
        if akTask then task.cancel(akTask) akTask = nil end

        akTask = task.spawn(function()
            local plr = AK_LocalPlayer
            local setOwner = AK_RS:WaitForChild("GrabEvents"):WaitForChild("SetNetworkOwner")
            local stickyEvent = AK_RS:WaitForChild("PlayerEvents"):WaitForChild("StickyPartEvent")
            local spawnRemote = AK_RS.MenuToys.SpawnToyRemoteFunction
            local canSpawn = plr:WaitForChild("CanSpawnToy")

            local function getHRP()
                if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
                    return plr.Character.HumanoidRootPart
                end
                local c = plr.CharacterAdded:Wait()
                return c:WaitForChild("HumanoidRootPart")
            end

            local function CheckForHome()
                if not workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) then return false end
                for _, v in pairs(workspace.Plots:GetChildren()) do
                    local sign = v:FindFirstChild("PlotSign")
                    local owners = sign and sign:FindFirstChild("ThisPlotsOwners")
                    if owners then
                        for _, b in pairs(owners:GetChildren()) do
                            if b.Value == plr.Name then
                                local folder = workspace.PlotItems:FindFirstChild(v.Name)
                                if folder then return true, folder end
                            end
                        end
                    end
                end
                return false
            end

            local function StickToy(toy)
                if not toy or not toy:FindFirstChild("StickyPart") then return end
                local currentHRP = getHRP()
                if not currentHRP then return end

                if toy:FindFirstChild("SoundPart") then
                    if not toy.SoundPart:FindFirstChild("PartOwner")
                        or toy.SoundPart.PartOwner.Value ~= plr.Name
                    then
                        setOwner:FireServer(toy.SoundPart, toy.SoundPart.CFrame)
                    end
                end

                local firePart = currentHRP:FindFirstChild("FirePlayerPart")
                    or currentHRP:WaitForChild("FirePlayerPart", 5)

                if firePart and toy:FindFirstChild("StickyPart") then
                    local rot = CFrame.Angles(
                        math.rad(AntiKickRotationX),
                        math.rad(AntiKickRotationY),
                        math.rad(AntiKickRotationZ)
                    )
                    local offset = CFrame.new(
                        AntiKickOffsetX,
                        AntiKickOffsetY,
                        AntiKickOffsetZ
                    )

                    local t0 = tick()
                    repeat
                        stickyEvent:FireServer(toy.StickyPart, firePart, offset * rot)
                        task.wait(0.02)
                        local weld = toy.StickyPart:FindFirstChild("StickyWeld")
                        if weld and weld.Part1 == firePart then break end
                    until tick() - t0 > 0.3
                end

                for _, obj in pairs(toy:GetChildren()) do
                    if obj:IsA("BasePart") then
                        obj.CanTouch = false
                        obj.CanCollide = false
                        obj.CanQuery = false
                        obj.Transparency = AntiKickTransparency
                    end
                end

                if toy:FindFirstChild("Handle") then
                    local handle = toy.Handle
                    if not handle:FindFirstChild("Highlight") then
                        local high = Instance.new("Highlight", handle)
                        high.FillColor = Color3.fromRGB(0, 255, 255)
                    end
                end
            end

            local function SpawnToy(name)
                local t = tick()
                while not canSpawn.Value do
                    if not akActive or tick() - t > 5 then return nil end
                    task.wait(0.05)
                end
                local currentHRP = getHRP()
                if currentHRP then
                    task.spawn(function()
                        pcall(function()
                            spawnRemote:InvokeServer(name, currentHRP.CFrame * CFrame.new(0, 12, 20), Vector3.new(0,0,0))
                        end)
                    end)
                end
                local boolik, house = CheckForHome()
                local inv = workspace:FindFirstChild(plr.Name .. "SpawnedInToys")
                if boolik and house then
                    return house:WaitForChild(name, 2)
                elseif not workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) and inv then
                    return inv:WaitForChild(name, 2)
                end
                return nil
            end

            while akActive do
                task.wait(0.005)

                if not plr.Character or not plr.Character:FindFirstChild("Humanoid") or plr.Character.Humanoid.Health <= 0 then
                    task.wait(0.5)
                    clearAntiKick()
                    repeat task.wait(0.1)
                    until (plr.Character and plr.Character:FindFirstChild("Humanoid") and plr.Character.Humanoid.Health > 0) or not akActive
                    if not akActive then break end
                    fixAKChar(plr.Character)
                    continue
                end

                local inv = workspace:FindFirstChild(plr.Name .. "SpawnedInToys")
                local toy = inv and inv:FindFirstChild(AntiKick)

                if workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) then
                    local boolik, house = CheckForHome()
                    if boolik and house and workspace.Plots:FindFirstChild(house.Name) then
                        local sign = workspace.Plots[house.Name]:FindFirstChild("PlotSign")
                        if sign and sign.ThisPlotsOwners.Value.TimeRemainingNum.Value > 89 then
                            toy = SpawnToy(AntiKick)
                            if toy == nil then return end
                            toy.Name = "AntiKick"
                            StickToy(toy)
                        end
                    end
                end

                if not toy then
                    if workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) then return end
                    toy = SpawnToy(AntiKick)
                    if toy == nil then return end
                    toy.Name = "AntiKick"
                end

                repeat
                    if toy and toy:FindFirstChild("StickyPart") and toy.StickyPart.CanTouch == true then
                        StickToy(toy)
                        toy.Name = "AntiKick"
                    end
                    task.wait(0.3)
                until not toy or not akActive
                    or not toy:FindFirstChild("StickyPart")
                    or toy.StickyPart.CanTouch == false
                    or not plr.Character
                    or not plr.Character:FindFirstChild("HumanoidRootPart")
                    or (plr.Character.HumanoidRootPart.Position - toy.StickyPart.Position).Magnitude >= 20

                if not toy or not toy:FindFirstChild("StickyPart")
                    or not plr.Character
                    or not plr.Character:FindFirstChild("HumanoidRootPart")
                    or (plr.Character.HumanoidRootPart.Position - toy.StickyPart.Position).Magnitude >= 20
                then
                    clearAntiKick()
                end

                pcall(function()
                    repeat task.wait(0.05)
                    until not akActive
                        or not plr.Character
                        or not plr.Character:FindFirstChild("Humanoid")
                        or not toy
                        or not toy:FindFirstChild("StickyPart")
                        or not toy.StickyPart:FindFirstChild("StickyWeld")
                        or not toy.StickyPart.StickyWeld.Part1
                    if not toy
                        or not toy:FindFirstChild("StickyPart")
                        or (plr.Character and plr.Character:FindFirstChild("Humanoid") and plr.Character.Humanoid.Health <= 0)
                        or not toy["StickyPart"]:FindFirstChild("StickyWeld").Part1
                    then
                        clearAntiKick()
                    end
                end)
            end
            clearAntiKick()
        end)
    end

    local akCharConn = nil
    local akRespawnConn = nil

    AK_Main:AddToggle("AntiKick", {
        Text = "Anti Kick",
        Default = false,
        Callback = function(Value)
            akActive = Value

            if akCharConn then akCharConn:Disconnect() akCharConn = nil end
            if akRespawnConn then akRespawnConn:Disconnect() akRespawnConn = nil end

            if Value then
                fixAKChar(AK_LocalPlayer.Character)

                akCharConn = AK_LocalPlayer.CharacterAdded:Connect(function(char)
                    task.wait(0.5)
                    fixAKChar(char)
                end)

                akRespawnConn = AK_LocalPlayer.CharacterAdded:Connect(function()
                    task.wait(1)
                    if akActive then
                        clearAntiKick()
                        fixAKChar(AK_LocalPlayer.Character)
                        startAKLoop()
                    end
                end)

                startAKLoop()
            else
                if akTask then task.cancel(akTask) akTask = nil end
                fixAKChar(AK_LocalPlayer.Character)
                clearAntiKick()
            end
        end,
    })
end

-- ============================================================
-- ANTI KICKS TAB — Anti Kick [ITEM]
-- ============================================================
do
    local Players = game:GetService("Players")
    local RS = game:GetService("ReplicatedStorage")
    local RunService = game:GetService("RunService")
    local plr = Players.LocalPlayer

    local AntiKickItemActive = false
    local MyPCLD = nil
    local pcldConn = nil
    local charFixConnection = nil

    local function GetMagnitude(a, b) return (a.Position - b.Position).Magnitude end
    local function FWD(parent, part, t) return parent:FindFirstChild(part) or parent:WaitForChild(part, t or 1) end

    local function CheckNetworkOwnerOnPart(Part)
        local po = Part:FindFirstChild("PartOwner")
        return po and po.Value == plr.Name
    end

    local function sno(part)
        pcall(function()
            local ge = RS:FindFirstChild("GrabEvents")
            local s = ge and ge:FindFirstChild("SetNetworkOwner")
            if s then s:FireServer(part, part.CFrame) end
        end)
    end

    local function CheckForHome()
        local plotItems = workspace:FindFirstChild("PlotItems")
        local plots = workspace:FindFirstChild("Plots")
        if plots and plotItems then
            for i = 1, 5 do
                local Plot = plots:FindFirstChild("Plot"..i)
                if Plot then
                    local sign = Plot:FindFirstChild("PlotSign")
                    local owners = sign and sign:FindFirstChild("ThisPlotsOwners")
                    if owners then
                        for _, v in pairs(owners:GetChildren()) do
                            if v.Value == plr.Name then
                                return plotItems:FindFirstChild("Plot"..i)
                            end
                        end
                    end
                end
            end
        end
        return nil
    end

    local function SpawnToy(ToyName)
        local InPlot = plr:FindFirstChild("InPlot")
        local InOwnedPlot = plr:FindFirstChild("InOwnedPlot")
        local CanSpawnToy = plr:FindFirstChild("CanSpawnToy")
        local inv = workspace:FindFirstChild(plr.Name.."SpawnedInToys")

        if InPlot and InPlot.Value and InOwnedPlot and not InOwnedPlot.Value then
            InPlot:GetPropertyChangedSignal("Value"):Wait()
        end
        if CanSpawnToy and not CanSpawnToy.Value then
            CanSpawnToy:GetPropertyChangedSignal("Value"):Wait()
        end

        local hrp = plr.Character and plr.Character:FindFirstChild("HumanoidRootPart")
        if not hrp then return nil end

        local SpawnCF = (MyPCLD or hrp).CFrame * CFrame.new(0, 14, 20)
        local Container = (InOwnedPlot and InOwnedPlot.Value) and CheckForHome() or inv
        if not Container then return nil end

        local spawnedObject = nil
        local connection
        connection = Container.ChildAdded:Connect(function(child)
            if child.Name == ToyName then spawnedObject = child end
        end)

        task.spawn(function()
            pcall(function()
                local mt = RS:FindFirstChild("MenuToys")
                local sr = mt and mt:FindFirstChild("SpawnToyRemoteFunction")
                if sr then sr:InvokeServer(ToyName, SpawnCF, Vector3.zero) end
            end)
        end)

        local start = tick()
        repeat task.wait() until spawnedObject or (tick() - start) > 2.5
        if connection then connection:Disconnect() end
        return spawnedObject
    end

    local function FindPCLD(hrp)
        if pcldConn then pcldConn:Disconnect() end
        MyPCLD = nil
        pcldConn = RunService.Heartbeat:Connect(function()
            if MyPCLD or not hrp or not hrp.Parent then
                if pcldConn then pcldConn:Disconnect() pcldConn = nil end
                return
            end
            for _, v in pairs(workspace:GetChildren()) do
                if v.Name == "PlayerCharacterLocationDetector" and v:IsA("BasePart") then
                    if GetMagnitude(v, hrp) <= 2 then
                        MyPCLD = v
                        break
                    end
                end
            end
        end)
    end

    local function fixCharacter(char)
        if not char then return end
        local hum = char:FindFirstChild("Humanoid")
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if hum and hrp then
            hum.AutoRotate = true
            hum.Sit = false
            hrp.Velocity = Vector3.zero
            hrp.AssemblyLinearVelocity = Vector3.zero
            hrp.AssemblyAngularVelocity = Vector3.zero
            hrp.CanCollide = true
            hrp.CanTouch = true
            hrp.CanQuery = true
            for _, part in pairs(char:GetChildren()) do
                if part:IsA("BasePart") then
                    part.CanCollide = true
                    part.CanTouch = true
                    part.CanQuery = true
                    part.Velocity = Vector3.zero
                    part.AssemblyLinearVelocity = Vector3.zero
                    part.AssemblyAngularVelocity = Vector3.zero
                end
            end
            hum:ChangeState(Enum.HumanoidStateType.Running)
        end
    end

    AK_Main:AddToggle("AntiKickItem", {
        Text = "Anti Kick [ITEM]",
        Default = false,
        Callback = function(Val)
            AntiKickItemActive = Val

            if Val then
                fixCharacter(plr.Character)

                if charFixConnection then charFixConnection:Disconnect() end
                charFixConnection = plr.CharacterAdded:Connect(function(char)
                    task.wait(0.5)
                    fixCharacter(char)
                end)

                task.spawn(function()
                    local Item, SoundPart
                    while AntiKickItemActive and task.wait() do
                        local char = plr.Character
                        local hrp = char and char:FindFirstChild("HumanoidRootPart")
                        local hum = char and char:FindFirstChild("Humanoid")
                        local inPlot = plr:FindFirstChild("InPlot")
                        local inv = workspace:FindFirstChild(plr.Name.."SpawnedInToys")
                        local dt = RS:FindFirstChild("MenuToys") and RS.MenuToys:FindFirstChild("DestroyToy")

                        if not hrp or not hum or hum.Health <= 0 or not inv then continue end
                        if inPlot and inPlot.Value then continue end

                        if not MyPCLD and not pcldConn then FindPCLD(hrp) end

                        Item = inv:FindFirstChild("AntiKickItem")
                        SoundPart = Item and Item:FindFirstChild("Hitbox")

                        if not Item or not SoundPart then
                            for _, v in pairs(inv:GetChildren()) do
                                if v.Name == "AntiKickItem" then
                                    pcall(function() dt:FireServer(v) end)
                                end
                            end

                            Item = SpawnToy(AntiKickItem)
                            if not Item then continue end

                            SoundPart = Item and FWD(Item, "Hitbox", 0.5)
                            if SoundPart then sno(SoundPart) end

                            for _, v in pairs(Item:GetChildren()) do
                                if v:IsA("BasePart") then
                                    v.CanCollide = false
                                    v.Transparency = 0.8
                                    v.Color = Color3.fromRGB(0, 255, 255)
                                end
                            end

                            Item.Name = "AntiKickItem"
                        end

                        if SoundPart and not CheckNetworkOwnerOnPart(SoundPart) then
                            sno(SoundPart)
                        end

                        local targetPart = MyPCLD or hrp:FindFirstChild("FirePlayerPart") or hrp

                        if SoundPart and targetPart then
                            SoundPart.CFrame = targetPart.CFrame
                            SoundPart.AssemblyLinearVelocity = Vector3.zero
                            SoundPart.AssemblyAngularVelocity = Vector3.zero
                        end
                    end
                end)
            else
                if pcldConn then pcldConn:Disconnect() pcldConn = nil end
                if charFixConnection then charFixConnection:Disconnect() charFixConnection = nil end
                MyPCLD = nil

                fixCharacter(plr.Character)

                task.spawn(function()
                    local inv = workspace:FindFirstChild(plr.Name.."SpawnedInToys")
                    local dt = RS:FindFirstChild("MenuToys") and RS.MenuToys:FindFirstChild("DestroyToy")
                    if inv and dt then
                        for _, v in pairs(inv:GetChildren()) do
                            if v.Name == "AntiKickItem" then
                                pcall(function() dt:FireServer(v) end)
                            end
                        end
                    end
                end)
            end
        end,
    })

    plr.CharacterAdded:Connect(function(char)
        if AntiKickItemActive then
            MyPCLD = nil
            local hrp = char:WaitForChild("HumanoidRootPart", 5)
            if hrp then FindPCLD(hrp) end
            task.wait(0.5)
            fixCharacter(char)
        end
    end)
end

-- ============================================================
-- ANTI KICKS TAB — Bread Anti Kick
-- ============================================================
do
    local BAK_Players = game:GetService("Players")
    local BAK_RS      = game:GetService("ReplicatedStorage")
    local BAK_Local   = BAK_Players.LocalPlayer

    BAK_Active = nil
    BAK_Task   = nil
    BAK_Stop   = false

    local function getContainer()
        return workspace:FindFirstChild(BAK_Local.Name .. "SpawnedInToys")
    end

    local function getMenuRemotes()
        local m = BAK_RS:FindFirstChild("MenuToys")
        if not m then return nil, nil end
        return m:FindFirstChild("SpawnToyRemoteFunction"),
               m:FindFirstChild("DestroyToy")
    end

    local function clearOld()
        BAK_Stop = true
        if BAK_Task then
            task.cancel(BAK_Task)
            BAK_Task = nil
        end
        local destroy = select(2, getMenuRemotes())
        local c = getContainer()
        if c then
            for _, t in ipairs(c:GetChildren()) do
                if t.Name == "FoodBread" then
                    if destroy then pcall(function() destroy:FireServer(t) end) end
                    pcall(function() t:Destroy() end)
                end
            end
        end
        BAK_Active = nil
    end

    local function spawnBread(cf)
        local spawnRF = getMenuRemotes()
        if not spawnRF then return nil end
        local c = getContainer()
        if not c then return nil end

        local before = {}
        for _, t in ipairs(c:GetChildren()) do before[t] = true end

        pcall(function()
            spawnRF:InvokeServer("FoodBread", cf or CFrame.new(0, 10, 16), Vector3.zero)
        end)

        local t0 = tick() + 1.2
        repeat
            c = getContainer()
            if c then
                for _, t in ipairs(c:GetChildren()) do
                    if not before[t] and t.Name == "FoodBread" then
                        return t
                    end
                end
            end
            task.wait(0.02)
        until tick() > t0
        return nil
    end

    local function claimOwnership(part)
        local ge = BAK_RS:FindFirstChild("GrabEvents")
        local setOwner = ge and ge:FindFirstChild("SetNetworkOwner")
        if not setOwner then return false end
        local t0 = tick() + 0.4
        repeat
            pcall(function() setOwner:FireServer(part, part.CFrame) end)
            local po = part:FindFirstChild("PartOwner")
            if po and po.Value == BAK_Local.Name then return true end
            task.wait(0.02)
        until tick() > t0
        local po = part:FindFirstChild("PartOwner")
        return po and po.Value == BAK_Local.Name
    end

    local function setNoCollide(model)
        if not model then return end
        for _, p in ipairs(model:GetDescendants()) do
            if p:IsA("BasePart") then
                p.CanCollide = false
                p.CanTouch = false
                p.CanQuery = false
            end
        end
    end

    local function attachBodyMovers(part)
        if not part then return end
        local bp = part:FindFirstChild("BAK_BP") or Instance.new("BodyPosition")
        bp.Name = "BAK_BP"
        bp.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
        bp.P = 2e5
        bp.D = 250
        bp.Position = part.Position
        bp.Parent = part

        local bg = part:FindFirstChild("BAK_BG") or Instance.new("BodyGyro")
        bg.Name = "BAK_BG"
        bg.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
        bg.P = 2e5
        bg.D = 250
        bg.CFrame = part.CFrame
        bg.Parent = part
    end

    local function runBread()
        clearOld()
        BAK_Stop = false

        local char = BAK_Local.Character
        if not char then return false end
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if not hrp then return false end

        local bread = spawnBread(hrp.CFrame * CFrame.new(0, 2, 0))
        if not bread then return false end
        BAK_Active = bread

        local sp = bread:FindFirstChild("SoundPart")
            or bread:FindFirstChildWhichIsA("BasePart", true)
        if not sp then clearOld() return false end

        claimOwnership(sp)
        setNoCollide(bread)
        attachBodyMovers(sp)

        BAK_Task = task.spawn(function()
            local lastClaim = 0
            while not BAK_Stop and bread.Parent and sp.Parent do
                local c = BAK_Local.Character
                local h = c and c:FindFirstChild("HumanoidRootPart")
                local fp = h and (h:FindFirstChild("FirePlayerPart") or h)
                if fp then
                    local target = fp.CFrame * CFrame.Angles(math.rad(90), 0, 0)
                    local bp = sp:FindFirstChild("BAK_BP")
                    local bg = sp:FindFirstChild("BAK_BG")
                    if bp then bp.Position = target.Position end
                    if bg then bg.CFrame = target end
                    sp.AssemblyLinearVelocity = Vector3.zero
                    sp.AssemblyAngularVelocity = Vector3.zero
                end

                local now = tick()
                if now - lastClaim > 0.3 then
                    lastClaim = now
                    local po = sp:FindFirstChild("PartOwner")
                    if not po or po.Value ~= BAK_Local.Name then
                        claimOwnership(sp)
                    end
                end

                task.wait()
            end
        end)

        return true
    end

    AK_Main:AddButton({
        Text = "Bread Anti Kick",
        Func = function() runBread() end,
        DoubleClick = false,
    })
end

-- ============================================================
-- ANTIS: Anti Network Ownership + Break PCLD
-- ============================================================

-- === DEPENDENCIES (self-contained) ===
local _AN_RS      = game:GetService("ReplicatedStorage")
local _AN_Players = game:GetService("Players")
local _AN_Run     = game:GetService("RunService")
local _AN_WS      = game:GetService("Workspace")
local _AN_LP      = _AN_Players.LocalPlayer

RS          = RS          or _AN_RS
Players     = Players     or _AN_Players
RunService  = RunService  or _AN_Run
Workspace   = Workspace   or _AN_WS
LocalPlayer = LocalPlayer or _AN_LP

local _AN_Lib = Library or {
    Notify = function(a, b)
        local t = type(a) == "table" and (a.Title or "") or tostring(a or "")
        local d = type(a) == "table" and (a.Description or "") or tostring(b or "")
        print("[AN-Notify]", t, d)
    end
}
local function _AN_Notify(t, d)
    _AN_Lib:Notify({ Title = t or "nLhe", Description = d or "", Duration = 3 })
end

local _AN_Tab = (Tabs and (Tabs.Def or Tabs.Defense or Tabs.Misc)) or nil
if not _AN_Tab then
    _AN_Notify("Antis", "No Tabs.Def / Tabs.Defense found. Block skipped.")
    return
end

local AntiGroup = _AN_Tab:AddRightGroupbox("Antis", "shield")

do
    local _anEnabled      = false
    local _anTask         = nil
    local _anCurrent      = nil
    local _anItem         = "FoodHamburger"
    local _anDelay        = 0.05
    local _anTransparency = 1

    local _AN_Items = {
        "FoodHamburger", "InstrumentDrumBongos", "InstrumentBrassTrumpet",
        "InstrumentVoiceMicrophone", "InstrumentWoodwindOcarina",
        "InstrumentGuitarUkulele", "InstrumentGuitarBanjo", "CupMugBrown",
        "CupMugWhite", "FoodBanana", "FoodBread", "FoodCakePink",
        "FoodCoconut", "FoodDippyEgg", "FoodDonut", "FoodFrenchFries",
        "FoodHotdog", "FoodMayonnaise", "FoodMeatStick", "FoodMushroomPoison",
        "FoodPizzaCheese", "FoodPizzaPepperoni", "PoopPile", "PoopPileSparkle",
    }

    local function _anSpawnToy(name)
        local spawnRemote = _AN_RS:FindFirstChild("MenuToys")
            and _AN_RS.MenuToys:FindFirstChild("SpawnToyRemoteFunction")
        if not spawnRemote then return nil end

        local inv = _AN_WS:FindFirstChild(_AN_LP.Name .. "SpawnedInToys")
        if not inv then return nil end

        local found = nil
        local conn
        conn = inv.ChildAdded:Connect(function(child)
            if child.Name == name then
                found = child
                if conn then conn:Disconnect() end
            end
        end)

        local cf = CFrame.new(0, 1e20, 0)
        task.spawn(function()
            pcall(function()
                spawnRemote:InvokeServer(name, cf, Vector3.zero)
            end)
        end)

        local t0 = tick()
        while not found and tick() - t0 < 2 do
            task.wait(0.02)
        end
        if conn then pcall(function() conn:Disconnect() end) end

        return found
    end

    local function _anDestroyToy(model)
        if not model or not model.Parent then return end
        local dt = _AN_RS:FindFirstChild("MenuToys")
            and _AN_RS.MenuToys:FindFirstChild("DestroyToy")
        if dt then
            pcall(function() dt:FireServer(model) end)
        end
        task.delay(0.5, function()
            if model and model.Parent then
                pcall(function() model:Destroy() end)
            end
        end)
    end

    local function _anCleanupAll()
        local inv = _AN_WS:FindFirstChild(_AN_LP.Name .. "SpawnedInToys")
        if not inv then return end
        local dt = _AN_RS:FindFirstChild("MenuToys")
            and _AN_RS.MenuToys:FindFirstChild("DestroyToy")
        for _, child in ipairs(inv:GetChildren()) do
            if child.Name == _anItem then
                if dt then
                    pcall(function() dt:FireServer(child) end)
                end
                task.delay(0.5, function()
                    if child and child.Parent then
                        pcall(function() child:Destroy() end)
                    end
                end)
            end
        end
    end

    local function _anSetupEndGrabEarly()
        local ge = _AN_RS:FindFirstChild("GrabEvents")
        if not ge then return end
        local old = ge:FindFirstChild("EndGrabEarly")
        if old then old:Destroy() end
        local re = Instance.new("RemoteEvent")
        re.Name = "EndGrabEarly"
        re.Parent = ge
    end

    local function _anLoop()
        while _anEnabled do
            task.wait(_anDelay)
            if not _anEnabled then break end

            _anSetupEndGrabEarly()

            local char = _AN_LP.Character
            local hum  = char and char:FindFirstChildOfClass("Humanoid")
            if not hum or hum.Health <= 0 then
                if _anCurrent then _anDestroyToy(_anCurrent); _anCurrent = nil end
                continue
            end

            if not _anCurrent or not _anCurrent.Parent then
                _anCurrent = _anSpawnToy(_anItem)
            end

            if _anCurrent and _anCurrent.Parent then
                local holdPart = _anCurrent:WaitForChild("HoldPart", 1)
                local holdRF   = holdPart and holdPart:WaitForChild("HoldItemRemoteFunction", 1)
                local dropRF   = holdPart and holdPart:WaitForChild("DropItemRemoteFunction", 1)

                for _, d in ipairs(_anCurrent:GetDescendants()) do
                    if d:IsA("BasePart") then
                        d.CanCollide = false
                        if d:IsA("MeshPart") or d.Name == "Part" then
                            d.Transparency = _anTransparency
                        end
                    elseif d:IsA("Decal") then
                        d.Transparency = _anTransparency
                    end
                end

                if holdRF and dropRF then
                    task.spawn(function()
                        pcall(function()
                            dropRF:InvokeServer(_anCurrent, CFrame.new(0, 1e20, 0), Vector3.zero)
                        end)
                    end)
                    task.spawn(function()
                        pcall(function()
                            holdRF:InvokeServer(_anCurrent, char)
                        end)
                    end)
                else
                    _anDestroyToy(_anCurrent)
                    _anCurrent = nil
                end
            end
        end

        if _anCurrent then
            _anDestroyToy(_anCurrent)
            _anCurrent = nil
        end
        _anCleanupAll()
    end

    AntiGroup:AddToggle("AntiNetOwner", {
        Text = "Anti Network Ownership",
        Default = false,
        Tooltip = "Anti Blob-kill, etc. Spawns item far away & re-holds to break net-owner",
        Callback = function(v)
            _anEnabled = v
            if v then
                if _anTask then
                    pcall(function() task.cancel(_anTask) end)
                    _anTask = nil
                end
                _anTask = task.spawn(_anLoop)
            else
                task.delay(0.5, function()
                    if _anCurrent then
                        _anDestroyToy(_anCurrent)
                        _anCurrent = nil
                    end
                    _anCleanupAll()
                end)
            end
        end,
    }):AddKeyPicker("AntiNetOwnerK", {
        Text = "Anti Net Owner Key",
        Default = "None",
        Mode = "Toggle",
        SyncToggleState = true,
        NoUI = false,
    })

    AntiGroup:AddDropdown("AntiNetOwnerItem", {
        Text = "Item Type",
        Values = _AN_Items,
        Default = "FoodHamburger",
        Multi = false,
        Callback = function(v) _anItem = v end,
    })

    AntiGroup:AddSlider("AntiNetOwnerDelay", {
        Text = "Grab & Drop Delay",
        Default = 0.05,
        Min = 0,
        Max = 0.3,
        Rounding = 2,
        Compact = false,
        Suffix = " sec",
        Tooltip = "Below 0.05 can cause high ping",
        Callback = function(v) _anDelay = v end,
    })

    AntiGroup:AddSlider("AntiNetOwnerTransp", {
        Text = "Item Transparency",
        Default = 1,
        Min = 0,
        Max = 1,
        Rounding = 2,
        Compact = false,
        Callback = function(v) _anTransparency = v end,
    })
end

-- ============================================================
-- BREAK PCLD  (Anti Kick 2)
-- ============================================================
do
    local _pEnabled = false
    local _pTask    = nil
    local _pRunning = false

    local function _pKillLoop(hum, cond)
        repeat
            pcall(function() hum.Health = 0 end)
            pcall(function() hum:ChangeState(Enum.HumanoidStateType.Dead) end)
            RunService.Heartbeat:Wait()
        until cond() or not _pEnabled
    end

    local function _pBreakSequence(_)
        if _pRunning then return end
        _pRunning = true

        local char = _AN_LP.Character
        local hum  = char and char:FindFirstChildOfClass("Humanoid")

        if hum and hum.Health <= 0 then
            _AN_Notify("PCLD Breaker", "Detected death, breaking PCLD again...")
        else
            _AN_Notify("PCLD Breaker", "Starting PCLD Break...")
        end

        -- pass 1
        local first = nil
        if hum and hum.Health > 0 then
            task.spawn(_pKillLoop, hum, function() return first ~= nil end)
        end
        first = _AN_LP.CharacterAdded:Wait()
        local h1 = first:WaitForChild("Humanoid", 5)
        if not h1 then _pRunning = false; return end

        -- pass 2
        local second = nil
        task.spawn(_pKillLoop, h1, function() return second ~= nil end)
        second = _AN_LP.CharacterAdded:Wait()
        local h2 = second:WaitForChild("Humanoid", 5)
        if not h2 then _pRunning = false; return end

        h2:SetAttribute("BrokenPCLD", true)
        _AN_Notify("PCLD Breaker", "Done!")
        _pRunning = false
    end

    local function _pLoop()
        while _pEnabled do
            task.wait(0.2)
            if not _pEnabled then break end

            local char = _AN_LP.Character
            local hum  = char and char:FindFirstChildOfClass("Humanoid")
            if hum and not _pRunning then
                local broken = hum:GetAttribute("BrokenPCLD")
                if not broken or hum.Health <= 0 then
                    _pBreakSequence(hum)
                end
            end
        end
    end

    AntiGroup:AddToggle("BreakPCLD", {
        Text = "[Break PCLD] Anti Kick",
        Default = false,
        Tooltip = "Unable to get kicked at all. Breaks PlayerCharacterLocationDetector on server.",
        Callback = function(v)
            _pEnabled = v
            if v then
                if _pTask then task.cancel(_pTask) end
                _pTask = task.spawn(_pLoop)
                _AN_Notify("PCLD Breaker", "Enabled")
            else
                if _pTask then task.cancel(_pTask); _pTask = nil end
                _AN_Notify("PCLD Breaker", "Disabled")
            end
        end,
    })
end

-- Создание вкладки Defense и таббокса для разделения на Toggle и Config
local Defense = Window:AddTab("Defense", "shield")

local AntiKickTabbox = Defense:AddLeftTabbox()

local AK_Toggle = AntiKickTabbox:AddTab("Toggle")
local AK_Config = AntiKickTabbox:AddTab("Config")

-- Глобальные переменные для конфигурации анти-кика
_G.AntiKickTransparency = 0
_G.AntiKickRotationX = 90
_G.AntiKickRotationY = 111
_G.AntiKickRotationZ = 0
_G.AntiKickOffsetX = 0
_G.AntiKickOffsetY = 0
_G.AntiKickOffsetZ = 0.1

-- ==== Убираем источники обводки ====
local function CleanupItemVisuals(item)
    if not item then return end
    for _, obj in ipairs(item:GetDescendants()) do
        if obj:IsA("Highlight") or obj:IsA("SelectionBox") or obj:IsA("SelectionSphere") then
            pcall(function() obj:Destroy() end)
        elseif obj:IsA("BillboardGui") or obj:IsA("SurfaceGui") then
            pcall(function() obj.Enabled = false end)
        elseif obj:IsA("Beam") or obj:IsA("Trail") then
            pcall(function()
                obj.Enabled = false
                obj.Transparency = NumberSequence.new(1)
            end)
        elseif obj:IsA("SpecialMesh") then
            pcall(function() obj.TextureId = "" end)
        elseif obj:IsA("SurfaceAppearance") then
            pcall(function() obj:Destroy() end)
        elseif obj:IsA("Decal") or obj:IsA("Texture") then
            pcall(function()
                obj.Transparency = _G.AntiKickTransparency or 0
            end)
        end
    end
end

-- ==== Прозрачность всех визуальных частей, служебные — только визуально ====
local function ApplyItemVisuals(item)
    if not item then return end
    local t = _G.AntiKickTransparency or 0
    for _, v32 in ipairs(item:GetDescendants()) do
        if v32:IsA("Part") or v32:IsA("MeshPart") then
            -- StickyPart / SoundPart — гасим визуально но не трогаем коллизию/touch/query
            if v32.Name == "StickyPart" or v32.Name == "SoundPart" then
                v32.Transparency = 1
                if v32:IsA("MeshPart") then
                    pcall(function() v32.TextureID = "" end)
                end
            elseif v32:FindFirstChild("PartOwner") then
                v32.Transparency = t
            else
                v32.Transparency = t
                if v32:IsA("MeshPart") then
                    pcall(function() v32.TextureID = "" end)
                end
                v32.CanCollide = false
            end
        end
    end
end

-- ==== Запуск цикла анти-кика (вынесено чтобы переиспользовать при респавне) ====
local function StartAntiKickLoop()
    local selectedItem = Options.AntiKickItemDropdown and Options.AntiKickItemDropdown.Value or "NinjaShuriken"

    local function ClearKunai()
        local plr = LocalPlayer
        local inv = workspace:FindFirstChild(plr.Name.."SpawnedInToys")
        local destroyrem = game.ReplicatedStorage:FindFirstChild("MenuToys") and game.ReplicatedStorage.MenuToys:FindFirstChild("DestroyToy")
        local itemName = Options.AntiKickItemDropdown and Options.AntiKickItemDropdown.Value or "NinjaShuriken"
        if inv and destroyrem then
            for _, v in pairs(inv:GetChildren()) do
                if v.Name == "AntiKick" or v.Name == itemName then
                    pcall(function() destroyrem:FireServer(v) end)
                end
            end
        end
    end

    task.spawn(function()
        local plr = LocalPlayer
        local ReplicatedStorage = game:GetService("ReplicatedStorage")
        local setOwner = ReplicatedStorage:WaitForChild("GrabEvents"):WaitForChild("SetNetworkOwner")
        local stickyEvent = ReplicatedStorage:WaitForChild("PlayerEvents"):WaitForChild("StickyPartEvent")
        local spawnRemote = ReplicatedStorage.MenuToys.SpawnToyRemoteFunction
        local canSpawn = plr:WaitForChild("CanSpawnToy")

        local function getHRP()
            if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
                return plr.Character.HumanoidRootPart
            else
                local character = plr.CharacterAdded:Wait()
                return character:WaitForChild("HumanoidRootPart")
            end
        end

        local function CheckForHome()
            if not workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) then
                return false
            end
            for _, v in pairs(workspace.Plots:GetChildren()) do
                local sign = v:FindFirstChild("PlotSign")
                local owners = sign and sign:FindFirstChild("ThisPlotsOwners")
                if owners then
                    for _, b in pairs(owners:GetChildren()) do
                        if b.Value == plr.Name then
                            local folder = workspace.PlotItems:FindFirstChild(v.Name)
                            if folder then return true, folder end
                        end
                    end
                end
            end
            return false
        end

        local function StickKunai(kunai)
            if not kunai or not kunai:FindFirstChild("StickyPart") then return end
            local currentHRP = getHRP()
            if not currentHRP then return end

            if kunai:FindFirstChild("SoundPart") then
                if not kunai.SoundPart:FindFirstChild("PartOwner") or kunai.SoundPart.PartOwner.Value ~= plr.Name then
                    setOwner:FireServer(kunai.SoundPart, kunai.SoundPart.CFrame)
                end
            end

            local firePart = currentHRP:FindFirstChild("FirePlayerPart") or currentHRP:WaitForChild("FirePlayerPart", 5)
            if firePart then
                local rotX = _G.AntiKickRotationX or 90
                local rotY = _G.AntiKickRotationY or 111
                local rotZ = _G.AntiKickRotationZ or 0
                local offX = _G.AntiKickOffsetX or 0
                local offY = _G.AntiKickOffsetY or 0
                local offZ = _G.AntiKickOffsetZ or 0.1

                local offsetCFrame = CFrame.new(offX, offY, offZ) * CFrame.Angles(math.rad(rotX), math.rad(rotY), math.rad(rotZ))
                stickyEvent:FireServer(kunai.StickyPart, firePart, offsetCFrame)
            end
        end

        local function SpawnToy(name)
            local t = tick()
            while not canSpawn.Value do
                if not _G.ShurikenAntiKick or tick() - t > 5 then return nil end
                task.wait(0.1)
            end
            local currentHRP = getHRP()
            if currentHRP then
                task.spawn(function()
                    pcall(function()
                        spawnRemote:InvokeServer(name, currentHRP.CFrame * CFrame.new(0, 12, 20), Vector3.new(0,0,0))
                    end)
                end)
            end
            local boolik, house = CheckForHome()
            local inv = workspace:FindFirstChild(plr.Name.."SpawnedInToys")
            if boolik and house then
                return house:WaitForChild(name, 2)
            elseif not workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) and inv then
                return inv:WaitForChild(name, 2)
            end
            return nil
        end

        while _G.ShurikenAntiKick do
            task.wait(0.005)
            selectedItem = Options.AntiKickItemDropdown and Options.AntiKickItemDropdown.Value or "NinjaShuriken"

            if not plr.Character or not plr.Character:FindFirstChild("Humanoid") or plr.Character.Humanoid.Health <= 0 then
                task.wait(0.3)
                continue
            end
            local inv = workspace:FindFirstChild(plr.Name.."SpawnedInToys")
            local kunai = inv and inv:FindFirstChild(selectedItem)

            if workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) then
                local boolik, house = CheckForHome()
                if boolik and house and workspace.Plots:FindFirstChild(house.Name) then
                    local sign = workspace.Plots[house.Name]:FindFirstChild("PlotSign")
                    if sign and sign.ThisPlotsOwners.Value.TimeRemainingNum.Value > 89 then
                        kunai = SpawnToy(selectedItem)
                        if kunai == nil then continue end
                        kunai.Name = "AntiKick"
                        CleanupItemVisuals(kunai)
                        ApplyItemVisuals(kunai)
                        StickKunai(kunai)
                    end
                end
            end

            if not kunai then
                if workspace.PlotItems.PlayersInPlots:FindFirstChild(plr.Name) then continue end
                kunai = SpawnToy(selectedItem)
                if kunai == nil then continue end
                kunai.Name = "AntiKick"
                CleanupItemVisuals(kunai)
                ApplyItemVisuals(kunai)
            end

            repeat
                if kunai and kunai:FindFirstChild("StickyPart") and kunai.StickyPart.CanTouch == true then
                    CleanupItemVisuals(kunai)
                    StickKunai(kunai)
                    kunai.Name = "AntiKick"
                end

                CleanupItemVisuals(kunai)
                ApplyItemVisuals(kunai)

                task.wait(0.3)
            until not kunai or not _G.ShurikenAntiKick or not kunai:FindFirstChild("StickyPart") or kunai.StickyPart.CanTouch == false
                or not plr.Character or not plr.Character:FindFirstChild("HumanoidRootPart")
                or not kunai:FindFirstChild("StickyPart")
                or (plr.Character.HumanoidRootPart.Position - kunai.StickyPart.Position).Magnitude >= 20

            if not kunai or not kunai:FindFirstChild("StickyPart") or not plr.Character or not plr.Character:FindFirstChild("HumanoidRootPart") or (plr.Character.HumanoidRootPart.Position - kunai.StickyPart.Position).Magnitude >= 20 then
                ClearKunai()
            end

            pcall(function()
                repeat
                    task.wait(0.05)
                    CleanupItemVisuals(kunai)
                    ApplyItemVisuals(kunai)
                until not _G.ShurikenAntiKick or not plr.Character or not plr.Character:FindFirstChild("Humanoid") or not kunai or not kunai:FindFirstChild("StickyPart") or not kunai.StickyPart:FindFirstChild("StickyWeld") or not kunai.StickyPart.StickyWeld.Part1

                if not kunai or not kunai:FindFirstChild("StickyPart") or (plr.Character and plr.Character:FindFirstChild("Humanoid") and plr.Character.Humanoid.Health <= 0) or not kunai["StickyPart"]:FindFirstChild("StickyWeld").Part1 then
                    ClearKunai()
                end
            end)
        end
        ClearKunai()
    end)
end

-- ==== Хранилище для авто-коннекта респавна ====
local _AntiKickRespawnConn = nil

-- Настройка подтаба Toggle
AK_Toggle:AddDropdown("AntiKickItemDropdown", {
    Values = {
        "NinjaShuriken",
        "NinjaKunai",
        "NinjaKatana",
        "ToolCleaver",
        "ToolPickaxe",
        "ToolPencil",
        "ToolDiggingForkRusty"
    },
    Default = 1,
    Text = "Anti-Kick Item",
})

AK_Toggle:AddToggle("AntiKick", {
    Text = "Anti Kick",
    Default = false,
    Callback = function(Value)
        _G.ShurikenAntiKick = Value

        if Value then
            StartAntiKickLoop()

            -- авто-восстановление при респавне
            if _AntiKickRespawnConn then
                pcall(function() _AntiKickRespawnConn:Disconnect() end)
                _AntiKickRespawnConn = nil
            end
            _AntiKickRespawnConn = LocalPlayer.CharacterAdded:Connect(function(newChar)
                if not _G.ShurikenAntiKick then return end
                -- ждём HRP и humanoid
                newChar:WaitForChild("HumanoidRootPart", 10)
                newChar:WaitForChild("Humanoid", 10)
                task.wait(0.5)
                if _G.ShurikenAntiKick then
                    StartAntiKickLoop()
                end
            end)
        else
            -- выключаем и убираем коннект
            if _AntiKickRespawnConn then
                pcall(function() _AntiKickRespawnConn:Disconnect() end)
                _AntiKickRespawnConn = nil
            end

            local plr = LocalPlayer
            local inv = workspace:FindFirstChild(plr.Name.."SpawnedInToys")
            local destroyrem = game.ReplicatedStorage:FindFirstChild("MenuToys") and game.ReplicatedStorage.MenuToys:FindFirstChild("DestroyToy")
            local selectedItem = Options.AntiKickItemDropdown and Options.AntiKickItemDropdown.Value or "NinjaShuriken"
            if inv and destroyrem then
                for _, v in pairs(inv:GetChildren()) do
                    if v.Name == "AntiKick" or v.Name == selectedItem then
                        pcall(function() destroyrem:FireServer(v) end)
                    end
                end
            end
        end
    end
})

-- Настройка подтаба Config
AK_Config:AddDivider()

AK_Config:AddInput("AntiKickRotationXInput", {
    Text = "Rotation X",
    Default = "90",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) _G.AntiKickRotationX = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickRotationYInput", {
    Text = "Rotation Y",
    Default = "111",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) _G.AntiKickRotationY = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickRotationZInput", {
    Text = "Rotation Z",
    Default = "0",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) _G.AntiKickRotationZ = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickOffsetXInput", {
    Text = "Offset X",
    Default = "0",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) _G.AntiKickOffsetX = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickOffsetYInput", {
    Text = "Offset Y",
    Default = "0",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) _G.AntiKickOffsetY = tonumber(arg) or 0 end,
})

AK_Config:AddInput("AntiKickOffsetZInput", {
    Text = "Offset Z",
    Default = "0.1",
    Numeric = true,
    ClearTextOnFocus = false,
    Callback = function(arg) _G.AntiKickOffsetZ = tonumber(arg) or 0 end,
})

AK_Config:AddSlider("AntiKickTransparencySlider", {
    Text     = "Item Transparency",
    Default  = 0,
    Min      = 0,
    Max      = 1,
    Rounding = 2,
    Compact  = true,
    Callback = function(arg) _G.AntiKickTransparency = arg end,
})

-- ============================================================
-- DEFENSE — FULL SELF-CONTAINED BLOCK
-- AutoReset + AntiPoison + AntiPaint + AntiExplosion
-- + AntiInvisiblePlayers + AntiLag/AutoAntiLag + CounterAttack
-- ============================================================
do
    -- === DEPENDENCIES (self-contained, не трогают глобалы) ===
    local Players           = game:GetService("Players")
    local RunService        = game:GetService("RunService")
    local ReplicatedStorage = game:GetService("ReplicatedStorage")
    local Workspace         = game:GetService("Workspace")
    local Debris            = game:GetService("Debris")
    local LocalPlayer       = Players.LocalPlayer

    local RS = ReplicatedStorage

    local DefenseTab = Tabs.Defense or Tabs.Def
    if not DefenseTab then
        warn("[Defense] Tabs.Defense not found — skipped")
        return
    end

    local DefenseGroup = DefenseTab:AddLeftGroupbox("Defense+", "shield-check")

    -- Локальный bool-контейнер для тоглов
    local bool = {}
    _G.__DefenseBool = bool

    -- --- helper: Notify ---
    local function notify(title, desc, dur)
        if Library and Library.Notify then
            Library:Notify({ Title = title or "nLhe", Description = desc or "", Duration = dur or 3 })
        else
            warn(("[%s] %s"):format(title or "nLhe", tostring(desc)))
        end
    end

    -- ------------------------------------------------------------
    -- AUTO RESET
    -- ------------------------------------------------------------
    do
        local kickFlags  = 0
        local lastFlagAt = 0

        RS.GameCorrectionEvents.GameCorrectionsNotify.OnClientEvent:Connect(function(reason)
            if reason ~= "Flying" then return end
            local now = tick()
            if now - lastFlagAt > 1 then
                lastFlagAt = now
                kickFlags  = 1
            else
                kickFlags  = kickFlags + 1
            end

            if bool.AutoReset then
                local char = LocalPlayer.Character
                local hum  = char and char:FindFirstChildOfClass("Humanoid")
                if hum then
                    hum:ChangeState(Enum.HumanoidStateType.Running)
                    hum:ChangeState(Enum.HumanoidStateType.Dead)
                    if kickFlags == 1 then
                        notify("Auto Reset", "Kick flag — reset", 2)
                    end
                end
            end
        end)

        DefenseGroup:AddToggle("AutoReset", {
            Text = "Auto Reset",
            Default = true,
            Tooltip = "Resets you on kick flag",
            Callback = function(state) bool.AutoReset = state end,
        })
    end

    -- ------------------------------------------------------------
    -- POISON
    -- ------------------------------------------------------------
    DefenseGroup:AddToggle("AntiPoison", {
        Text = "Anti Poison",
        Default = false,
        Tooltip = "Poison parts won't kill you",
        Callback = function(state)
            bool.AntiPoison = state
            local map  = Workspace:FindFirstChild("Map")
            local hole = map and map:FindFirstChild("Hole")
            if not hole then return end
            for _, name in ipairs({ "PoisonBigHole", "PoisonSmallHole" }) do
                local obj = hole:FindFirstChild(name)
                if obj then
                    local hurt  = obj:FindFirstChild("PoisonHurtPart")
                    local paint = obj:FindFirstChild("PaintPlayerPart")
                    if hurt  then hurt.CanTouch  = not state end
                    if paint then paint.CanTouch = not state end
                end
            end
        end,
    })

    -- ------------------------------------------------------------
    -- ANTI PAINT
    -- ------------------------------------------------------------
    do
        local paintBackup    = {}
        local paintWatchConn = nil

        local function handlePaintPart(obj)
            if not (obj:IsA("BasePart") and obj.Name == "PaintPlayerPart") then return end
            if not bool.AntiPaint then return end
            obj.CanTouch = false
            if not paintBackup[obj] then
                paintBackup[obj] = obj:GetPropertyChangedSignal("CanTouch"):Connect(function()
                    if bool.AntiPaint and obj.CanTouch then obj.CanTouch = false end
                end)
            end
        end

        DefenseGroup:AddToggle("AntiPaint", {
            Text = "Anti Paint",
            Default = false,
            Tooltip = "You won't get painted",
            Callback = function(state)
                bool.AntiPaint = state
                if state then
                    for _, obj in ipairs(Workspace:GetDescendants()) do
                        if obj:IsA("BasePart") and obj.Name == "PaintPlayerPart" then
                            handlePaintPart(obj)
                        end
                    end
                    paintWatchConn = Workspace.DescendantAdded:Connect(handlePaintPart)
                else
                    if paintWatchConn then
                        paintWatchConn:Disconnect()
                        paintWatchConn = nil
                    end
                    for obj, conn in pairs(paintBackup) do
                        pcall(function() conn:Disconnect() end)
                        if obj and obj.Parent then obj.CanTouch = true end
                    end
                    paintBackup = {}
                end
            end,
        })
    end

    -- ------------------------------------------------------------
    -- ANTI EXPLOSION
    -- ------------------------------------------------------------
    do
        local conn = nil

        DefenseGroup:AddToggle("AntiExplosion", {
            Text = "Anti Explosion",
            Default = false,
            Tooltip = "You won't get exploded",
            Callback = function(state)
                bool.AntiExplosion = state
                if conn then conn:Disconnect() conn = nil end
                if not state then return end

                conn = Workspace.ChildAdded:Connect(function(child)
                    if not bool.AntiExplosion then return end
                    if child.Name ~= "Part" or not child:IsA("BasePart") then return end

                    local char = LocalPlayer.Character
                    local hrp  = char and char:FindFirstChild("HumanoidRootPart")
                    local hum  = char and char:FindFirstChild("Humanoid")
                    if not hrp or not hum then return end
                    if (child.Position - hrp.Position).Magnitude > 20 then return end

                    task.spawn(function()
                        hrp.Anchored = true
                        task.wait(0.02)
                        hum.Sit = false
                        for _, part in ipairs(char:GetDescendants()) do
                            if part:IsA("BasePart") then
                                part.CanCollide              = false
                                part.AssemblyLinearVelocity  = Vector3.zero
                                part.AssemblyAngularVelocity = Vector3.zero
                            end
                        end
                        if hrp and hrp.Parent then
                            hrp.AssemblyLinearVelocity  = Vector3.zero
                            hrp.AssemblyAngularVelocity = Vector3.zero
                            hrp.Anchored = false
                        end
                    end)
                end)
            end,
        })
    end

    -- ------------------------------------------------------------
    -- ANTI INVISIBLE PLAYERS
    -- ------------------------------------------------------------
    do
        local task_ = nil

        DefenseGroup:AddToggle("AntiInvisiblePlayers", {
            Text = "Anti-Invisible Players [Beta]",
            Default = false,
            Tooltip = "Makes invisible players visible again",
            Callback = function(state)
                bool.AntiInvis = state
                if task_ then task.cancel(task_) task_ = nil end
                if not state then return end

                task_ = task.spawn(function()
                    while bool.AntiInvis do
                        for _, other in ipairs(Players:GetPlayers()) do
                            if other ~= LocalPlayer and other.Character then
                                local root = other.Character:FindFirstChild("HumanoidRootPart")
                                local hum  = other.Character:FindFirstChildOfClass("Humanoid")
                                if root and root.Massless then root.Massless = false end
                                if hum and hum.Sit and hum.SeatPart then
                                    local weld = hum.SeatPart:FindFirstChild("SeatWeld")
                                    if weld and not weld.Enabled then weld.Enabled = true end
                                end
                            end
                        end
                        task.wait(0.2)
                    end
                end)
            end,
        })
    end

do
    local Players    = game:GetService("Players")
    local RunService = game:GetService("RunService")
    local Workspace  = game:GetService("Workspace")
    local LocalPlayer = Players.LocalPlayer

    local tbl7 = _G.__DefenseTbl7 or {}
    local tbl8 = _G.__DefenseTbl8 or {}
    local tbl9 = _G.__DefenseTbl9 or {}
    _G.__DefenseTbl7 = tbl7
    _G.__DefenseTbl8 = tbl8
    _G.__DefenseTbl9 = tbl9

    tbl8.AntiLag       = false
    tbl8.AutoAntiLag   = true
    tbl9.AntiLagSens   = 10
    tbl9.WatchdogReady = false

    -- ============================================================
    -- ANTI STICKY LAG (hook на WeldConstraint#StickyWeld)
    -- ============================================================
    local FAR_COORD = 2147483648
    local FAR_TOL   = 1e9

    tbl7.ShurikenLagWelds = tbl7.ShurikenLagWelds or setmetatable({}, { __mode = "k" })
    tbl7.BreakPartWelds   = tbl7.BreakPartWelds   or setmetatable({}, { __mode = "k" })

    local function isFar(weld)
        local function partFar(part)
            if not part or not part:IsA("BasePart") then return false end
            local p = part.Position
            return math.abs(math.abs(p.X) - FAR_COORD) > FAR_TOL
               and math.abs(math.abs(p.Z) - FAR_COORD) > FAR_TOL
        end
        return partFar(weld.Part0) and partFar(weld.Part1)
    end

    local function unhookStickyWeld(weld, restoreParent)
        local data = tbl7.ShurikenLagWelds[weld]
        if not data then return end

        for _, conn in ipairs(data.Connections or {}) do
            pcall(function() conn:Disconnect() end)
        end
        tbl7.ShurikenLagWelds[weld] = nil

        if restoreParent and not weld.Parent and data.Parent and data.Parent.Parent then
            pcall(function() weld.Parent = data.Parent end)
        end
    end

    local function hookStickyWeld(weld)
        if not tbl8.AntiLag then return end
        if not weld:IsA("WeldConstraint") then return end
        if weld.Name ~= "StickyWeld" then return end
        if tbl7.BreakPartWelds[weld] or tbl7.ShurikenLagWelds[weld] then return end

        local data = { Parent = weld.Parent, Connections = {} }
        tbl7.ShurikenLagWelds[weld] = data

        local function update()
            if tbl7.BreakPartWelds[weld] then
                if not weld.Parent and data.Parent and data.Parent.Parent then
                    weld.Parent = data.Parent
                end
                return
            end

            if weld.Part0 and weld.Part1 and not isFar(weld) then
                if weld.Parent then
                    data.Parent = weld.Parent
                    weld.Parent = nil
                end
            elseif not weld.Parent and data.Parent and data.Parent.Parent then
                weld.Parent = data.Parent
            end
        end

        table.insert(data.Connections, weld:GetPropertyChangedSignal("Enabled"):Connect(update))
        table.insert(data.Connections, weld:GetPropertyChangedSignal("Part0"):Connect(update))
        table.insert(data.Connections, weld:GetPropertyChangedSignal("Part1"):Connect(update))
        table.insert(data.Connections, weld.Destroying:Connect(function()
            unhookStickyWeld(weld, false)
        end))

        update()
    end

    local stickyAddedConn = nil

    local function setAntiStickyLag(enabled)
        if enabled then
            for _, weld in ipairs(Workspace:QueryDescendants("WeldConstraint#StickyWeld")) do
                hookStickyWeld(weld)
            end
            if stickyAddedConn then stickyAddedConn:Disconnect() end
            stickyAddedConn = Workspace.DescendantAdded:Connect(function(desc)
                if tbl8.AntiLag then hookStickyWeld(desc) end
            end)
        else
            if stickyAddedConn then
                stickyAddedConn:Disconnect()
                stickyAddedConn = nil
            end
            for weld in pairs(tbl7.ShurikenLagWelds) do
                unhookStickyWeld(weld, true)
            end
        end
    end

    local function applyAntiLag(enabled)
        tbl8.AntiLag = enabled

        local ps = LocalPlayer.PlayerScripts
        local cb = ps:FindFirstChild("CharacterAndBeamMove")
        local st = ps:FindFirstChild("StickyPartsTouchDetection")
        if cb then cb.Enabled = not enabled end
        if st then st.Enabled = not enabled end

        setAntiStickyLag(enabled)

        if enabled then
            task.delay(0.7, function()
                if not tbl8.AntiLag then return end
                for _, other in ipairs(Players:GetPlayers()) do
                    local char = other.Character
                    if char then
                        for _, child in ipairs(char:GetChildren()) do
                            if child.Name == "GrabParts" then
                                pcall(function() child:Destroy() end)
                            end
                        end
                    end
                end
            end)
        end
    end

    task.delay(0.7, function()
        tbl9.WatchdogReady = true
    end)

    RunService.Heartbeat:Connect(function(deltaTime)
        if not tbl9.WatchdogReady then return end
        if not tbl8.AutoAntiLag then return end
        if tbl8.AntiLag then return end

        local fps = math.floor(1 / deltaTime)
        if fps < tbl9.AntiLagSens then
            if Toggles and Toggles.AntiLag then
                Toggles.AntiLag:SetValue(true)
            else
                applyAntiLag(true)
            end
            Library:Notify({
                Title       = "Auto Anti Lag",
                Description = ("Anti Lag Enabled | FPS &lt; %d"):format(tbl9.AntiLagSens),
                Duration    = 3,
            })
        end
    end)

    DefenseGroup:AddToggle("AntiLag", {
        Text    = "Anti Lag",
        Default = false,
        Tooltip = "Anti line lag & Anti sticky lag",
        Callback = function(v)
            applyAntiLag(v)
        end,
    }):AddKeyPicker("AntiLagKey", {
        Text            = "Anti Lag",
        Default         = "None",
        Mode            = "Toggle",
        SyncToggleState = true,
        NoUI            = false,
    })

    DefenseGroup:AddToggle("AutoAntiLag", {
        Text    = "Auto Anti Lag",
        Default = true,
        Callback = function(v)
            tbl8.AutoAntiLag = v
        end,
    })

    DefenseGroup:AddSlider("AntiLagSens", {
        Text     = "Auto Anti Lag Setting",
        Default  = 10,
        Min      = 1,
        Max      = 120,
        Rounding = 0,
        Suffix   = " FPS",
        Callback = function(v)
            tbl9.AntiLagSens = v
        end,
    })
end

    do
        local counterEnabled = false
        local counterMode    = "Fling"
        local conn           = nil
        local crazyline      = false
        local crazylineTask  = nil

        local GE              = RS:WaitForChild("GrabEvents")
        local SetNetOwner     = GE:WaitForChild("SetNetworkOwner")
        local DestroyGrabLine = GE:FindFirstChild("DestroyGrabLine")
        local CreateGrabEvent = GE:FindFirstChild("CreateGrabLine")

        local function getAttacker()
            local char = LocalPlayer.Character
            if not char then return nil end
            local head = char:FindFirstChild("Head")
            if not head then return nil end
            local owner = head:FindFirstChild("PartOwner")
            if not owner or not owner:IsA("StringValue") then return nil end
            if owner.Value == "" then return nil end
            return Players:FindFirstChild(owner.Value)
        end

        local function performFling(attacker)
            if not attacker or not attacker.Character then return end
            local root   = attacker.Character:FindFirstChild("HumanoidRootPart")
            local myRoot = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            if not root or not myRoot then return end
            pcall(function()
                SetNetOwner:FireServer(root, root.CFrame)
                if DestroyGrabLine then DestroyGrabLine:FireServer(root) end
                local away = (root.Position - myRoot.Position).Unit
                away = Vector3.new(away.X, 0, away.Z) * 90000
                local bv = Instance.new("BodyVelocity")
                bv.Name = "CounterFling"
                bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                bv.Velocity = away
                bv.P = 12500
                bv.Parent = root
                Debris:AddItem(bv, 0.01)
            end)
        end

        local function performKill(attacker)
            if not attacker or not attacker.Character then return end
            local root   = attacker.Character:FindFirstChild("HumanoidRootPart")
            local myRoot = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            if not root or not myRoot then return end
            pcall(function()
                SetNetOwner:FireServer(root, root.CFrame)
                if DestroyGrabLine then DestroyGrabLine:FireServer(root) end
                local away = (root.Position - myRoot.Position).Unit
                away = Vector3.new(away.X, 0, away.Z) * 99999999999999
                local bv = Instance.new("BodyVelocity")
                bv.Name = "CounterKill"
                bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                bv.Velocity = away
                bv.P = 12500
                bv.Parent = root
                Debris:AddItem(bv, 0.01)
            end)
        end

        local function performKick(attacker)
            if not attacker or not attacker.Character then return end
            local root = attacker.Character:FindFirstChild("HumanoidRootPart")
            if not root then return end
            pcall(function()
                SetNetOwner:FireServer(root, root.CFrame)
                if DestroyGrabLine then DestroyGrabLine:FireServer(root) end
                root.CFrame = CFrame.new(0, 999999999999, 0)
                local bv = Instance.new("BodyVelocity")
                bv.Name = "CounterKick"
                bv.MaxForce = Vector3.new(0, math.huge, 0)
                bv.Velocity = Vector3.new(0, 99999999999999, 0)
                bv.P = 12500
                bv.Parent = root
                Debris:AddItem(bv, 0.01)
            end)
        end

        local function performRagdoll(attacker)
            if not attacker or not attacker.Character then return end
            local root = attacker.Character:FindFirstChild("HumanoidRootPart")
            if not root then return end
            pcall(function()
                SetNetOwner:FireServer(root, root.CFrame)
                if DestroyGrabLine then DestroyGrabLine:FireServer(root) end
                local bv = Instance.new("BodyVelocity")
                bv.Name = "CounterRagdoll"
                bv.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                bv.Velocity = Vector3.new(0, -20, 0)
                bv.P = 12500
                bv.Parent = root
                Debris:AddItem(bv, 0.01)
            end)
        end

        local function performAnchor(attacker)
            if not attacker or not attacker.Character then return end
            local root = attacker.Character:FindFirstChild("HumanoidRootPart")
            if not root then return end
            pcall(function()
                SetNetOwner:FireServer(root, root.CFrame)
                if DestroyGrabLine then DestroyGrabLine:FireServer(root) end
                local bp = Instance.new("BodyPosition")
                bp.Name = "CounterAnchor"
                bp.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                bp.P = 50000
                bp.D = 1500
                bp.Position = root.Position
                bp.Parent = root
                Debris:AddItem(bp, 2)
            end)
        end

        local function performDeleteLimbs(attacker)
            if not attacker or not attacker.Character then return end
            local char  = attacker.Character
            local torso = char:FindFirstChild("Torso")
            local hum   = char:FindFirstChild("Humanoid")
            local hrp   = char:FindFirstChild("HumanoidRootPart")
            if not torso or not hum or not hrp then return end
            local ragdolled = hum:FindFirstChild("Ragdolled")
            if not ragdolled then return end

            pcall(function()
                SetNetOwner:FireServer(hrp, hrp.CFrame)
                if DestroyGrabLine then DestroyGrabLine:FireServer(hrp) end
            end)

            task.spawn(function()
                if not ragdolled.Value then
                    pcall(function()
                        RS.CharacterEvents.RagdollRemote:FireServer(hrp, 0.35)
                    end)
                    local t = tick()
                    while not ragdolled.Value and tick() - t < 0.5 do task.wait() end
                end
                if not ragdolled.Value then return end
                local saved = torso.CFrame
                Workspace.FallenPartsDestroyHeight = -10000
                for _, part in ipairs(char:GetChildren()) do
                    if part:IsA("BasePart") and (part.Name:find("Arm") or part.Name:find("Leg")) then
                        part.CFrame = CFrame.new(0, -100000, 0)
                    end
                end
                task.wait(0.15)
                if torso and torso.Parent then
                    torso.CFrame = CFrame.new(0, -11000, 0)
                    task.wait()
                    torso.CFrame = saved
                end
                Workspace.FallenPartsDestroyHeight = bool.DestroyVoid and 0/0 or -100
            end)
        end

        local function performSpamGrabLines()
            while crazyline do
                pcall(function()
                    local char  = LocalPlayer.Character
                    local head  = char and char:FindFirstChild("Head")
                    local owner = head and head:FindFirstChild("PartOwner")
                    if owner and owner:IsA("StringValue") and owner.Value ~= "" then
                        local attacker = Players:FindFirstChild(owner.Value)
                        if attacker and attacker.Character then
                            local aHead = attacker.Character:FindFirstChild("Head")
                            local aRoot = attacker.Character:FindFirstChild("HumanoidRootPart")
                            if aHead and aRoot then
                                for _ = 1, 10 do
                                    pcall(function() CreateGrabEvent:FireServer(aHead, aHead.CFrame) end)
                                end
                                for _ = 1, 10 do
                                    pcall(function() CreateGrabEvent:FireServer(aRoot, aRoot.CFrame) end)
                                end
                            end
                        end
                    end
                end)
                task.wait(0.01)
            end
        end

        local function startDefense()
            if conn then return end
            conn = RunService.Heartbeat:Connect(function()
                if not counterEnabled then return end
                local attacker = getAttacker()
                if not attacker then return end
                if counterMode == "Fling"            then performFling(attacker)
                elseif counterMode == "Kill"         then performKill(attacker)
                elseif counterMode == "Kick"         then performKick(attacker)
                elseif counterMode == "Ragdoll"      then performRagdoll(attacker)
                elseif counterMode == "Anchor"       then performAnchor(attacker)
                elseif counterMode == "Delete Limbs" then performDeleteLimbs(attacker)
                elseif counterMode == "GrabLine" then
                    if not crazylineTask then
                        crazyline = true
                        crazylineTask = task.spawn(performSpamGrabLines)
                    end
                end
            end)
        end

        local function stopDefense()
            if conn then conn:Disconnect() conn = nil end
            crazyline = false
            if crazylineTask then task.cancel(crazylineTask) crazylineTask = nil end
            for _, other in ipairs(Players:GetPlayers()) do
                local char = other.Character
                if char then
                    for _, obj in ipairs(char:GetDescendants()) do
                        if obj:IsA("BodyVelocity") and obj.Name:find("Counter") then
                            obj:Destroy()
                        elseif obj:IsA("BodyPosition") and obj.Name == "CounterAnchor" then
                            obj:Destroy()
                        end
                    end
                end
            end
        end

        LocalPlayer.CharacterAdded:Connect(function()
            if counterEnabled then
                task.wait(1)
                startDefense()
            end
        end)

        DefenseGroup:AddToggle("CounterAttack", {
            Text = "Counter Attacks",
            Default = false,
            Tooltip = "Реагирует на того, кто тебя схватил",
            Callback = function(state)
                counterEnabled = state
                if state then startDefense() else stopDefense() end
            end,
        })

        DefenseGroup:AddDropdown("CounterMode", {
            Text = "Attack Mode",
            Values = { "Fling", "Kill", "Kick", "Ragdoll", "Anchor", "Delete Limbs", "GrabLine" },
            Default = "Fling",
            Multi = false,
            Callback = function(v) counterMode = v end,
        })
    end
end

local VisualCamera = Tabs.Visual:AddLeftGroupbox("Camera")
defaultFOV = 70 

function UpdateFOV()
 local camera = workspace.CurrentCamera
 if camera then
 if Toggles.EnableFOV.Value then
 camera.FieldOfView = Options.FOVValue.Value
 else
 camera.FieldOfView = defaultFOV
 end
 end
end

VisualCamera:AddToggle("EnableFOV", {
 Text = "Custom FOV",
 Default = false,
 Tooltip = "Включить кастомный Field of View",
 Callback = function(Value)
 UpdateFOV()
 end
})

VisualCamera:AddSlider("FOVValue", {
 Text = "FOV Amount",
 Default = 70,
 Min = 0,
 Max = 120,
 Rounding = 0,
 Compact = false,
 Tooltip = "Настройка угла обзора",
 Callback = function(Value)
 UpdateFOV()
 end
})

task.spawn(function()
 while task.wait(0.1) do
 if Toggles.EnableFOV and Toggles.EnableFOV.Value then
 local camera = workspace.CurrentCamera
 if camera and camera.FieldOfView ~= Options.FOVValue.Value then
 camera.FieldOfView = Options.FOVValue.Value
 end
 end
 end
end)

local tpDefCamMode = LocalPlayer.CameraMode
local tpDefMaxZoom = LocalPlayer.CameraMaxZoomDistance
local tpDefMinZoom = LocalPlayer.CameraMinZoomDistance

do
    local blobCamActive = false
    local blobCamBound = false

    local function updateBlobCamera()
        if not blobCamActive then return end

        local char = LocalPlayer.Character
        if not char then return end

        local hum = char:FindFirstChildOfClass("Humanoid")
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if not hum or not hrp then return end

        local cam = workspace.CurrentCamera
        if not cam then return end

        if hum.Sit or hum.SeatPart then
            if cam.CameraSubject ~= hrp then
                cam.CameraSubject = hrp
            end
        else
            if cam.CameraSubject ~= hum then
                cam.CameraSubject = hum
            end
        end
    end
end

do
    local blobCamActive = false
    local blobCamBound = false
    local camSubjectConn = nil
    local camTypeConn = nil

    local function updateBlobCamera(dt)
        if not blobCamActive then return end

        local char = LocalPlayer.Character
        local hum = char and char:FindFirstChildOfClass("Humanoid")
        if not hum then return end

        local cam = workspace.CurrentCamera

        if hum.Sit and hum.SeatPart then
            if cam.CameraSubject ~= hum then
                cam.CameraSubject = hum
            end
            if cam.CameraType ~= Enum.CameraType.Custom then
                cam.CameraType = Enum.CameraType.Custom
            end
            if not hum.AutoRotate then
                hum.AutoRotate = true
            end
            if hum.CameraOffset.Magnitude > 0 then
                hum.CameraOffset = Vector3.zero
            end
        end
    end

    local function hookCamera()
        local cam = workspace.CurrentCamera

        if camSubjectConn then camSubjectConn:Disconnect() end
        if camTypeConn then camTypeConn:Disconnect() end

        camSubjectConn = cam:GetPropertyChangedSignal("CameraSubject"):Connect(function()
            if not blobCamActive then return end
            local char = LocalPlayer.Character
            local hum = char and char:FindFirstChildOfClass("Humanoid")
            if hum and hum.Sit and cam.CameraSubject ~= hum then
                cam.CameraSubject = hum
            end
        end)

        camTypeConn = cam:GetPropertyChangedSignal("CameraType"):Connect(function()
            if not blobCamActive then return end
            local char = LocalPlayer.Character
            local hum = char and char:FindFirstChildOfClass("Humanoid")
            if hum and hum.Sit and cam.CameraType ~= Enum.CameraType.Custom then
                cam.CameraType = Enum.CameraType.Custom
            end
        end)
    end

    local function unhookCamera()
        if camSubjectConn then camSubjectConn:Disconnect() camSubjectConn = nil end
        if camTypeConn    then camTypeConn:Disconnect()    camTypeConn = nil end
    end

do
    local blobCamActive = false
    local blobCamBound = false
    local camSubjectConn = nil
    local camTypeConn = nil

    local function updateBlobCamera(dt)
        if not blobCamActive then return end

        local char = LocalPlayer.Character
        local hum = char and char:FindFirstChildOfClass("Humanoid")
        if not hum then return end

        local cam = workspace.CurrentCamera

        if hum.Sit and hum.SeatPart then
            if cam.CameraSubject ~= hum then
                cam.CameraSubject = hum
            end
            if cam.CameraType ~= Enum.CameraType.Custom then
                cam.CameraType = Enum.CameraType.Custom
            end
            if not hum.AutoRotate then
                hum.AutoRotate = true
            end
            if hum.CameraOffset.Magnitude > 0 then
                hum.CameraOffset = Vector3.zero
            end
        end
    end

    local function hookCamera()
        local cam = workspace.CurrentCamera

        if camSubjectConn then camSubjectConn:Disconnect() end
        if camTypeConn then camTypeConn:Disconnect() end

        camSubjectConn = cam:GetPropertyChangedSignal("CameraSubject"):Connect(function()
            if not blobCamActive then return end
            local char = LocalPlayer.Character
            local hum = char and char:FindFirstChildOfClass("Humanoid")
            if hum and hum.Sit and cam.CameraSubject ~= hum then
                cam.CameraSubject = hum
            end
        end)

        camTypeConn = cam:GetPropertyChangedSignal("CameraType"):Connect(function()
            if not blobCamActive then return end
            local char = LocalPlayer.Character
            local hum = char and char:FindFirstChildOfClass("Humanoid")
            if hum and hum.Sit and cam.CameraType ~= Enum.CameraType.Custom then
                cam.CameraType = Enum.CameraType.Custom
            end
        end)
    end

    local function unhookCamera()
        if camSubjectConn then camSubjectConn:Disconnect() camSubjectConn = nil end
        if camTypeConn    then camTypeConn:Disconnect()    camTypeConn = nil end
    end

    VisualCamera:AddToggle("EnableBlob3rdPerson", {
        Text = "3rd Person",
        Default = false,
        Callback = function(Value)
            blobCamActive = Value

            if Value then
                LocalPlayer.CameraMode = Enum.CameraMode.Classic
                LocalPlayer.CameraMaxZoomDistance = 1000
                LocalPlayer.CameraMinZoomDistance = 0.5

                if not blobCamBound then
                    blobCamBound = true
                    RunService:BindToRenderStep(
                        "nLheBlobCam",
                        Enum.RenderPriority.Camera.Value + 1,
                        updateBlobCamera
                    )
                end

                hookCamera()
            else
                if blobCamBound then
                    blobCamBound = false
                    pcall(function()
                        RunService:UnbindFromRenderStep("nLheBlobCam")
                    end)
                end

                unhookCamera()

                local char = LocalPlayer.Character
                local hum = char and char:FindFirstChildOfClass("Humanoid")
                if hum then
                    workspace.CurrentCamera.CameraSubject = hum
                    workspace.CurrentCamera.CameraType = Enum.CameraType.Custom
                    hum.AutoRotate = true
                    hum.CameraOffset = Vector3.zero
                end

                LocalPlayer.CameraMode = Enum.CameraMode.LockFirstPerson
            end
        end,
    })
end

VisualCamera:AddSlider("ThirdPersonDistance", {
 Text = "Дальность камеры",
 Default = 128,
 Min = 5,
 Max = 400,
 Rounding = 0,
 Compact = false,
 Callback = function(Value)
 if Toggles.EnableBlob3rdPerson and Toggles.EnableBlob3rdPerson.Value then
 LocalPlayer.CameraMaxZoomDistance = Value
 end
 end
})

local VisualESP = Tabs.Visual:AddRightGroupbox("ESP")

espColor = Color3.fromRGB(255, 255, 255)
guiParent = (gethui and gethui()) or game:GetService("CoreGUI")
playerGui = LocalPlayer:FindFirstChild("PlayerGui") or LocalPlayer:WaitForChild("PlayerGui", 10)

espObjects = {}

VisualESP:AddToggle("EnableESP", {
    Text = "ESP",
    Default = false,
    Tooltip = "Включить/выключить ESP",
}):AddColorPicker("ESPColor", {
    Default = Color3.fromRGB(255, 255, 255),
    Title = "Цвет ESP",
    Callback = function(Value)
        espColor = Value
        for _, obj in pairs(espObjects) do
            if obj.hl then obj.hl.FillColor = Value; obj.hl.OutlineColor = Value end
            if obj.name then obj.name.TextColor3 = Value end
            if obj.dist then obj.dist.TextColor3 = Value end
        end
    end,
})

VisualESP:AddDropdown("ESPMode", {
    Text = "Режим",
    Default = "Контур",
    Values = {"Контур", "Заливка"},
    Multi = false,
    Tooltip = "Режим отображения ESP",
})

VisualESP:AddDropdown("ESPElements", {
    Text = "Элементы",
    Default = {"Ник"},
    Values = {"Ник", "Дистанция", "Иконка"},
    Multi = true,
    Tooltip = "Что показывать в ESP",
})

VisualESP:AddSlider("ESPSize", {
    Text = "Размер",
    Default = 12,
    Min = 6,
    Max = 30,
    Rounding = 0,
    Tooltip = "Размер текста и иконок",
})

VisualESP:AddButton({
    Text = "Сбросить элементы",
    Tooltip = "Снимает все элементы ESP",
    Func = function()
        if Options.ESPElements and Options.ESPElements.SetValue then
            pcall(function() Options.ESPElements:SetValue({}) end)
        end
    end,
})

local smoothPCLDs = {}
local pcldPlayerCache = {}
local espColorPCLD = Color3.fromRGB(255, 60, 60)
local smoothTime = 0.18
local consPCLD = {}
local rainbowPCLD = false

VisualESP:AddLabel("PCLD ESP Color"):AddColorPicker("PCLDColor", {
    Default = espColorPCLD,
    Title = "PCLD ESP Color",
    Callback = function(v)
        espColorPCLD = v
        if not rainbowPCLD then
            for _, d in pairs(smoothPCLDs) do
                if d.box then d.box.Color = v end
                if d.outline then d.outline.Color3 = v end
            end
        end
    end,
})

VisualESP:AddToggle("ViewPCLD", {
    Text = "PCLD ESP",
    Default = false,
    Callback = function(v)
        if v then
            for _, obj in ipairs(Workspace:GetChildren()) do
                if obj.Name == "PlayerCharacterLocationDetector" then
                    createSmoothPCLD(obj)
                end
            end

            consPCLD.viewpcld = Workspace.ChildAdded:Connect(function(child)
                if child.Name == "PlayerCharacterLocationDetector" then
                    task.wait(0.1)
                    createSmoothPCLD(child)
                end
            end)

            consPCLD.pcldRemoved = Workspace.ChildRemoved:Connect(function(child)
                if child.Name == "PlayerCharacterLocationDetector" then
                    removeSmoothPCLD(child)
                end
            end)
        else
            if consPCLD.viewpcld then consPCLD.viewpcld:Disconnect() end
            if consPCLD.pcldRemoved then consPCLD.pcldRemoved:Disconnect() end
            clearAllSmoothPCLDs()
        end
    end,
})

VisualESP:AddToggle("RainbowPCLD", {
    Text = "PCLD Rainbow",
    Default = false,
    Tooltip = "переливание пцлд всеми цветами радуги",
    Callback = function(v)
        rainbowPCLD = v
        if v then
            task.spawn(function()
                while rainbowPCLD do
                    local hue = tick() % 1
                    local color = Color3.fromHSV(hue, 1, 1)
                    for _, d in pairs(smoothPCLDs) do
                        if d.box then d.box.Color = color end
                        if d.outline then d.outline.Color3 = color end
                    end
                    task.wait(0.05)
                end
            end)
        else
            espColorPCLD = Options.PCLDColor.Value or Color3.fromRGB(255, 60, 60)
            for _, d in pairs(smoothPCLDs) do
                if d.box then d.box.Color = espColorPCLD end
                if d.outline then d.outline.Color3 = espColorPCLD end
            end
        end
    end,
})

local function getPlayerFromPCLD(pcld)
    local closestPlayer
    local closestDist = 10
    for _, player in ipairs(Players:GetPlayers()) do
        local char = player.Character
        local hrp = char and char:FindFirstChild("HumanoidRootPart")
        if hrp then
            local dist = (hrp.Position - pcld.Position).Magnitude
            if dist < closestDist then
                closestDist = dist
                closestPlayer = player
            end
        end
    end
    if closestPlayer then
        pcldPlayerCache[pcld] = { player = closestPlayer, time = tick() }
        return closestPlayer.DisplayName .. " (@ " .. closestPlayer.Name .. ")"
    end
    local cached = pcldPlayerCache[pcld]
    if cached and tick() - cached.time < 2 then
        local p = cached.player
        return p.DisplayName .. " (@ " .. p.Name .. ")"
    end
    return "Unknown"
end

function createSmoothPCLD(original)
    if smoothPCLDs[original] then return end
    original.Transparency = 1

    local box = Instance.new("Part")
    box.Name = "PCLD_Box"
    box.Size = original.Size
    box.CFrame = original.CFrame
    box.Anchored = true
    box.CanCollide = false
    box.CanTouch = false
    box.CanQuery = false
    box.CastShadow = false
    box.Material = Enum.Material.Neon
    box.Color = espColorPCLD
    box.Transparency = 0.45
    box.Parent = Workspace

    local outline = Instance.new("SelectionBox")
    outline.Adornee = box
    outline.LineThickness = 0.02
    outline.Color3 = espColorPCLD
    outline.Transparency = 0.1
    outline.Parent = box

    local data = { box = box, outline = outline, original = original, lastUpdate = tick(), tween = nil }
    smoothPCLDs[original] = data

    task.spawn(function()
        local lastPos = original.Position
        while box.Parent and original.Parent do
            local pos = original.Position
            local cf = original.CFrame
            if (pos - lastPos).Magnitude > 0.02 then
                lastPos = pos
                if data.tween then data.tween:Cancel() end
                data.tween = TweenService:Create(box, TweenInfo.new(smoothTime, Enum.EasingStyle.Linear), {CFrame = cf})
                data.tween:Play()
            end
            task.wait(0.03)
        end
    end)
end

function removeSmoothPCLD(original)
    local d = smoothPCLDs[original]
    if not d then return end
    if d.tween then d.tween:Cancel() end
    if d.box then d.box:Destroy() end
    smoothPCLDs[original] = nil
    pcldPlayerCache[original] = nil
end

function clearAllSmoothPCLDs()
    for _, d in pairs(smoothPCLDs) do
        if d.tween then d.tween:Cancel() end
        if d.box then d.box:Destroy() end
    end
    smoothPCLDs = {}
    pcldPlayerCache = {}
end

Options.PCLDColor:OnChanged(function()
    if not rainbowPCLD then
        espColorPCLD = Options.PCLDColor.Value
        for _, d in pairs(smoothPCLDs) do
            if d.box then d.box.Color = espColorPCLD end
            if d.outline then d.outline.Color3 = espColorPCLD end
        end
    end
end)

function createESP(plr)
    if espObjects[plr] then return end

    local hl = Instance.new("Highlight")
    hl.FillColor = espColor
    hl.OutlineColor = espColor
    hl.FillTransparency = 1
    hl.OutlineTransparency = 1
    hl.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
    hl.Enabled = false
    hl.Parent = workspace

    local bb = Instance.new("BillboardGui")
    bb.Size = UDim2.new(0, 200, 0, 60)
    bb.StudsOffset = Vector3.new(0, 3, 0)
    bb.AlwaysOnTop = true
    bb.LightInfluence = 0
    bb.MaxDistance = 600
    bb.Enabled = false
    bb.ResetOnSpawn = false
    bb.Parent = guiParent

    local nLabel = Instance.new("TextLabel")
    nLabel.Size = UDim2.new(1, 0, 0, 20)
    nLabel.BackgroundTransparency = 1
    nLabel.Text = ""
    nLabel.TextColor3 = espColor
    nLabel.TextStrokeTransparency = 0
    nLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
    nLabel.Font = Enum.Font.GothamBold
    nLabel.TextSize = 14
    nLabel.Visible = false
    nLabel.Parent = bb

    local dLabel = Instance.new("TextLabel")
    dLabel.Size = UDim2.new(1, 0, 0, 16)
    dLabel.Position = UDim2.new(0, 0, 0, 20)
    dLabel.BackgroundTransparency = 1
    dLabel.Text = ""
    dLabel.TextColor3 = espColor
    dLabel.TextStrokeTransparency = 0
    dLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
    dLabel.Font = Enum.Font.Gotham
    dLabel.TextSize = 12
    dLabel.Visible = false
    dLabel.Parent = bb

    local iLabel = Instance.new("ImageLabel")
    iLabel.Size = UDim2.new(0, 40, 0, 40)
    iLabel.Position = UDim2.new(0.5, -20, 0, 40)
    iLabel.BackgroundTransparency = 1
    iLabel.Image = ""
    iLabel.Visible = false
    iLabel.Parent = bb

    espObjects[plr] = {
        hl = hl, bb = bb,
        name = nLabel, dist = dLabel, icon = iLabel,
    }
end

function removeESP(plr)
    local obj = espObjects[plr]
    if not obj then return end
    if obj.hl then obj.hl:Destroy() end
    if obj.bb then obj.bb:Destroy() end
    espObjects[plr] = nil
end

function hasElement(el, name)
    if type(el) ~= "table" then return false end
    if el[name] == true then return true end
    for _, v in pairs(el) do
        if v == name then return true end
    end
    return false
end

function updateESP(plr)
    local obj = espObjects[plr]
    if not obj then return end

    local function hideElements()
        if obj.bb then obj.bb.Adornee = nil; obj.bb.Enabled = false end
        if obj.name then obj.name.Visible = false end
        if obj.dist then obj.dist.Visible = false end
        if obj.icon then obj.icon.Visible = false end
    end

    local function hideVisuals()
        if obj.hl then obj.hl.Enabled = false; obj.hl.Adornee = nil end
    end

    if not (Toggles.EnableESP and Toggles.EnableESP.Value) then
        hideVisuals(); hideElements(); return
    end

    local char = plr.Character
    if not char then hideVisuals(); hideElements(); return end

    local root = char:FindFirstChild("HumanoidRootPart")
    local hum = char:FindFirstChild("Humanoid")
    local head = char:FindFirstChild("Head")
    if not root or not hum or hum.Health <= 0 then
        hideVisuals(); hideElements(); return
    end

    obj.hl.FillColor = espColor
    obj.hl.OutlineColor = espColor
    obj.name.TextColor3 = espColor
    obj.dist.TextColor3 = espColor

    local mode = Options.ESPMode and Options.ESPMode.Value or "Контур"
    if mode == "Контур" then
        obj.hl.FillTransparency = 1
        obj.hl.OutlineTransparency = 0
        obj.hl.Adornee = char
        obj.hl.Enabled = true
    elseif mode == "Заливка" then
        obj.hl.FillTransparency = 0.5
        obj.hl.OutlineTransparency = 0.2
        obj.hl.Adornee = char
        obj.hl.Enabled = true
    end

    local elements = Options.ESPElements and Options.ESPElements.Value or {}
    local showN = hasElement(elements, "Ник")
    local showD = hasElement(elements, "Дистанция")
    local showI = hasElement(elements, "Иконка")
    local anyElement = showN or showD or showI

    if not anyElement then
        hideElements(); return
    end

    obj.bb.Adornee = head or root
    obj.bb.Enabled = true

    local ts = Options.ESPSize and Options.ESPSize.Value or 12
    obj.name.TextSize = ts
    obj.dist.TextSize = math.max(ts - 2, 6)
    obj.icon.Size = UDim2.new(0, ts * 3, 0, ts * 3)
    obj.icon.Position = UDim2.new(0.5, -ts * 1.5, 0, ts + 20)

    obj.name.Visible = showN
    obj.name.Text = showN and (plr.DisplayName .. " | " .. plr.Name) or ""

    if showD then
        local cam = workspace.CurrentCamera
        if cam and root then
            obj.dist.Text = string.format("%.0f studs", (root.Position - cam.CFrame.Position).Magnitude)
            obj.dist.Visible = true
        end
    else
        obj.dist.Visible = false
    end

    obj.icon.Visible = showI
    if showI and obj.icon.Image == "" then
        obj.icon.Image = string.format("rbxthumb://type=AvatarHeadShot&id=%d&w=150&h=150", plr.UserId)
    end
end

task.spawn(function()
    while task.wait(0.1) do
        if Toggles.EnableESP and Toggles.EnableESP.Value then
            for _, plr in ipairs(Players:GetPlayers()) do
                if plr ~= LocalPlayer then
                    local obj = espObjects[plr]
                    if obj and (not obj.bb.Parent or not obj.hl.Parent) then
                        removeESP(plr)
                        obj = nil
                    end
                    if not obj then createESP(plr) end
                    updateESP(plr)
                end
            end
        end
    end
end)

Players.PlayerRemoving:Connect(removeESP)

Toggles.EnableESP:OnChanged(function()
    if not Toggles.EnableESP.Value then
        for _, obj in pairs(espObjects) do
            obj.hl.Enabled = false
            obj.bb.Enabled = false
            obj.name.Visible = false
            obj.dist.Visible = false
            obj.icon.Visible = false
        end
    end
end)

-- =============================================================
--  CUSTOM MENU  (CoinBoxDesign + CoinSpinTimer + LiquidGlassMenu)
--  Таб: Visual → группа Custom Menu
-- =============================================================

local CustomMenuGroup = Tabs.Visual:AddLeftGroupbox("Custom Menu", "sparkles")

-- палитра под лого
local CMTheme = {
    Accent          = Color3.fromRGB(126, 87, 194),
    AccentDark      = Color3.fromRGB(72,  48, 122),
    AccentLight     = Color3.fromRGB(180, 150, 235),
    Text            = Color3.fromRGB(255, 255, 255),
    TextDim         = Color3.fromRGB(210, 200, 230),
    BgFrame         = Color3.fromRGB(20,  16,  30),
    BgTransparency  = 0.35,
    StrokeTransp    = 0.15,
    GlassTransp     = 0.72,
    HoverGlowAlpha  = 0.85,
    BorderTransp    = 0.3,
    CornerRadius    = UDim.new(0, 16),
    MaxBlurSize     = 22,
    MeltDuration    = 1.2,
    IconId          = "rbxassetid://87014275958938",
    TextureId       = "rbxassetid://125696751031713",
    Font            = Enum.Font.GothamBold,
}

-- runtime-состояние
local CM = {
    CoinEnabled     = false,
    GlassEnabled    = false,
    Originals       = {},
    CustomFrame     = nil,
    SpinLabel       = nil,
    CoinsLabel      = nil,
    IconLabel       = nil,
    UpdateThread    = nil,
    GlassDescConn   = nil,
    GlassVisibleConn= nil,
    GlassChangedSet = {},     -- [GuiObject] = true — что уже обработано
    GlassOriginals  = {},     -- [GuiObject] = {prop=val} — оригиналы для Glass
    GlassMeltSeq    = 0,
}

-- утилита: сохранить оригинал
local function cm_save(tbl, inst, prop, value)
    if not tbl[inst] then tbl[inst] = {} end
    if tbl[inst][prop] == nil then
        tbl[inst][prop] = inst[prop]
    end
    inst[prop] = value
end

-- утилита: восстановить
local function cm_restore(tbl, inst)
    local saved = tbl[inst]
    if not saved then return end
    for prop, val in pairs(saved) do
        pcall(function() inst[prop] = val end)
    end
    tbl[inst] = nil
end

-- утилита: парс "10:50/7:01" → "10:50", ready?
local function cm_parse_spin(txt)
    if not txt or txt == "" then return nil, false end
    txt = tostring(txt)
    if txt:lower():find("ready") then return "Ready!", true end
    local left = txt:match("^([^/]+)") or txt
    left = left:gsub("%s+", "")
    local mm, ss = left:match("^(%d+):(%d+)$")
    if mm and ss then
        local mins, secs = tonumber(mm), tonumber(ss)
        if mins == 0 and secs == 0 then return "Ready!", true end
        return string.format("%d:%02d", mins, secs), false
    end
    return left, false
end

-- получить текст спина из игры
local function cm_get_spin_text()
    local ok, res = pcall(function()
        local SlotsFolder = workspace:FindFirstChild("Slots")
        local SlotsScreen = SlotsFolder and SlotsFolder:FindFirstChild("Slots")
        local SlotGui     = SlotsScreen and SlotsScreen:FindFirstChild("Screen") and SlotsScreen.Screen:FindFirstChild("SlotGui")
        local TimeLeft    = SlotGui and SlotGui:FindFirstChild("TimeLeftFrame")
        local TimeText    = TimeLeft and TimeLeft:FindFirstChild("TimeText")
        return TimeText and TimeText.Text
    end)
    return ok and res or nil
end

-- получить коины
local function cm_get_coins()
    local ok, res = pcall(function()
        local PlayerGui = LocalPlayer:FindFirstChild("PlayerGui")
        local MenuGui   = PlayerGui and PlayerGui:FindFirstChild("MenuGui")
        local TopRight  = MenuGui and MenuGui:FindFirstChild("TopRight")
        local CoinsFrame= TopRight and TopRight:FindFirstChild("CoinsFrame")
        local CoinsDisp = CoinsFrame and CoinsFrame:FindFirstChild("CoinsDisplay")
        local CoinsText = CoinsDisp and CoinsDisp:FindFirstChild("Coins")
        return CoinsText and CoinsText.Text
    end)
    return (ok and res) or "0"
end

-- ============ COIN BOX DESIGN ============
local function cm_build_custom_frame(coinsFrame)
    if not coinsFrame then return end
    if CM.CustomFrame and CM.CustomFrame.Parent then CM.CustomFrame:Destroy() end

    local f = Instance.new("Frame")
    f.Name = "UtopaCustomCoins"
    f.BackgroundColor3 = CMTheme.BgFrame
    f.BackgroundTransparency = CMTheme.BgTransparency
    f.BorderSizePixel = 0
    f.Size = UDim2.fromOffset(240, 62)
    f.AnchorPoint = Vector2.new(1, 0.5)
    f.Position = UDim2.new(1, -8, 0.5, 0)
    f.ZIndex = 50
    f.Parent = coinsFrame

    local corner = Instance.new("UICorner", f)
    corner.CornerRadius = UDim.new(0, 14)

    local stroke = Instance.new("UIStroke", f)
    stroke.Color = CMTheme.Accent
    stroke.Thickness = 1.6
    stroke.Transparency = CMTheme.StrokeTransp
    stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

    local grad = Instance.new("UIGradient", f)
    grad.Rotation = 90
    grad.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, CMTheme.AccentDark),
        ColorSequenceKeypoint.new(1, CMTheme.BgFrame),
    })
    grad.Transparency = NumberSequence.new({
        NumberSequenceKeypoint.new(0, 0.15),
        NumberSequenceKeypoint.new(1, 0.6),
    })

    local spin = Instance.new("TextLabel", f)
    spin.Name = "SpinLine"
    spin.BackgroundTransparency = 1
    spin.Size = UDim2.new(1, -84, 0.5, 0)
    spin.Position = UDim2.new(0, 12, 0, 4)
    spin.Font = CMTheme.Font
    spin.TextSize = 18
    spin.TextColor3 = CMTheme.Text
    spin.TextXAlignment = Enum.TextXAlignment.Left
    spin.TextStrokeTransparency = 0.6
    spin.TextStrokeColor3 = Color3.new(0, 0, 0)
    spin.Text = "Spin: --:--"
    spin.ZIndex = 51

    local coins = Instance.new("TextLabel", f)
    coins.Name = "CoinsLine"
    coins.BackgroundTransparency = 1
    coins.Size = UDim2.new(1, -84, 0.5, 0)
    coins.Position = UDim2.new(0, 12, 0.5, -4)
    coins.Font = CMTheme.Font
    coins.TextSize = 18
    coins.TextColor3 = CMTheme.TextDim
    coins.TextXAlignment = Enum.TextXAlignment.Left
    coins.TextStrokeTransparency = 0.6
    coins.TextStrokeColor3 = Color3.new(0, 0, 0)
    coins.Text = "Coins: 0"
    coins.ZIndex = 51

    local icon = Instance.new("ImageLabel", f)
    icon.Name = "Icon"
    icon.BackgroundTransparency = 1
    icon.Size = UDim2.fromOffset(58, 58)
    icon.Position = UDim2.new(1, -64, 0.5, 0)
    icon.AnchorPoint = Vector2.new(0, 0.5)
    icon.Image = CMTheme.IconId
    icon.ImageColor3 = CMTheme.Text
    icon.ZIndex = 52

    CM.CustomFrame = f
    CM.SpinLabel = spin
    CM.CoinsLabel = coins
    CM.IconLabel = icon
end

local function cm_apply_coin_design()
    local PlayerGui = LocalPlayer:FindFirstChild("PlayerGui")
    local MenuGui   = PlayerGui and PlayerGui:FindFirstChild("MenuGui")
    local TopRight  = MenuGui and MenuGui:FindFirstChild("TopRight")
    if not TopRight then return end
    local CoinsFrame = TopRight:FindFirstChild("CoinsFrame")
    if not CoinsFrame then return end

    cm_save(CM.Originals, CoinsFrame, "BackgroundColor3", CMTheme.BgFrame)
    cm_save(CM.Originals, CoinsFrame, "BackgroundTransparency", CMTheme.BgTransparency)
    cm_save(CM.Originals, CoinsFrame, "BorderSizePixel", 0)
    cm_save(CM.Originals, CoinsFrame, "Size", UDim2.fromOffset(270, 66))

    local corner = CoinsFrame:FindFirstChildOfClass("UICorner") or Instance.new("UICorner", CoinsFrame)
    corner.CornerRadius = UDim.new(0, 14)

    local stroke = CoinsFrame:FindFirstChildOfClass("UIStroke") or Instance.new("UIStroke", CoinsFrame)
    stroke.Color = CMTheme.Accent
    stroke.Thickness = 1.6
    stroke.Transparency = CMTheme.StrokeTransp
    stroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
    stroke.Enabled = true

    for _, child in ipairs(CoinsFrame:GetChildren()) do
        if child:IsA("GuiObject") and child.Name ~= "UtopaCustomCoins" then
            cm_save(CM.Originals, child, "Visible", false)
        end
    end

    cm_build_custom_frame(CoinsFrame)
end

local function cm_remove_coin_design()
    if CM.CustomFrame then CM.CustomFrame:Destroy(); CM.CustomFrame = nil end
    CM.SpinLabel, CM.CoinsLabel, CM.IconLabel = nil, nil, nil
    for inst, _ in pairs(CM.Originals) do
        pcall(function() cm_restore(CM.Originals, inst) end)
    end
    CM.Originals = {}
end

local function cm_update_loop()
    while CM.CoinEnabled do
        task.wait(1)
        if not CM.CoinEnabled then break end
        local spinText, isReady = cm_parse_spin(cm_get_spin_text())
        local coinsText = cm_get_coins()
        if CM.SpinLabel then
            if isReady then
                CM.SpinLabel.Text = "Spin: Ready!"
                CM.SpinLabel.TextColor3 = CMTheme.AccentLight
            else
                CM.SpinLabel.Text = "Spin: " .. tostring(spinText)
                CM.SpinLabel.TextColor3 = CMTheme.Text
            end
        end
        if CM.CoinsLabel then
            CM.CoinsLabel.Text = "Coins: " .. tostring(coinsText)
        end
    end
end

-- ============ LIQUID GLASS MENU ============
local function cm_glass_get_menu()
    local PlayerGui = LocalPlayer:FindFirstChild("PlayerGui")
    local MenuGui   = PlayerGui and PlayerGui:FindFirstChild("MenuGui")
    return MenuGui and MenuGui:FindFirstChild("Menu")
end

local function cm_glass_style_one(obj)
    if not obj or not obj:IsA("GuiObject") then return end
    if CM.GlassChangedSet[obj] then return end
    CM.GlassChangedSet[obj] = true

    -- не трогаем наш кастомный коин-фрейм и кнопку rejoin
    if obj.Name == "UtopaCustomCoins" or obj.Name == "UtopaGlassRejoin" then return end

    -- защита: не трогаем поля ввода / color picker
    local nameLower = string.lower(obj.Name)
    if obj:IsA("TextBox") then return end

    if obj:IsA("Frame") or obj:IsA("ScrollingFrame") then
        cm_save(CM.GlassOriginals, obj, "BackgroundTransparency", CMTheme.GlassTransp)
        cm_save(CM.GlassOriginals, obj, "BorderSizePixel", 0)
    elseif obj:IsA("TextLabel") or obj:IsA("TextButton") or obj:IsA("ImageLabel") or obj:IsA("ImageButton") then
        cm_save(CM.GlassOriginals, obj, "BackgroundTransparency", 1)
        cm_save(CM.GlassOriginals, obj, "BorderSizePixel", 0)
    end

    if not obj:FindFirstChildOfClass("UICorner") then
        local c = Instance.new("UICorner", obj)
        c.CornerRadius = CMTheme.CornerRadius
    end

    if obj:IsA("TextButton") or obj:IsA("ImageButton") then
        local glow = obj:FindFirstChild("UtopaGlassGlow") or Instance.new("UIStroke", obj)
        glow.Name = "UtopaGlassGlow"
        glow.Thickness = 0
        glow.Color = CMTheme.Accent
        glow.Transparency = 0.5
        glow.Parent = obj

        local scale = obj:FindFirstChildOfClass("UIScale") or Instance.new("UIScale", obj)

        obj.MouseEnter:Connect(function()
            if not CM.GlassEnabled then return end
            obj:SetAttribute("UtopaHovering", true)
            TweenService:Create(obj, TweenInfo.new(0.35), {
                BackgroundTransparency = CMTheme.HoverGlowAlpha,
                BackgroundColor3 = CMTheme.AccentDark,
            }):Play()
            TweenService:Create(glow, TweenInfo.new(0.35), { Thickness = 2.4 }):Play()
            TweenService:Create(scale, TweenInfo.new(0.35, Enum.EasingStyle.Back, Enum.EasingDirection.Out), { Scale = 1.05 }):Play()
        end)

        obj.MouseLeave:Connect(function()
            if not CM.GlassEnabled then return end
            TweenService:Create(obj, TweenInfo.new(0.35), {
                BackgroundTransparency = 1,
                BackgroundColor3 = CMTheme.Accent,
            }):Play()
            TweenService:Create(glow, TweenInfo.new(0.35), { Thickness = 0 }):Play()
            TweenService:Create(scale, TweenInfo.new(0.35, Enum.EasingStyle.Back, Enum.EasingDirection.Out), { Scale = 1 }):Play()
            task.delay(0.35, function()
                obj:SetAttribute("UtopaHovering", false)
            end)
        end)

        obj.MouseButton1Down:Connect(function()
            if not CM.GlassEnabled then return end
            TweenService:Create(scale, TweenInfo.new(0.15, Enum.EasingStyle.Sine), { Scale = 0.93 }):Play()
            cm_glass_melt(obj)
        end)

        obj.MouseButton1Up:Connect(function()
            if not CM.GlassEnabled then return end
            TweenService:Create(scale, TweenInfo.new(0.35, Enum.EasingStyle.Back, Enum.EasingDirection.Out), { Scale = 1.05 }):Play()
        end)
    end
end

function cm_glass_melt(parent)
    CM.GlassMeltSeq = CM.GlassMeltSeq + 1
    local seq = CM.GlassMeltSeq

    local f = Instance.new("Frame")
    f.Name = "UtopaGlassMelt_" .. seq
    f.BackgroundColor3 = CMTheme.Accent
    f.BackgroundTransparency = 0.85
    f.AnchorPoint = Vector2.new(0.5, 0.5)
    f.Size = UDim2.fromOffset(0, 0)
    f.Position = UDim2.fromScale(0.5, 0.5)
    f.ZIndex = 5000
    f.Parent = parent
    Instance.new("UICorner", f).CornerRadius = UDim.new(1, 0)

    TweenService:Create(f, TweenInfo.new(CMTheme.MeltDuration, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), {
        Size = UDim2.fromOffset(600, 600),
        BackgroundTransparency = 1,
    }):Play()
    Debris:AddItem(f, CMTheme.MeltDuration + 0.2)
end

local function cm_glass_apply_menu()
    local menu = cm_glass_get_menu()
    if not menu then return end

    -- лого
    local oldLogo = menu:FindFirstChild("UtopaGlassLogo")
    if oldLogo then oldLogo:Destroy() end
    local logo = Instance.new("ImageLabel")
    logo.Name = "UtopaGlassLogo"
    logo.Size = UDim2.fromOffset(100, 100)
    logo.Position = UDim2.new(1, -30, 0, 10)
    logo.AnchorPoint = Vector2.new(1, 0)
    logo.BackgroundTransparency = 1
    logo.Image = CMTheme.IconId
    logo.ImageColor3 = CMTheme.Text
    logo.ImageTransparency = 0.25
    logo.ZIndex = 10000
    logo.Parent = menu

    -- rejoin
    local oldRejoin = menu:FindFirstChild("UtopaGlassRejoin")
    if oldRejoin then oldRejoin:Destroy() end
    local rj = Instance.new("TextButton")
    rj.Name = "UtopaGlassRejoin"
    rj.Size = UDim2.fromOffset(110, 34)
    rj.Position = UDim2.new(0, 16, 0, 16)
    rj.BackgroundColor3 = CMTheme.Accent
    rj.BackgroundTransparency = 0.35
    rj.Text = "REJOIN"
    rj.TextColor3 = CMTheme.Text
    rj.TextSize = 14
    rj.Font = CMTheme.Font
    rj.ZIndex = 10000
    rj.Parent = menu
    Instance.new("UICorner", rj).CornerRadius = UDim.new(0, 12)
    local rjStroke = Instance.new("UIStroke", rj)
    rjStroke.Thickness = 2
    rjStroke.Color = CMTheme.AccentLight
    rjStroke.Transparency = 0.4
    rjStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

    rj.MouseButton1Click:Connect(function()
        pcall(function()
            if #Players:GetPlayers() <= 1 then
                LocalPlayer:Kick("\nRejoining...")
                task.wait(0.1)
                TeleportService:Teleport(game.PlaceId, LocalPlayer)
            else
                TeleportService:TeleportToPlaceInstance(game.PlaceId, game.JobId, LocalPlayer)
            end
        end)
    end)

    -- стилизуем всё что есть
    for _, obj in ipairs(menu:GetDescendants()) do
        cm_glass_style_one(obj)
    end

    -- на будущие добавления
    if CM.GlassDescConn then CM.GlassDescConn:Disconnect() end
    CM.GlassDescConn = menu.DescendantAdded:Connect(function(obj)
        if CM.GlassEnabled then
            task.defer(cm_glass_style_one, obj)
        end
    end)

    -- blur
    local blur = Lighting:FindFirstChild("UtopaGlassBlur") or Instance.new("BlurEffect", Lighting)
    blur.Name = "UtopaGlassBlur"
    TweenService:Create(blur, TweenInfo.new(0.3, Enum.EasingStyle.Sine), { Size = CMTheme.MaxBlurSize }):Play()

    -- видимость меню = вкл/выкл blur
    if CM.GlassVisibleConn then CM.GlassVisibleConn:Disconnect() end
    CM.GlassVisibleConn = menu:GetPropertyChangedSignal("Visible"):Connect(function()
        if not CM.GlassEnabled then return end
        local target = menu.Visible and CMTheme.MaxBlurSize or 0
        TweenService:Create(blur, TweenInfo.new(0.3), { Size = target }):Play()
    end)
end

local function cm_glass_remove()
    if CM.GlassDescConn then CM.GlassDescConn:Disconnect(); CM.GlassDescConn = nil end
    if CM.GlassVisibleConn then CM.GlassVisibleConn:Disconnect(); CM.GlassVisibleConn = nil end

    for inst, _ in pairs(CM.GlassOriginals) do
        pcall(function() cm_restore(CM.GlassOriginals, inst) end)
    end
    CM.GlassOriginals = {}
    CM.GlassChangedSet = {}

    local menu = cm_glass_get_menu()
    if menu then
        for _, n in ipairs({ "UtopaGlassLogo", "UtopaGlassRejoin" }) do
            local x = menu:FindFirstChild(n)
            if x then x:Destroy() end
        end
    end

    local blur = Lighting:FindFirstChild("UtopaGlassBlur")
    if blur then
        TweenService:Create(blur, TweenInfo.new(0.2), { Size = 0 }):Play()
        Debris:AddItem(blur, 0.4)
    end
end

-- ============ UI ============
local cm_setcoins_buf = ""

CustomMenuGroup:AddInput("CustomMenuSetCoins", {
    Text = "Set Coins",
    Default = "",
    Placeholder = "Input a Number",
    Numeric = true,
    Finished = false,
    Callback = function(arg) cm_setcoins_buf = arg end,
})

CustomMenuGroup:AddButton({
    Text = "Apply Coins",
    Func = function()
        local n = tonumber(cm_setcoins_buf) or 0
        pcall(function()
            local PlayerGui = LocalPlayer:FindFirstChild("PlayerGui")
            local MenuGui   = PlayerGui and PlayerGui:FindFirstChild("MenuGui")
            local TopRight  = MenuGui and MenuGui:FindFirstChild("TopRight")
            local CoinsFrame= TopRight and TopRight:FindFirstChild("CoinsFrame")
            local CoinsDisp = CoinsFrame and CoinsFrame:FindFirstChild("CoinsDisplay")
            local CoinsText = CoinsDisp and CoinsDisp:FindFirstChild("Coins")
            if CoinsText then CoinsText.Text = tostring(n) end
        end)
    end,
})

CustomMenuGroup:AddDivider()

CustomMenuGroup:AddToggle("CustomMenu", {
    Text = "Custom Menu",
    Default = false,
    Tooltip = "Стилизует коины + счёт до спина",
    Callback = function(Value)
        CM.CoinEnabled = Value
        if Value then
            cm_apply_coin_design()
            if CM.UpdateThread then task.cancel(CM.UpdateThread) end
            CM.UpdateThread = task.spawn(cm_update_loop)
        else
            if CM.UpdateThread then task.cancel(CM.UpdateThread); CM.UpdateThread = nil end
            cm_remove_coin_design()
        end
    end,
})

CustomMenuGroup:AddToggle("LiquidGlassMenu", {
    Text = "Liquid Glass Menu",
    Default = false,
    Tooltip = "Стеклянное меню игрушек",
    Callback = function(Value)
        CM.GlassEnabled = Value
        if Value then
            cm_glass_apply_menu()
        else
            cm_glass_remove()
        end
    end,
})

-- ============================================================
-- Misc → Gamepasses
-- ============================================================

-- === DEPENDENCIES (только если чего-то нет у тебя) ===
local Players           = Players           or game:GetService("Players")
local ReplicatedStorage = ReplicatedStorage or game:GetService("ReplicatedStorage")
local Workspace         = Workspace         or game:GetService("Workspace")
local LocalPlayer       = LocalPlayer       or Players.LocalPlayer

-- Resonance-таблицы. Если у тебя уже есть — не перезаписывай, оставь свои.
tbl7 = tbl7 or {}
tbl8 = tbl8 or {}
tbl9 = tbl9 or {}

tbl7.Gradients = tbl7.Gradients or {
    Color1   = Color3.fromRGB(255, 0, 0),
    Color2   = Color3.fromRGB(255, 165, 0),
    Color3   = Color3.fromRGB(255, 255, 0),
    Color4   = Color3.fromRGB(0, 255, 0),
    Color5   = Color3.fromRGB(0, 255, 255),
    Color6   = Color3.fromRGB(0, 0, 255),
    Color7   = Color3.fromRGB(170, 0, 255),
    Color8   = Color3.fromRGB(255, 255, 255),
    DotColor = Color3.fromRGB(255, 255, 255),
}

tbl8.GradientLine = tbl8.GradientLine or false
tbl8.FasterEscape = tbl8.FasterEscape or false
tbl9.FasterEscape = tbl9.FasterEscape or 3

-- Notify-враппер. У тебя nLheNotify, если есть — оставь.
local fn18 = fn18 or function(msg, title, soundId, duration, silent)
    if _G.nLheNotify then
        _G.nLheNotify(title or "nLhe", tostring(msg), "info", duration or 3)
    elseif Library and Library.Notify then
        Library:Notify({
            Title       = title or "nLhe",
            Description = tostring(msg),
            Duration    = duration or 3,
        })
    else
        warn(("[%s] %s"):format(title or "nLhe", tostring(msg)))
    end
end

-- Флаг выгрузки скрипта. У Resonance — flag11. У тебя пусть будет false.
local flag11 = false


-- ============================================================
-- GAME PASSES GROUP
-- ============================================================
do
    local MiscTab = Tabs and Tabs.Misc
    if not MiscTab then
        warn("[Gamepasses] Tabs.Misc not found — skipped")
        return
    end

    local Gamepasses  = MiscTab:AddLeftTabbox("Gamepasses")
    local Gamepasses2 = Gamepasses:AddTab("Gamepasses", "dollar-sign")
    local tbl16 = { Enabled = false }

    -- ---------------------------------------------
    -- Further Reach Line (free gamepass)
    -- ---------------------------------------------
    Gamepasses2:AddToggle("FartherReach", {
        Text = "Further Reach Line",
        Default = false,
        Tooltip = "Increases your reach",
        Callback = function(arg)
            local flag12 = arg and not flag11
            if tbl16.Enabled == flag12 then return end

            if flag12 then
                local gamepassEvents = ReplicatedStorage:FindFirstChild("GamepassEvents")
                local menuToys       = ReplicatedStorage:FindFirstChild("MenuToys")
                local furtherReachBoughtNotifier = gamepassEvents and gamepassEvents:FindFirstChild("FurtherReachBoughtNotifier")
                local limitedTimeToyEvent        = menuToys and menuToys:FindFirstChild("LimitedTimeToyEvent")
                local fartherReach               = LocalPlayer:FindFirstChild("FartherReach")

                if not (furtherReachBoughtNotifier and furtherReachBoughtNotifier:IsA("RemoteEvent")
                        and limitedTimeToyEvent and limitedTimeToyEvent:IsA("RemoteEvent"))
                    or (fartherReach and not fartherReach:IsA("BoolValue")) then
                    toggles.FartherReach:SetValue(false)
                    return fn18("Further Reach is unavailable: required game objects are missing or invalid.")
                end

                tbl16.Enabled = true
                tbl16.Notifier = furtherReachBoughtNotifier
                tbl16.Event    = limitedTimeToyEvent
                tbl16.Events   = gamepassEvents
                tbl16.Toys     = menuToys

                local boolValue     = fartherReach or Instance.new("BoolValue")
                local prevLineValue = fartherReach and fartherReach.Value

                tbl16.Line      = boolValue
                tbl16.LineValue = prevLineValue

                boolValue.Name   = "FartherReach"
                boolValue.Value  = true
                boolValue.Parent = LocalPlayer

                furtherReachBoughtNotifier.Parent = Workspace
                limitedTimeToyEvent.Name          = "FurtherReachBoughtNotifier"
                limitedTimeToyEvent.Parent        = gamepassEvents

                local connection = nil

                local function fireEventOnce()
                    local char = LocalPlayer.Character
                    local grabbingScript = char and char:FindFirstChild("GrabbingScript")
                    if connection and connection.Connected
                        and not flag11
                        and grabbingScript and grabbingScript.Parent == char
                        and grabbingScript.Enabled
                        and limitedTimeToyEvent.Parent then
                        limitedTimeToyEvent:FireServer()
                    end
                end

                local function onCharAdded(character)
                    if not connection or not connection.Connected or flag11 then return end
                    local grabbingScript = character and character:WaitForChild("GrabbingScript", 5)
                    if not (connection.Connected and not flag11
                            and character == LocalPlayer.Character
                            and grabbingScript and grabbingScript.Parent == character
                            and grabbingScript:IsA("LocalScript")) then
                        return
                    end

                    if tbl16.Script then tbl16.Script:Disconnect() end

                    grabbingScript.Enabled = false
                    grabbingScript.Enabled = true

                    tbl16.Script = grabbingScript:GetPropertyChangedSignal("Enabled"):Connect(function()
                        if grabbingScript.Enabled then
                            task.delay(1, fireEventOnce)
                        end
                    end)

                    task.delay(1, fireEventOnce)
                end

                connection = LocalPlayer.CharacterAdded:Connect(onCharAdded)
                tbl16.Connection = connection
                task.spawn(onCharAdded, LocalPlayer.Character)

            else
                tbl16.Enabled = false

                if tbl16.Connection then tbl16.Connection:Disconnect() end
                if tbl16.Script     then tbl16.Script:Disconnect()     end

                if tbl16.Line and tbl16.Line.Parent then
                    if tbl16.LineValue == nil then
                        tbl16.Line:Destroy()
                    else
                        tbl16.Line.Value = tbl16.LineValue
                    end
                end

                if tbl16.Event and tbl16.Event.Parent and tbl16.Toys.Parent then
                    tbl16.Event.Name   = "LimitedTimeToyEvent"
                    tbl16.Event.Parent = tbl16.Toys
                end

                if tbl16.Notifier and tbl16.Notifier.Parent and tbl16.Events.Parent then
                    tbl16.Notifier.Parent = tbl16.Events
                end

                tbl16.Connection = nil
                tbl16.Script     = nil
                tbl16.Line       = nil
                tbl16.Event      = nil
                tbl16.Notifier   = nil

                local grabbingScript = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("GrabbingScript")
                if grabbingScript and grabbingScript:IsA("LocalScript") then
                    grabbingScript.Enabled = false
                    grabbingScript.Enabled = true
                end
            end

            local grabParts = Workspace:FindFirstChild("GrabParts")
            if grabParts then grabParts:Destroy() end
        end,
    })

    -- ---------------------------------------------
    -- Gradient Line
    -- ---------------------------------------------
    Gamepasses2:AddToggle("GradientLineT", {
        Text = "Gradient Line",
        Default = false,
        Tooltip = "Changes the color of your line to the selected gradient in Config",
        Callback = function(gradientLine)
            tbl8.GradientLine = gradientLine

            task.spawn(function()
                local gradients = tbl7.Gradients

                while task.wait(0.5) and tbl8.GradientLine do
                    local dataEvents  = ReplicatedStorage:FindFirstChild("DataEvents")
                    local updateEvent = dataEvents and dataEvents:FindFirstChild("UpdateLineColorsEvent")
                    if not updateEvent then return end

                    local g = gradients
                    local points = {
                        ColorSequenceKeypoint.new(0,     g.Color1),
                        ColorSequenceKeypoint.new(0.125, g.Color2),
                        ColorSequenceKeypoint.new(0.25,  g.Color3),
                        ColorSequenceKeypoint.new(0.375, g.Color4),
                        ColorSequenceKeypoint.new(0.5,   g.Color5),
                        ColorSequenceKeypoint.new(0.625, g.Color6),
                        ColorSequenceKeypoint.new(0.75,  g.Color7),
                        ColorSequenceKeypoint.new(0.875, g.Color8),
                        ColorSequenceKeypoint.new(1,     g.DotColor),
                    }

                    updateEvent:FireServer(
                        ColorSequence.new(points),
                        g.Color1, g.Color2, g.Color3, g.Color4,
                        g.Color5, g.Color6, g.Color7, g.Color8,
                        g.DotColor
                    )
                end
            end)
        end,
    })

    -- ---------------------------------------------
    -- Faster Escape
    -- ---------------------------------------------
    Gamepasses2:AddToggle("FasterEscapeT", {
        Text = "Faster Escape",
        Default = false,
        Tooltip = "Allows you to escape in 3 seconds instead of 12",
        Callback = function(fasterEscape)
            tbl8.FasterEscape = fasterEscape
        end,
    })

    -- =============================================
    -- Config tab
    -- =============================================
    local Config = Gamepasses:AddTab("Config", "settings")

    Config:AddSlider("FastEscapeSlider", {
        Text = "Faster Escape",
        Default = 3,
        Min = 0,
        Max = 12,
        Rounding = 0,
        Compact = true,
        Callback = function(fasterEscape)
            tbl9.FasterEscape = fasterEscape
        end,
    })

    Config:AddDivider()

    Config:AddLabel("Line Color 1"):AddColorPicker("LineC1", {
        Default = tbl7.Gradients.Color1,
        Title = "Line Color 1",
        Callback = function(v) tbl7.Gradients.Color1 = v end,
    })
    Config:AddLabel("Line Color 2"):AddColorPicker("LineC2", {
        Default = tbl7.Gradients.Color2,
        Title = "Line Color 2",
        Callback = function(v) tbl7.Gradients.Color2 = v end,
    })
    Config:AddLabel("Line Color 3"):AddColorPicker("LineC3", {
        Default = tbl7.Gradients.Color3,
        Title = "Line Color 3",
        Callback = function(v) tbl7.Gradients.Color3 = v end,
    })
    Config:AddLabel("Line Color 4"):AddColorPicker("LineC4", {
        Default = tbl7.Gradients.Color4,
        Title = "Line Color 4",
        Callback = function(v) tbl7.Gradients.Color4 = v end,
    })
    Config:AddLabel("Line Color 5"):AddColorPicker("LineC5", {
        Default = tbl7.Gradients.Color5,
        Title = "Line Color 5",
        Callback = function(v) tbl7.Gradients.Color5 = v end,
    })
    Config:AddLabel("Line Color 6"):AddColorPicker("LineC6", {
        Default = tbl7.Gradients.Color6,
        Title = "Line Color 6",
        Callback = function(v) tbl7.Gradients.Color6 = v end,
    })
    Config:AddLabel("Line Color 7"):AddColorPicker("LineC7", {
        Default = tbl7.Gradients.Color7,
        Title = "Line Color 7",
        Callback = function(v) tbl7.Gradients.Color7 = v end,
    })
    Config:AddLabel("Line Color 8"):AddColorPicker("LineC8", {
        Default = tbl7.Gradients.Color8,
        Title = "Line Color 8",
        Callback = function(v) tbl7.Gradients.Color8 = v end,
    })
    Config:AddLabel("Dot Color"):AddColorPicker("DotColor", {
        Default = tbl7.Gradients.DotColor,
        Title = "Dot Color",
        Callback = function(v) tbl7.Gradients.DotColor = v end,
    })
end

-- ============================================================
-- Misc → Cheaters
-- ============================================================

-- === DEPS ===
local Players           = Players           or game:GetService("Players")
local LocalPlayer       = LocalPlayer       or Players.LocalPlayer

tbl7 = tbl7 or {}
tbl12 = tbl12 or {}

tbl7.PlayerList = tbl7.PlayerList or Players:GetPlayers()

local fn18 = fn18 or function(msg, title, soundId, duration)
    if _G.nLheNotify then
        _G.nLheNotify(title or "nLhe", tostring(msg), "info", duration or 5)
    elseif Library and Library.Notify then
        Library:Notify({
            Title = title or "nLhe",
            Description = tostring(msg),
            Duration = duration or 5,
        })
    else
        warn(("[%s] %s"):format(title or "nLhe", tostring(msg)))
    end
end

-- Если у тебя уже есть getChar/getPlayer — подхватится. Иначе локальный фолбэк.
local function _getChar(player)
    if type(tbl12.Char) == "function" then
        return tbl12.Char(player)
    end
    local char = player.Character
    if not char then return nil, nil, nil end
    return char, char:FindFirstChild("HumanoidRootPart"), char:FindFirstChildOfClass("Humanoid")
end

local function _formatPlayer(player, multi, you)
    if type(tbl12.FormatPlayer) == "function" then
        return tbl12.FormatPlayer(player, multi, you)
    end
    if type(player) ~= "Instance" then
        player = Players:FindFirstChild(tostring(player))
    end
    if not player then return "???" end
    if player == LocalPlayer and you then return "You" end
    if multi then
        return ("%s\n(@%s)"):format(player.DisplayName or player.Name, player.Name)
    end
    return ("%s (@%s)"):format(player.DisplayName or player.Name, player.Name)
end


-- === GROUP ===
do
    local MiscTab = Tabs and Tabs.Misc
    if not MiscTab then
        warn("[Cheaters] Tabs.Misc not found — skipped")
        return
    end

    MiscTab:AddLeftGroupbox("Cheaters", "drama"):AddButton({
        Text = "Find Cheaters",
        Func = function()
            local found = {}

            local list = tbl7.PlayerList and #tbl7.PlayerList > 0 and tbl7.PlayerList or Players:GetPlayers()

            for _, player in ipairs(list) do
                if player ~= LocalPlayer then
                    local char, root, hum = _getChar(player)
                    local hasSticky

                    if hum then
                        local seatPart = hum.SeatPart
                        if seatPart then
                            local seatWeld = seatPart:FindFirstChild("SeatWeld")
                            if not seatWeld or not seatWeld.Enabled then
                                found[player] = "Has Gucci"
                            else
                                if root then
                                    hasSticky = function(part)
                                        if not part or not part.Parent then return end
                                        for _, c in ipairs(part:GetConnectedParts()) do
                                            if c.Name == "StickyPart" then return true end
                                        end
                                    end
                                    local ragdollTouched = root:FindFirstChild("RagdollTouchedHitbox")
                                    local firePlayer     = root:FindFirstChild("FirePlayerPart")
                                    if hasSticky(root) or hasSticky(ragdollTouched) or hasSticky(firePlayer) then
                                        found[player] = "Shuriken in HRP"
                                    end
                                end
                            end
                        elseif root then
                            hasSticky = function(part)
                                if not part or not part.Parent then return end
                                for _, c in ipairs(part:GetConnectedParts()) do
                                    if c.Name == "StickyPart" then return true end
                                end
                            end
                            local ragdollTouched = root:FindFirstChild("RagdollTouchedHitbox")
                            local firePlayer     = root:FindFirstChild("FirePlayerPart")
                            if hasSticky(root) or hasSticky(ragdollTouched) or hasSticky(firePlayer) then
                                found[player] = "Shuriken in HRP"
                            end
                        end
                    end
                end
            end

            if not next(found) then
                return fn18("Cheaters not found!", "Cheaters", nil, 4)
            end

            local str = "Cheaters Found\n\n"
            for plr, reason in pairs(found) do
                str ..= ("[%s]\n%s\n\n"):format(_formatPlayer(plr), reason)
            end
            fn18(str:sub(1, -3), "Cheaters", nil, 10)
        end,
    })
end

-- ============================================================
-- OPEN INVENTORY PLUS — порт из Wourld Hub
-- ============================================================
do
    -- универсальный лоадер (как runExternalLoadstring из Wourld Hub)
    local function runExternalLoadstring(url, name)
        local ok, body = pcall(function() return game:HttpGet(url) end)
        if not ok or type(body) ~= "string" or #body < 12 then
            Library:Notify({
                Title = "Loader",
                Description = tostring(name or "Feature") .. " load failed",
                Duration = 3,
            })
            return false
        end

        local cok, fn = pcall(function() return loadstring(body) end)
        if not cok or type(fn) ~= "function" then
            Library:Notify({
                Title = "Loader",
                Description = tostring(name or "Feature") .. " compile failed",
                Duration = 3,
            })
            return false
        end

        local rok = pcall(fn)
        if rok then
            Library:Notify({
                Title = "Loader",
                Description = tostring(name or "Feature") .. " loaded",
                Duration = 3,
            })
            return true
        end

        Library:Notify({
            Title = "Loader",
            Description = tostring(name or "Feature") .. " runtime error",
            Duration = 3,
        })
        return false
    end

    -- ===== UI =====
    local Box = Tabs.Misc:AddLeftGroupbox("External Tools")

    Box:AddButton({
        Text = "Open Inventory Plus",
        Func = function()
            runExternalLoadstring(
                "https://raw.githubusercontent.com/m1kp0/ftap/refs/heads/main/InventoryPlusV2.lua",
                "Inventory Plus"
            )
        end,
        DoubleClick = false,
    })
end

-- ============================================================
-- APPLY HDR SHADER — порт из Wourld Hub
-- ============================================================
do
    local function runExternalLoadstring(url, name)
        local ok, body = pcall(function() return game:HttpGet(url) end)
        if not ok or type(body) ~= "string" or #body < 12 then
            Library:Notify({
                Title = "Loader",
                Description = tostring(name or "Feature") .. " load failed",
                Duration = 3,
            })
            return false
        end

        local cok, fn = pcall(function() return loadstring(body) end)
        if not cok or type(fn) ~= "function" then
            Library:Notify({
                Title = "Loader",
                Description = tostring(name or "Feature") .. " compile failed",
                Duration = 3,
            })
            return false
        end

        local rok = pcall(fn)
        if rok then
            Library:Notify({
                Title = "Loader",
                Description = tostring(name or "Feature") .. " loaded",
                Duration = 3,
            })
            return true
        end

        Library:Notify({
            Title = "Loader",
            Description = tostring(name or "Feature") .. " runtime error",
            Duration = 3,
        })
        return false
    end

    -- ===== UI =====
    local Box2 = Tabs.Misc:AddRightGroupbox("External Tools")

    Box2:AddButton({
        Text = "Apply HDR Shader",
        Func = function()
            runExternalLoadstring(
                "https://raw.githubusercontent.com/SyntaxScript/HDR-Graphics/main/main.lua",
                "HDR Shader"
            )
        end,
        DoubleClick = false,
    })
end

_G.NS_Enabled        = true
_G.NS_Volume         = 0.5
_G.NS_PitchBase      = 1.0

_G.NS_Brand          = "Project nLhe"
_G.NS_BrandDisplay   = "Project nLhe"

_G.NS_SoundList = {
    ["Electronic ping short"] = "rbxasset://sounds/electronicpingshort.wav",
    ["Ahh~"] = "rbxassetid://83559496188823",
    ["???"] = "rbxassetid://124394921745752",
	["I got this"] = "rbxassetid://140084776912218",
    ["Rust"] = "rbxassetid://138750331387064",
    ["Resonanse"] = "rbxassetid://71450094482101",
}

_G.NS_SelectedSound = "Ping Short"

_G.NS_Pitch = {
    kick    = 0.80,
    join    = 1.08,
    leave   = 0.95,
    packet  = 0.96,
}

_G.NS_Duration = {
    kick    = 4,
    join    = 4,
    leave   = 4,
    packet  = 4,
}

_G.NS_Icon = {
    kick    = nil,
    join    = nil,
    leave   = nil,
    packet  = nil,
}

_NS_DefaultIcon = "rbxassetid://11767037107"

local _NS_SoundService = game:GetService("SoundService")
local _NS_Template

local function _NS_GetCurrentSoundId()
    return _G.NS_SoundList[_G.NS_SelectedSound]
        or "rbxasset://sounds/electronicpingshort.wav"
end

local function _NS_EnsureTemplate()
    if _NS_Template and _NS_Template.Parent then return _NS_Template end
    _NS_Template = Instance.new("Sound")
    _NS_Template.Name         = "nLheNotifyTemplate"
    _NS_Template.SoundId      = _NS_GetCurrentSoundId()
    _NS_Template.Volume       = math.clamp(_G.NS_Volume or 0.5, 0, 1)
    _NS_Template.PlayOnRemove = false
    _NS_Template.Parent       = _NS_SoundService
    return _NS_Template
end

local function _NS_Play(soundType)
    if not _G.NS_Enabled then return end
    soundType = soundType or "info"

    local pitchMult = (_G.NS_Pitch and _G.NS_Pitch[soundType]) or 1.0
    local pitch     = (_G.NS_PitchBase or 1.0) * pitchMult
    local vol       = math.clamp(_G.NS_Volume or 0.5, 0, 1)

    local t = _NS_EnsureTemplate()
    local s = t:Clone()
    s.SoundId       = _NS_GetCurrentSoundId()
    s.PlaybackSpeed = pitch
    s.Volume        = vol
    s.Parent        = _NS_SoundService

    local played = false
    pcall(function()
        _NS_SoundService:PlayLocalSound(s)
        played = true
    end)
    if not played then pcall(function() s:Play() end) end

    task.delay(3, function()
        if s and s.Parent then s:Destroy() end
    end)
end

local function nLheNotify(title, content, kind, duration, icon)
    kind = kind or "info"
    _NS_Play(kind)

    if not title or title == "" then
        title = _G.NS_BrandDisplay or _G.NS_Brand or "Project nLhe"
    end

    local dur = duration or ((_G.NS_Duration and _G.NS_Duration[kind]) or 3)
    local icn = icon     or ((_G.NS_Icon    and _G.NS_Icon[kind])    or _NS_DefaultIcon)

    local ok = pcall(function()
        if icn then
            Library:Notify({ Title = title, Description = content, Duration = dur, Icon = icn })
        else
            Library:Notify({ Title = title, Description = content, Duration = dur })
        end
    end)

    if not ok then
        print(string.format("[%s][%s] %s", kind:upper(), tostring(title), tostring(content)))
    end
end

_G.nLheNotify = nLheNotify
_G.Notify     = nLheNotify

local function _Brand() return _G.NS_BrandDisplay or _G.NS_Brand or "Project nLhe" end

local _NS_Players   = game:GetService("Players")
local _NS_RS        = game:GetService("ReplicatedStorage")
local _NS_Workspace = game:GetService("Workspace")
local _NS_LP        = _NS_Players.LocalPlayer

local _recentlyKicked = {}
local _ANTI_STACK_WINDOW = 6

local function _markKicked(username)
    _recentlyKicked[username] = tick()
end

local function _wasRecentlyKicked(username)
    local t = _recentlyKicked[username]
    if not t then return false end
    if tick() - t <= _ANTI_STACK_WINDOW then return true end
    _recentlyKicked[username] = nil
    return false
end

task.spawn(function()
    while true do
        task.wait(2)
        local now = tick()
        for name, t in pairs(_recentlyKicked) do
            if now - t > _ANTI_STACK_WINDOW then
                _recentlyKicked[name] = nil
            end
        end
    end
end)

local _kickDetEnabled = false
local _kickDetConn    = nil

local _KICK_OBJECT_NAMES = {
    ["blackholekick"]            = true,
    ["blackholekicktweens(old)"] = true,
    ["blackholekicktweens"]      = true,
    ["jhole"]                    = true,
    ["blackhole"]                = true,
    ["black_hole"]               = true,
    ["voidhole"]                 = true,
    ["singularity"]              = true,
}

local function _kickGetClosestPlayer(pos)
    local closest, closestDist = nil, math.huge
    for _, plr in ipairs(_NS_Players:GetPlayers()) do
        if plr ~= _NS_LP and plr.Character then
            local hrp = plr.Character:FindFirstChild("HumanoidRootPart")
            if hrp then
                local d = (hrp.Position - pos).Magnitude
                if d < closestDist then
                    closestDist = d
                    closest     = plr
                end
            end
        end
    end
    return closest
end

local function _kickStart()
    if _kickDetConn then return end
    _kickDetConn = _NS_Workspace.ChildAdded:Connect(function(obj)
        if not _kickDetEnabled then return end

        local name = obj.Name and obj.Name:lower()
        if not name or not _KICK_OBJECT_NAMES[name] then return end

        task.wait(0.1)

        local pos
        if obj:IsA("BasePart") then
            pos = obj.Position
        else
            local part = obj:FindFirstChildWhichIsA("BasePart", true)
            if part then pos = part.Position end
        end
        if not pos then return end

        local closestPlayer = _kickGetClosestPlayer(pos)
        if closestPlayer then
            _markKicked(closestPlayer.Name)
            nLheNotify(_Brand(),
                closestPlayer.DisplayName .. " (@" .. closestPlayer.Name .. ") was kicked!",
                "kick")
        else
            nLheNotify(_Brand(), "Someone was kicked!", "kick")
        end
    end)
end

local function _kickStop()
    if _kickDetConn then
        _kickDetConn:Disconnect()
        _kickDetConn = nil
    end
end

local _jlEnabled = false
local _jlConns   = {}

local function _jlStart()
    if #_jlConns > 0 then return end

    table.insert(_jlConns, _NS_Players.PlayerAdded:Connect(function(plr)
        if not _jlEnabled then return end
        nLheNotify(_Brand(),
            plr.DisplayName .. " (@" .. plr.Name .. ") joined the server",
            "join")
    end))

    table.insert(_jlConns, _NS_Players.PlayerRemoving:Connect(function(plr)
        if not _jlEnabled then return end
        if _wasRecentlyKicked(plr.Name) then return end
        nLheNotify(_Brand(),
            plr.DisplayName .. " (@" .. plr.Name .. ") left the server",
            "leave")
    end))
end

local function _jlStop()
    for _, conn in ipairs(_jlConns) do
        if typeof(conn) == "RBXScriptConnection" then conn:Disconnect() end
    end
    table.clear(_jlConns)
end

local _packetEnabled    = false
local _packetConns      = {}
local _packetLastNotify = 0
local _PACKET_COOLDOWN  = 0.2

local function _packetResolveSender(args)
    for _, v in ipairs(args) do
        if typeof(v) == "Instance" then
            if v:IsA("Player") then return v end
            local model = v:IsA("Model") and v or v:FindFirstAncestorOfClass("Model")
            if model then
                local plr = _NS_Players:GetPlayerFromCharacter(model)
                if plr then return plr end
            end
        end
    end
    return nil
end

local function _packetHandle(eventType, remoteName, ...)
    if not _packetEnabled then return end
    local args = {...}
    local totalBytes = 0
    local maxStringLength = 0

    for _, v in ipairs(args) do
        if typeof(v) == "string" then
            totalBytes = totalBytes + #v
            if #v > maxStringLength then maxStringLength = #v end
        end
    end

    local sender = _packetResolveSender(args)
    if sender == _NS_LP then return end

    local mbSize = totalBytes / (1024 * 1024)
    local isAbnormalSize = mbSize > 0.05 or maxStringLength > 5000
    if not isAbnormalSize and #args <= 6 then return end

    if tick() - _packetLastNotify < _PACKET_COOLDOWN then return end
    _packetLastNotify = tick()

    local senderDisplayName = sender and (sender.DisplayName or sender.Name) or "Unknown"
    local senderName        = sender and sender.Name or "Unknown"

    nLheNotify(_Brand(),
        string.format("%s (@%s) packet detect (%.2f MB)",
            senderDisplayName, senderName, mbSize),
        "packet")
end

local function _packetCheckBlobRemote(child)
    if not _packetEnabled then return end
    if child:IsA("RemoteEvent") and child.Name == "RelayClientAnimation" then
        local parent = child.Parent
        if parent and parent.Name == "BlobmanAnimations" then
            local gpName = parent.Parent and parent.Parent.Name or "Unknown"
            table.insert(_packetConns, child.OnClientEvent:Connect(function(...)
                _packetHandle("Blob", gpName, ...)
            end))
        end
    end
end

local function _packetStart()
    if #_packetConns > 0 then return end

    task.spawn(function()
        local grabEvents = _NS_RS:WaitForChild("GrabEvents", 5)
        if grabEvents then
            local grabRemote = grabEvents:WaitForChild("ExtendGrabLine", 5)
            if grabRemote then
                table.insert(_packetConns, grabRemote.OnClientEvent:Connect(function(...)
                    _packetHandle("Grab", "ExtendGrabLine", ...)
                end))
            end
        end
    end)

    for _, child in ipairs(_NS_Workspace:GetDescendants()) do
        _packetCheckBlobRemote(child)
    end
    table.insert(_packetConns, _NS_Workspace.DescendantAdded:Connect(_packetCheckBlobRemote))
end

local function _packetStop()
    for _, conn in ipairs(_packetConns) do
        if typeof(conn) == "RBXScriptConnection" then conn:Disconnect() end
    end
    table.clear(_packetConns)
end

local _activeDetects = {}

local _detectHandlers = {
    ["Kick Notify"]         = { start = _kickStart,   stop = _kickStop,   flag = function(v) _kickDetEnabled   = v end },
    ["Join / Leave Notify"] = { start = _jlStart,     stop = _jlStop,     flag = function(v) _jlEnabled       = v end },
    ["Packet Lag Notify"]   = { start = _packetStart, stop = _packetStop, flag = function(v) _packetEnabled   = v end },
}

local function _syncDetects(sel)
    for name, handler in pairs(_detectHandlers) do
        local want = sel[name] == true
        local has  = _activeDetects[name] == true
        if want and not has then
            handler.flag(true)
            handler.start()
            _activeDetects[name] = true
        elseif not want and has then
            handler.flag(false)
            handler.stop()
            _activeDetects[name] = nil
        end
    end
end

do
    local NotifyTab = Tabs.Settings:AddRightGroupbox("Notifications", "bell")

    NotifyTab:AddDropdown("NotifyDetects", {
        Text = "Notifications",
        Values = { "Kick Notify", "Join / Leave Notify", "Packet Lag Notify" },
        Default = {},
        Multi = true,
        Callback = function(selected)
            _syncDetects(selected)
        end,
    })

    NotifyTab:AddDivider()

    local soundNames = {}
    for name, _ in pairs(_G.NS_SoundList) do
        table.insert(soundNames, name)
    end
    table.sort(soundNames)

    NotifyTab:AddDropdown("NotifySoundSelect", {
        Text = "Notification Sound",
        Values = soundNames,
        Default = _G.NS_SelectedSound,
        Multi = false,
        Callback = function(name)
            if _G.NS_SoundList[name] then
                _G.NS_SelectedSound = name
                if _NS_Template then
                    _NS_Template.SoundId = _NS_GetCurrentSoundId()
                end
            end
        end,
    })

    NotifyTab:AddSlider("NotifyVolumeSlider", {
        Text = "Notification Volume",
        Default = _G.NS_Volume,
        Min = 0,
        Max = 1,
        Rounding = 2,
        Compact = false,
        Callback = function(v)
            _G.NS_Volume = v
            if _NS_Template then _NS_Template.Volume = v end
        end,
    })

    NotifyTab:AddDivider()

    NotifyTab:AddButton({
        Text = "Test Sound",
        Func = function()
            nLheNotify(_Brand(), "Test notification", "join")
        end,
    })
end

local MenuGroup = Tabs.Settings:AddLeftGroupbox("Menu", "wrench")

MenuGroup:AddCheckbox("KeybindMenuOpen", {
    Text = "Open Keybind Menu",
    Default = Library.KeybindFrame.Visible,
    Callback = function(value)
        Library.KeybindFrame.Visible = value
    end,
})

MenuGroup:AddCheckbox("ShowCustomCursor", {
    Text = "Custom Cursor",
    Default = true,
    Callback = function(Value)
        Library.ShowCustomCursor = Value
    end,
})

MenuGroup:AddDropdown("NotificationSide", {
    Values = { "Left", "Right" },
    Default = "Right",
    Text = "Notification Side",
    Callback = function(Value)
        Library:SetNotifySide(Value)
    end,
})

MenuGroup:AddDropdown("DPIDropdown", {
    Values = { "50%", "75%", "100%", "125%", "150%", "175%", "200%" },
    Default = "100%",
    Text = "DPI Scale",
    Callback = function(Value)
        Value = Value:gsub("%%", "")
        DPI = tonumber(Value)
        Library:SetDPIScale(DPI)
    end,
})

MenuGroup:AddDivider()

MenuGroup:AddLabel("Menu bind"):AddKeyPicker("MenuKeybind", { 
    Default = "RightShift", 
    NoUI = true, 
    Text = "Menu keybind" 
})

MenuGroup:AddButton({
    Text = "Unload",
    Func = function()
        Library:Unload()
    end,
    DoubleClick = false
})

bgData = {
    Enabled = true,
    Image = "0",
    Last = nil,
    Transparency = 0.15
}
end

print([[
    ██╗   ██╗████████╗ ██████╗ ██████╗  █████╗
    ██║   ██║╚══██╔══╝██╔═══██╗██╔══██╗██╔══██╗
    ██║   ██║   ██║   ██║   ██║██████╔╝███████║
    ██║   ██║   ██║   ██║   ██║██╔═══╝ ██╔══██║
    ╚██████╔╝   ██║   ╚██████╔╝██║     ██║  ██║
     ╚═════╝    ╚═╝    ╚═════╝ ╚═╝     ╚═╝  ╚═╝
    ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
     version 1.0.1
]])
