--[[NCDev Team Evolution]]
local d = string.byte
local B = string.char
local c = string.sub
local h = table.concat
local l = table.insert
local r = math.ldexp
local D = getfenv or function()
        return _ENV
    end
local u = setmetatable
local s = select
local t = unpack or table.unpack
local f = tonumber
local function A(i)
    local e, n, a = "", "", {}
    local o = 256
    local t = {}
    for l = 0, o - 1 do
        t[l] = B(l)
    end
    local l = 1
    local function d()
        local e = f(c(i, l, l), 36)
        l = l + 1
        local n = f(c(i, l, l + e - 1), 36)
        l = l + e
        return n
    end
    e = B(d())
    a[1] = e
    while l < #i do
        local l = d()
        if t[l] then
            n = t[l]
        else
            n = e .. c(e, 1, 1)
        end
        t[o] = e .. c(n, 1, 1)
        a[#a + 1], e, o = n, n, o + 1
    end
    return table.concat(a)
end
local f =
    A(
    "26P27327527126X27527323W24C23X24623Z23V27126Z27924824E24224A27126T27925424A23V24S24A23X23T24624C27N26W27924V24324E23Q27V23W27126S27924Z24024C24E24328328527V27126U27925824724E23X24E24C23V28J27827524V24023S28727127027Q23U24228K27923W24A23R24E24124824A28428927924T24A24224028T25623T24A24127G27427529I29K28T25523U24128S24624024127126R27925224123T24024424A27U27W28J26V27Q27S24Y24023U29827126Y29723Z24E23S24127326E27926L26L2792712792672792792922AY2732B027I2B32AZ2B72732B22BA2AO2BE2B32782BH2792812BK2752AG2B62752722AW2B32BS27526726G2BA27P26726C2BA28A2BN2732A52BA2B02B02BQ27328L2752CB2B02BW2BA27327I2C52BG2BR27926Q2BU2BC2CA27627329S27326X2662732922CN2BV28V2732BV2752AV2C92D427526B2792D52D52AO2762B927327K27M27O2AH27T27V27X27Z2DL29T29Y2AD2DP27N2CP29T29P24B27V24S28T23Z23Z24A24B2712812752582A224124A28S27327P2CE2D02D92CH2C82732B62B02EJ2EM2B02C52CK2CI2AO2CX2BC2D12752CD2CI2632BB2BV2DB2CN2F72EK2B72DF27323Z28E2432432732FB26L2612DC2792EX2DD2EK2F12BA2AV2CT2F52FL2F826J2FV2B31F25C29627529829A29C29E24E2D52B325B2G227325429428X28Z23X25O2G92BO2GB2D525R2GK27326N2GB2EJ25324623V2GP26J2GB2D324R28P29D27G2DH2DJ27N2EH2GD27S2DU27Y28028228428623X28828A27528C2FE28H2HG2GC28N28P28R28T23X27728228Y2902EJ2GE2952HJ27329U29L24A29N29P27G2H825524623X2AC2DO28U27929Y2AQ24C24427326D2B32DX2792AO2B62BS2CG2GQ2CQ2BS25R2B329227I2IY2IQ2CW2CQ2B32BE2BS2BS2AG26N2B32812G92GK2J72D927P2JB27928L2BS2IS2732I22JG2BS2A52B62922IP2FL2922ES2EZ2742JQ27326O2BD2EZ2JB2K126M2K42D92JM2K92J827326K2EN2752922FX2BA2DH2BA2J02CI2FO2BA2GP273"
)
local o = bit and bit.bxor or function(l, e)
        local n, o = 1, 0
        while l > 0 and e > 0 do
            local a, c = l % 2, e % 2
            if a ~= c then
                o = o + n
            end
            l, e, n = (l - a) / 2, (e - c) / 2, n * 2
        end
        if l < e then
            l = e
        end
        while l > 0 do
            local e = l % 2
            if e > 0 then
                o = o + n
            end
            l, n = (l - e) / 2, n * 2
        end
        return o
    end
local function n(e, l, n)
    if n then
        local l = (e / 2 ^ (l - 1)) % 2 ^ ((n - 1) - (l - 1) + 1)
        return l - l % 1
    else
        local l = 2 ^ (l - 1)
        return (e % (l + l) >= l) and 1 or 0
    end
end
local l = 1
local function e()
    local a, e, c, n = d(f, l, l + 3)
    a = o(a, 255)
    e = o(e, 255)
    c = o(c, 255)
    n = o(n, 255)
    l = l + 4
    return (n * 16777216) + (c * 65536) + (e * 256) + a
end
local function i()
    local e = o(d(f, l, l), 255)
    l = l + 1
    return e
end
local function a()
    local e, n = d(f, l, l + 2)
    e = o(e, 255)
    n = o(n, 255)
    l = l + 2
    return (n * 256) + e
end
local function C()
    local l = e()
    local e = e()
    local c = 1
    local o = (n(e, 1, 20) * (2 ^ 32)) + l
    local l = n(e, 21, 31)
    local e = ((-1) ^ n(e, 32))
    if (l == 0) then
        if (o == 0) then
            return e * 0
        else
            l = 1
            c = 0
        end
    elseif (l == 2047) then
        return (o == 0) and (e * (1 / 0)) or (e * (0 / 0))
    end
    return r(e, l - 1023) * (c + (o / (2 ^ 52)))
end
local A = e
local function r(e)
    local n
    if (not e) then
        e = A()
        if (e == 0) then
            return ""
        end
    end
    n = c(f, l, l + e - 1)
    l = l + e
    local e = {}
    for l = 1, #n do
        e[l] = B(o(d(c(n, l, l)), 255))
    end
    return h(e)
end
local l = e
local function E(...)
    return {...}, s("#", ...)
end
local function A()
    local B = {}
    local f = {}
    local l = {}
    local d = {B, f, nil, l}
    local l = e()
    local c = {}
    for n = 1, l do
        local e = i()
        local l
        if (e == 0) then
            l = (i() ~= 0)
        elseif (e == 1) then
            l = C()
        elseif (e == 2) then
            l = r()
        end
        c[n] = l
    end
    d[3] = i()
    for d = 1, e() do
        local l = i()
        if (n(l, 1, 1) == 0) then
            local o = n(l, 2, 3)
            local t = n(l, 4, 6)
            local l = {a(), a(), nil, nil}
            if (o == 0) then
                l[3] = a()
                l[4] = a()
            elseif (o == 1) then
                l[3] = e()
            elseif (o == 2) then
                l[3] = e() - (2 ^ 16)
            elseif (o == 3) then
                l[3] = e() - (2 ^ 16)
                l[4] = a()
            end
            if (n(t, 1, 1) == 1) then
                l[2] = c[l[2]]
            end
            if (n(t, 2, 2) == 1) then
                l[3] = c[l[3]]
            end
            if (n(t, 3, 3) == 1) then
                l[4] = c[l[4]]
            end
            B[d] = l
        end
    end
    for l = 1, e() do
        f[l - 1] = A()
    end
    return d
end
local function h(l, d, a)
    local n = l[1]
    local e = l[2]
    local l = l[3]
    return function(...)
        local o = n
        local C = e
        local c = l
        local r = E
        local n = 1
        local i = -1
        local D = {}
        local A = {...}
        local f = s("#", ...) - 1
        local B = {}
        local e = {}
        for l = 0, f do
            if (l >= c) then
                D[l - c] = A[l + 1]
            else
                e[l] = A[l + 1]
            end
        end
        local l = f - c + 1
        local l
        local c
        while true do
            l = o[n]
            c = l[1]
            if c <= 19 then
                if c <= 9 then
                    if c <= 4 then
                        if c <= 1 then
                            if c == 0 then
                                local l = l[2]
                                e[l](t(e, l + 1, i))
                            else
                                a[l[3]] = e[l[2]]
                            end
                        elseif c <= 2 then
                            local n = l[2]
                            local o = e[l[3]]
                            e[n + 1] = o
                            e[n] = o[l[4]]
                        elseif c == 3 then
                            local i
                            local c
                            e[l[2]] = a[l[3]]
                            n = n + 1
                            l = o[n]
                            c = l[2]
                            i = e[l[3]]
                            e[c + 1] = i
                            e[c] = i[l[4]]
                            n = n + 1
                            l = o[n]
                            e[l[2]] = l[3]
                            n = n + 1
                            l = o[n]
                            c = l[2]
                            e[c] = e[c](t(e, c + 1, l[3]))
                            n = n + 1
                            l = o[n]
                            e[l[2]] = e[l[3]][l[4]]
                            n = n + 1
                            l = o[n]
                            c = l[2]
                            i = e[l[3]]
                            e[c + 1] = i
                            e[c] = i[l[4]]
                        else
                            local n = l[2]
                            e[n] = e[n](t(e, n + 1, l[3]))
                        end
                    elseif c <= 6 then
                        if c > 5 then
                            e[l[2]] = e[l[3]]
                        else
                            e[l[2]] = e[l[3]][l[4]]
                        end
                    elseif c <= 7 then
                        a[l[3]] = e[l[2]]
                    elseif c > 8 then
                        e[l[2]] = d[l[3]]
                    else
                        local i = C[l[3]]
                        local t
                        local c = {}
                        t =
                            u(
                            {},
                            {__index = function(e, l)
                                    local l = c[l]
                                    return l[1][l[2]]
                                end, __newindex = function(n, l, e)
                                    local l = c[l]
                                    l[1][l[2]] = e
                                end}
                        )
                        for a = 1, l[4] do
                            n = n + 1
                            local l = o[n]
                            if l[1] == 6 then
                                c[a - 1] = {e, l[3]}
                            else
                                c[a - 1] = {d, l[3]}
                            end
                            B[#B + 1] = c
                        end
                        e[l[2]] = h(i, t, a)
                    end
                elseif c <= 14 then
                    if c <= 11 then
                        if c == 10 then
                            local l = l[2]
                            e[l] = e[l](e[l + 1])
                        else
                            e[l[2]][l[3]] = e[l[4]]
                        end
                    elseif c <= 12 then
                        local l = l[2]
                        e[l] = e[l](e[l + 1])
                    elseif c == 13 then
                        local B
                        local h, s
                        local f
                        local c
                        e[l[2]] = {}
                        n = n + 1
                        l = o[n]
                        e[l[2]] = a[l[3]]
                        n = n + 1
                        l = o[n]
                        e[l[2]][l[3]] = e[l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]][l[3]] = l[4]
                        n = n + 1
                        l = o[n]
                        e[l[2]][l[3]] = l[4]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = d[l[3]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]][l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]][l[3]] = e[l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = d[l[3]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]][l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]][l[3]] = e[l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = a[l[3]]
                        n = n + 1
                        l = o[n]
                        c = l[2]
                        f = e[l[3]]
                        e[c + 1] = f
                        e[c] = f[l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = l[3]
                        n = n + 1
                        l = o[n]
                        c = l[2]
                        e[c] = e[c](t(e, c + 1, l[3]))
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]][l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]][l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]][l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]][l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]][l[4]]
                        n = n + 1
                        l = o[n]
                        c = l[2]
                        f = e[l[3]]
                        e[c + 1] = f
                        e[c] = f[l[4]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = a[l[3]]
                        n = n + 1
                        l = o[n]
                        e[l[2]] = e[l[3]]
                        n = n + 1
                        l = o[n]
                        c = l[2]
                        h, s = r(e[c](e[c + 1]))
                        i = s + c - 1
                        B = 0
                        for l = c, i do
                            B = B + 1
                            e[l] = h[B]
                        end
                        n = n + 1
                        l = o[n]
                        c = l[2]
                        e[c](t(e, c + 1, i))
                        n = n + 1
                        l = o[n]
                        do
                            return
                        end
                    else
                        local l = l[2]
                        e[l](e[l + 1])
                    end
                elseif c <= 16 then
                    if c > 15 then
                        e[l[2]] = l[3]
                    else
                        local n = l[2]
                        local o = e[l[3]]
                        e[n + 1] = o
                        e[n] = o[l[4]]
                    end
                elseif c <= 17 then
                    e[l[2]] = e[l[3]]
                elseif c > 18 then
                    local l = l[2]
                    e[l](t(e, l + 1, i))
                else
                    local i
                    local c
                    e[l[2]] = a[l[3]]
                    n = n + 1
                    l = o[n]
                    c = l[2]
                    i = e[l[3]]
                    e[c + 1] = i
                    e[c] = i[l[4]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = l[3]
                    n = n + 1
                    l = o[n]
                    c = l[2]
                    e[c] = e[c](t(e, c + 1, l[3]))
                    n = n + 1
                    l = o[n]
                    e[l[2]] = e[l[3]][l[4]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = e[l[3]][l[4]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = e[l[3]][l[4]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = e[l[3]][l[4]]
                    n = n + 1
                    l = o[n]
                    a[l[3]] = e[l[2]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = a[l[3]]
                end
            elseif c <= 29 then
                if c <= 24 then
                    if c <= 21 then
                        if c > 20 then
                            e[l[2]][l[3]] = e[l[4]]
                        else
                            local n = l[2]
                            e[n] = e[n](t(e, n + 1, l[3]))
                        end
                    elseif c <= 22 then
                        e[l[2]] = {}
                    elseif c > 23 then
                        local l = l[2]
                        local o, n = r(e[l](e[l + 1]))
                        i = n + l - 1
                        local n = 0
                        for l = l, i do
                            n = n + 1
                            e[l] = o[n]
                        end
                    else
                        e[l[2]] = e[l[3]][l[4]]
                    end
                elseif c <= 26 then
                    if c == 25 then
                        local l = l[2]
                        e[l](e[l + 1])
                    else
                        e[l[2]][l[3]] = l[4]
                    end
                elseif c <= 27 then
                    local t
                    local c
                    e[l[2]] = e[l[3]][l[4]]
                    n = n + 1
                    l = o[n]
                    c = l[2]
                    t = e[l[3]]
                    e[c + 1] = t
                    e[c] = t[l[4]]
                    n = n + 1
                    l = o[n]
                    c = l[2]
                    e[c] = e[c](e[c + 1])
                    n = n + 1
                    l = o[n]
                    a[l[3]] = e[l[2]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = a[l[3]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = e[l[3]][l[4]]
                    n = n + 1
                    l = o[n]
                    e[l[2]] = e[l[3]][l[4]]
                    n = n + 1
                    l = o[n]
                    c = l[2]
                    t = e[l[3]]
                    e[c + 1] = t
                    e[c] = t[l[4]]
                    n = n + 1
                    l = o[n]
                    c = l[2]
                    e[c] = e[c](e[c + 1])
                    n = n + 1
                    l = o[n]
                    e[l[2]] = a[l[3]]
                elseif c > 28 then
                    e[l[2]] = a[l[3]]
                else
                    do
                        return
                    end
                end
            elseif c <= 34 then
                if c <= 31 then
                    if c > 30 then
                        local n = l[2]
                        e[n](t(e, n + 1, l[3]))
                    else
                        e[l[2]] = d[l[3]]
                    end
                elseif c <= 32 then
                    local l = l[2]
                    local o, n = r(e[l](e[l + 1]))
                    i = n + l - 1
                    local n = 0
                    for l = l, i do
                        n = n + 1
                        e[l] = o[n]
                    end
                elseif c == 33 then
                    local i = C[l[3]]
                    local t
                    local c = {}
                    t =
                        u(
                        {},
                        {__index = function(e, l)
                                local l = c[l]
                                return l[1][l[2]]
                            end, __newindex = function(n, l, e)
                                local l = c[l]
                                l[1][l[2]] = e
                            end}
                    )
                    for a = 1, l[4] do
                        n = n + 1
                        local l = o[n]
                        if l[1] == 6 then
                            c[a - 1] = {e, l[3]}
                        else
                            c[a - 1] = {d, l[3]}
                        end
                        B[#B + 1] = c
                    end
                    e[l[2]] = h(i, t, a)
                else
                    e[l[2]] = l[3]
                end
            elseif c <= 36 then
                if c > 35 then
                    local n = l[2]
                    e[n](t(e, n + 1, l[3]))
                else
                    e[l[2]] = {}
                end
            elseif c <= 37 then
                do
                    return
                end
            elseif c > 38 then
                e[l[2]][l[3]] = l[4]
            else
                e[l[2]] = a[l[3]]
            end
            n = n + 1
        end
    end
end
return h(A(), {}, D())()
