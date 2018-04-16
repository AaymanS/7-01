----------------------------------------------------------------------------------------------------
-- Created by: Aayman Shameem
-- Created on: Apr 16, 2018
--
-- This code will show what happens when two sprites are touched with two different kinds of touches
----------------------------------------------------------------------------------------------------

-- Monstercat 
local monsterCat = display.newImageRect( "./assets/sprites/Monstercat.png", 675, 350 )
monsterCat.x = display.contentCenterX - 520
monsterCat.y = display.contentCenterY + 458
monsterCat.id = "Monstercat"

-- Unknown object 
local nightmareThing = display.newImageRect( "./assets/sprites/FNAFtotempole.png", 675, 918 )
nightmareThing.x = display.contentCenterX + 520
nightmareThing.y = display.contentCenterY + 177
nightmareThing.id = "Unknown object"

-- the button of talking
local function catButton( event )

	local y = 0

	local catTalking = display.newText( "WHAT IS THAT THING?!?!", display.contentCenterX - 520, display.contentCenterY + 300, native.systemFont, 50 )
end

monsterCat:addEventListener( "touch", catButton)

function nightmareThing:touch( event )

	local thingTalking = display.newText( "*EEERRRRGGGGHHHHHHH*", display.contentCenterX + 520, display.contentCenterY - 277, native.systemFont, 50 )

	-- Set touch focus
    display.getCurrentStage():setFocus( self )
    self.isFocus = true

    -- Reset touch focus
    display.getCurrentStage():setFocus( nil )
    self.isFocus = nil

end

nightmareThing:addEventListener( "touch", nightmareThing )
