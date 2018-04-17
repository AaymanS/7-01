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
local function monsterCatTouch( event )
    if ( event.phase == "began" ) then
        print( "Touch event began on: " .. event.target.id )
    elseif ( event.phase == "ended" ) then
        print( "Touch event ended on: " .. event.target.id )
    end
    	
    return true
	
end

	monsterCat:addEventListener( "touch", monsterCatTouch)




 
function nightmareThing:touch( event )
    if ( event.phase == "began" ) then
        print( "Touch event began on: " .. self.id )
 
        -- Set touch focus
        display.getCurrentStage():setFocus( self )
        self.isFocus = true
     
    elseif ( self.isFocus ) then
        if ( event.phase == "moved" ) then
            print( "Moved phase of touch event detected." )
 
        elseif ( event.phase == "ended" or event.phase == "cancelled" ) then
 
            -- Reset touch focus
            display.getCurrentStage():setFocus( nil )
            self.isFocus = nil
        end
    end
    return true
end

nightmareThing:addEventListener( "touch", nightmareThing )
