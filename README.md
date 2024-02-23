# TurtleWax for IKEMEN by Kamekaze and Jesuszilla
This system aims to provide a complete command parser and buffering system for the IKEMEN-Go engine. A minimal
installation requires `turtlewax.zss` to be placed in the `CommonStates` section of `config.json`, with each
character specifying their own `buffering.zss` file to determine state setting logic.

## Available Maps
The following maps are made available to the user. All times are in frames:
<table>
    <tr>
        <th>Map Name</th>
        <th>Description</th>
        <th>Default</th>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_ver)</td>
        <td style="text-align: left;">
            TurtleWax version
        </td>
        <td style="text-align: center;">(current version)</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_debug)</td>
        <td style="text-align: left;">
            Set to nonzero to enable debug print statements.
        </td>
        <td style="text-align: center;">0</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_MashPCt)</td>
        <td style="text-align: left;">
            Total buffer time for HHS presses.
        </td>
        <td style="text-align: center;">10</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_MashCt)</td>
        <td style="text-align: left;">
            Number of button presses required for a "mashing" command to activate
        </td>
        <td style="text-align: center;">5</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_ChargePartition)</td>
        <td style="text-align: left;">
            Set to 1 to enable charge partitioning.
        </td>
        <td style="text-align: center;">0 (off)</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_ChargePartitionTime)</td>
        <td style="text-align: left;">
            Time a charge partition should last.
        </td>
        <td style="text-align: center;">15</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_D_ChargeTime)</td>
        <td style="text-align: left;">
            Total charge time to hold for a Down charge. 
        </td>
        <td style="text-align: center;">48</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_D_BufferTime)</td>
        <td style="text-align: left;">
            Total buffer time for Down charge once it's active.
        </td>
        <td style="text-align: center;">9</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_U_ChargeTime)</td>
        <td style="text-align: left;">
            Total charge time to hold for an Up charge. 
        </td>
        <td style="text-align: center;">48</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_U_BufferTime)</td>
        <td style="text-align: left;">
            Total buffer time for Up charge once it's active.
        </td>
        <td style="text-align: center;">9</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_B_ChargeTime)</td>
        <td style="text-align: left;">
            Total charge time to hold for a Back charge. 
        </td>
        <td style="text-align: center;">48</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_B_BufferTime)</td>
        <td style="text-align: left;">
            Total buffer time for Back charge once it's active.
        </td>
        <td style="text-align: center;">9</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_F_ChargeTime)</td>
        <td style="text-align: left;">
            Total charge time to hold for a Forward charge. 
        </td>
        <td style="text-align: center;">48</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_F_BufferTime)</td>
        <td style="text-align: left;">
            Total buffer time for Forward charge once it's active.
        </td>
        <td style="text-align: center;">9</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_Dash_input1_BufferTime)</td>
        <td style="text-align: left;">
            Total buffer time for the first input in any dash (FF,BB) command.
        </td>
        <td style="text-align: center;">9</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_Dash_input2_BufferTime)</td>
        <td style="text-align: left;">
            Total buffer time for the second input in any dash (FF,BB) command.
        </td>
        <td style="text-align: center;">6</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_Input_Delay_frames)</td>
        <td style="text-align: left;">
            Total number of frames to additionally delay all inputs.
        </td>
        <td style="text-align: center;">0 (no delay)</td>
    </tr>
    <tr>
        <td style="text-align: center;">Map(tw_Buffer_Snk)</td>
        <td style="text-align: left;">
            Set to 1 to treat the character's buffer as an SNK (KOF) style buffer.
        </td>
        <td style="text-align: center;">0 (off)</td>
    </tr>
    <tr>
		<td style="text-align: center;">Map(tw_Buffer_ChangeStateNo)</td>
		<td style="text-align: left;">
			Set in your buffering.zss file to set move state. Keep at -1 for no change.
		</td>
		<td style="text-align: center;">(dynamic)</td>
	</tr>
	<tr>
		<td style="text-align: center;">Map(tw_MoveStrength)</td>
		<td style="text-align: left;">
			Set in your buffering.zss file to set move strength.
		</td>
		<td style="text-align: center;">(dynamic)</td>
	</tr>
	<tr>
		<td style="text-align: center;">Map(tw_Btn6)</td>
		<td style="text-align: left;">
			Set to 1 to signify that this is a 6-button character.
		</td>
		<td style="text-align: center;">1 (is 6-button)</td>
	</tr>
    <tr>
		<td style="text-align: center;">Map(tw_Assert_NoBufferTimeDec)</td>
		<td style="text-align: left;">
			Set to nonzero to assert no buffer decrementing. The buffer can still move along, but
            this can allow for things such as "infinite" buffer time such as SFA2/SFZ2 CC/VC.
		</td>
		<td style="text-align: center;">0 (only set as-needed)</td>
	</tr>
    <tr>
		<td style="text-align: center;">Map(tw_B_ChargeReady)</td>
		<td style="text-align: left;">
			Indicates that a back charge is ready.
		</td>
		<td style="text-align: center;">0 (set by system)</td>
    </tr>
    <tr>
		<td style="text-align: center;">Map(tw_D_ChargeReady)</td>
		<td style="text-align: left;">
			Indicates that a down charge is ready.
		</td>
		<td style="text-align: center;">0 (set by system)</td>
    </tr>
    <tr>
		<td style="text-align: center;">Map(tw_F_ChargeReady)</td>
		<td style="text-align: left;">
			Indicates that a forward charge is ready.
		</td>
		<td style="text-align: center;">0 (set by system)</td>
    </tr>
    <tr>
		<td style="text-align: center;">Map(tw_U_ChargeReady)</td>
		<td style="text-align: left;">
			Indicates that an up charge is ready.
		</td>
		<td style="text-align: center;">0 (set by system)</td>
    </tr>
