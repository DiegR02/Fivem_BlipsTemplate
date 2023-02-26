# Fivem_BlipsTemplate
A FiveM Blip generator template

    local blips = {
      --[[
      title -> Show the name of the blip in the map.
      colour -> Choose the colour of the blip.
      id -> Choose the blip for the map(https://docs.fivem.net/docs/game-references/blips/).
      scale -> Chooose the size of the blip.
      x, y, z -> Choose the coordinates of the blip.
      ]]
      {title="Hospital", colour=75, id=61, scale= 1.0, x = -256.82, y = 6334.4, z = 32.8},
    }
      

    Citizen.CreateThread(function()

        for _, info in pairs(blips) do
        info.blip = AddBlipForCoord(info.x, info.y, info.z)
        SetBlipSprite(info.blip, info.id)
        SetBlipDisplay(info.blip, 4)
        SetBlipScale(info.blip, info.scale)
        SetBlipColour(info.blip, info.colour)
        -- SetBlipAsShortRange() if true -> set the market short-range
        -- SetBlipAsShortRange() if false -> set the market long-range
        SetBlipAsShortRange(info.blip, true)
	      BeginTextCommandSetBlipName("STRING")
        AddTextComponentString(info.title)
        EndTextCommandSetBlipName(info.blip)
        end
    end)