</table>

## Usage (2.0)
To properly make use of the command stateNo setting system, you must handle the ChangeState logic by setting
and reading the `Map(tw_Buffer_ChangeStateNo)` variable. Once you change to the state that the buffering
system sets, it will automatically reset it in +1 if you set it up like the examples have it. An example CNS
implementation may look like the example below in your StateDef -1 `.cmd` (legacy) or `.cds` (recommended
extension) file.

You must also add `turtlewax.zss` and optionally (if you want the default command maps) `turtlewax_common.zss` to
`CommonStates` in `config.json`. Change your `CommonCmd` to also use `common.cds` instead of `common.cmd`.

You will need to create a buffering.zss file for your character(s). You may reference
[TW Cvs Raiden](https://github.com/Jesuszilla/TW_Cvs_raiden) for an example implementation. When building your buffering.zss, most likely, you will have some
commands that are alike such as `QCF`, `HCF`, and `QCFx2` for instance (they all contain `D,DF,F` or `236` as a substring).
Because doing Lua operations every frame is expensive and there are currently no arrays in ZSS, **you, the character
author, are now responsible for resetting these.** Again, refer to Raiden's buffering.zss for more information on
resetting alike commands. You should ideally only reset alike commands with 3 or more elements. A lot of Capcom and to an
extent SNK games do this. Observe your game for proper behavior. CvS2 for sure does this, though.

TurtleWax 2.0 uses Capcom vs. SNK 2 3-star defaults for the Capcom commands.

TurtleWax 2.0 is officially Raspberry Pi 4 performant!

	;---------------------------------------------------------------------------
	; Supers
	[State -1, Supers]
	type = ChangeState
	value = Map(tw_Buffer_ChangeStateNo)
	triggerall = Map(tw_Buffer_ChangeStateNo) = [3000,3999]
	triggerall = Power >= 1000
	triggerall = statetype != A
	triggerall = roundstate = 2
	trigger1  = ctrl || (StateNo = 100 && AnimElemTime(2) >1) || StateNo = 101 || StateNo = 40 || (StateNo = 52 && Anim = 47 && Time >= 2)
	trigger2  = StateNo = 200
	trigger3  = StateNo = 210 && AnimElemTime(6) < 0
	trigger4  = StateNo = 215 && AnimElemTime(7) < 0
	trigger4  = StateNo = 220 && Time < 4
	trigger5  = StateNo = 225 && AnimElemTime(6) < 0
	trigger6  = StateNo = 230 && AnimElemTime(5) < 0
	trigger7  = StateNo = 240 && Time < 4
	trigger8  = StateNo = 250 && Time < 4
	trigger9  = StateNo = 255 && Time < 4
	trigger10 = StateNo = 400
	trigger11 = StateNo = 410 && AnimElemTime(6) < 0
	trigger12 = StateNo = 430 && AnimElemTime(5) < 0
	trigger13 = StateNo = 440 && Time < 4
	trigger14 = StateNo = 450 && AnimElemTime(5) < 0
	trigger15 = StateNo = 1260 && MoveContact = 1
	ignorehitpause = 0

	;---------------------------------------------------------------------------
	; Specials
	[State -1, Specials]
	type = ChangeState
	value = Map(tw_Buffer_ChangeStateNo)
	triggerall = !AILevel
	triggerall = !IsHelper
	triggerall = roundstate = 2
	triggerall = Map(tw_Buffer_ChangeStateNo) = 195 || (Map(tw_Buffer_ChangeStateNo) = [1000,2999])
	triggerall = statetype != A
	trigger1  = ctrl || (StateNo = 100 && AnimElemTime(2) >1) || StateNo = 101 || StateNo = 40 || (StateNo = 52 && Anim = 47 && Time >= 2)
	trigger2  = StateNo = 200
	trigger3  = StateNo = 210 && AnimElemTime(6) < 0
	trigger4  = StateNo = 215 && Time < 4
	trigger4  = StateNo = 220 && Time < 4
	trigger5  = StateNo = 225 && AnimElemTime(6) < 0
	trigger6  = StateNo = 230 && AnimElemTime(5) < 0
	trigger7  = StateNo = 240 && Time < 4
	trigger8  = StateNo = 250 && Time < 4
	trigger9  = StateNo = 255 && Time < 4
	trigger10 = StateNo = 400
	trigger11 = StateNo = 410 && AnimElemTime(6) < 0
	trigger12 = StateNo = 430 && AnimElemTime(5) < 0
	trigger13 = StateNo = 440 && Time < 4
	trigger14 = StateNo = 450 && Time < 4

	;---------------------------------------------------------------------------
	; Throw 1
	[State -1, Throw 1]
	type = ChangeState
	value = 800
	triggerall = !AILevel
	triggerall = (Map(h_Fd) || Map(h_Bk))
	triggerall = Map(xa)
	triggerall = ctrl
	triggerall = stateno != 100
	trigger1 = statetype = S
	ignorehitpause = 0

    ;---------------------------------------------------------------------------
    ; State Correction
    ; This is to prevent bad things from happening when the state is set to an
    ; air state immediately upon landing. You can either force it to a ground
    ; basic or just null it out completely by setting it to -1.
    [State -1, MapSet]
    type = MapSet
    trigger1 = StateType != A && (Map(tw_Buffer_ChangeStateNo) = [600,699])
    map = "tw_Buffer_ChangeStateNo"
    value = Map(tw_Buffer_ChangeStateNo)-cond(Map(h_Dn),200,400)    ; or -1, depending on your use case
    ignorehitpause = 1

    ;---------------------------------------------------------------------------
    ; State Correction
    ; This is to prevent basics from coming out after throws.
    [State -1, MapSet]
    type = MapSet
    trigger1 = stateNo = [800,899]
    trigger1 = Time < 3 && (map(tw_Buffer_ChangeStateNo) = [200,799])
    trigger2 = stateno = 195
    trigger2 = !ctrl && map(tw_Buffer_ChangeStateNo) = 195
    map = "tw_Buffer_ChangeStateNo"
    value = -1
    ignorehitpause = 1

	;---------------------------------------------------------------------------
	; Basics
	[State -1, Basics]
	type = ChangeState
	value = Map(tw_Buffer_ChangeStateNo)
	triggerall = !AILevel
	triggerall = !IsHelper
	triggerall = roundstate = 2
	triggerall = StateNo != [800,899]
    triggerall = MoveType != H
	trigger1 = Map(tw_Buffer_ChangeStateNo) = [200,299]
	trigger2 = Map(tw_Buffer_ChangeStateNo) = [400,499]
	trigger3 = Map(tw_Buffer_ChangeStateNo) = [600,699]
	ignorehitpause = 0

## Debugging
You can reload your characters' `buffering.zss` files the same as you always would (`Shift+F4`). This can be really helpful for debugging.

## History
### Version 2.0
* Changed to ZSS implementation.
* Motion map names have been moved to `turtlewax_common.zss` and now prefixed with `tw_`. Base directions and buttons are unchanged.
* Now Raspberry Pi 4 compliant.

### Version 1.6
* Fixed default charge commands.
* Code optimization

### Version 1.5
* Added input_types array to all move definitions so that the input type can be defined for each motion.
* tt can now be specified as a single value, or a table of values. Each value in the table must either be
  an integer value or a function that takes an integer, p (player index) as its sole argument and returns
  an integer value.
* tt can now hold up to 31 frames of buffering time.
* Refactored arrays so that all button inputs are in one array.
* Added input delay.
* Added standard Up charging implementation and maps to control the buffer and charge times for it.
* Added maps to control the buffering times for dash commands.
* Added StateNo setting system defined by a new file, buffering.lua, required as part of the implementation.
  Every character should have a buffering.lua file with the command-state mappings defined. Please read
  buffering.lua.example for more info.
* Added move strength setting and map for retrieval, Map(tw_MoveStrength). This is set by the "strength" parameter
  in the move table definition in buffering.lua.

### Version 1.0
Initial release

### Special Thanks
* Kamekaze - Ported a lot of the original Deep Buffering code to Lua and re-porting version 1.6 fixes to ZSS, testing, implementation.
* Jesuszilla - Original author of Deep Buffering, testing, advice & implementation.
* TTTTTsd - Testing
* Vans - Original Tiny Buffering system which formed the basis for all good buffering systems in M.U.G.E.N and its derivatives.
* extravagant - Testing
* Phantom.of.the.Server - Testing
