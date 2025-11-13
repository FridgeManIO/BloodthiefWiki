# Entity Reference
This will be quite overwhelming to read end-to-end. I recommend using this like a wiki or a reference manual and revisit it when you have a specific need or idea. Also use the section links to quickly jump to the documentation for a specific entity.

## Point Entities
Point entities are what they sound like: Entities that are placed at a single point in the map.

### Enemies
All enemies pretty much share the same properties, so they will be lumped together in this section.

!!!info "Key Properties"
    * hidden
        * 0: The enemy will not be hidden when the game starts.
        * 1: The enemy will be hidden and out of play when the game starts. Triggering the enemy will cause them to “unhide”
    * has_spawn_effect
        * 0: When the enemy “unhides”, there will be no spawn effect
        * 1: There will be a spawn effect when the enemy unhides
    * target
        * This property designates the entity that should be triggered when this enemy dies. So for example, if you want door1 to open when this enemy dies, you would specify door1 for the target.
    * target_func
        * The function on the target that should be called when this entity dies. For example, if our target is a door, this can be set to reverse_motion to close a door when this entity dies
    * targetname:
        * Use this to make the entity triggerable. This enemy will unhide when triggered. For example you can make an enemy hidden, and then give it targetname of e1. Then when e1 is triggered, the enemy will unhide
    * bubble_shield_id
        * Give this any value to give this enemy a bubble shield. In Bloodthief shields are typically tethered to a vt_mage and are disabled when the mage dies. If the tethered mage is shielding two different enemies, both enemies should have the same bubble_shield_id.
    * shield_type
        * Only specify this property if bubble_shield_id is set.
    * NO_AIR_DASH
        * Applies a purple shield. Air dashes will be blocked while this enemy is shielded
    * DAMAGE_ON_TOUCH
        * Applies a red shield. The player can’t touch this shield or they will be damaged


* #### vt_generic_knight
* #### vt_bow_knight
* #### vt_armored_bow_knight
* #### vt_green_knight
    * Note this is the generic armored knight. It’s called the green knight for legacy reasons.
* #### vt_black_knight
    !!!info "Special Properties"
        * should_move
            * 0: Will not move. Will stand in place, even after becoming aggroed.
            * 1: Will move toward player once aggroed

* #### vt_spider
* #### vt_cherub
    !!!info "Special Properties"
        * Must be triggered to function (see targetname above)
        * should_launch
            * 0: Should not launch when triggered
            * 1: Should launch when triggered (ie. fly upward briefly before firing)

* #### vt_marble_golem
* #### vt_cyclops
* #### vt_vampire
    !!!info "Special Properties"
        * Must be triggered to function (see targetname above)
        * should_launch
            * 0: Should not launch when triggered
            * 1: Should launch when triggered (ie. fly upward briefly before firing)

* #### vt_god_blood_vessel
* #### vt_skull
    !!!info "Special Properties"
        * Must be triggered to function (see targetname above)
        * should_launch
            * 0: Should not launch when triggered
            * 1: Should launch when triggered (ie. fly upward briefly before firing)
* #### vt_mage
    !!!info "Special Properties"
        * target
            * For the mage, the target property specifies the entity group that this mage should be tethered to with a magical shield link. Note the enemy it attaches to also needs a bubble_shield_id
        * death_target
            * This is the entity that should be triggered when this mage dies.

### vt_arrow_pickup
* A pickup that gives you arrows. If you haven’t picked up a bow yet, you’ll pick it up automatically when arrows are picked up

    !!!info "Key Properties"
        * arrow_count
        * type
            * The type of the arrow that should be picked up
                * 1: Explosive arrows
                * 2: Blood tether arrows

### vt_artifact_pickup
* Picks up an artifact part

    !!!info "Key Properties"
        * artifact_part_name
            * NO_ARTIFACT_NAM
            * RUSTY_BLADE_POMME
            * DRAGON_TOOTH_SCABBAR
            * BATTERED_SOUL_OF_PRISONE
            * RUSTY_IRON_RO
            * BENJIS_STIC
            * ORNATE_BLADE_PART_
            * ORNATE_BLADE_PART_
            * STONE_SWORD_PART_
            * STONE_SWORD_PART_
            * STONE_SWORD_PART_3
            * GLURMS_WALKING_STICK
            * GLURMS_NOTES
            * KINGS_BEATING_HEART
            * KINGS_BLADE_PART_2
            * ANCIENT_BOOK
            * GOD_KILLER_BLADE_PART_2
            * STONE_HEART
            * WIDGET
            * HOURGLASS
            * TRESS
            * TROWEL
            * FLAGELLUM
            * THREAD
            * GODSTEEL
            * SIN_BOOK
            * TALKING_SPIDER
            * BROTHERHOOD_COIN
            * LENS
            * SCREAMING_CRUCIBLE
            * VOW_OF_RETRIBUTION
            * MASK
            * BLESSED_OIL
            * BLOOD_CHALICE
            * FINETOOTH_GEAR
            * EXQUISITE_TOURBILLON
            * CALLUS
            * CAT_TAIL
            * WEDDING_RING
            * SEED
            * FINE_WINE
            * GROTESQUE
            * LOADED_DICE
            * TRIXIAN_MANTLE
            * VASYLGLASS_BANGLE
            * WIND_ESSENCE
            * BLAST_POWDER
            * THIEF_SHIV
            * THEOLMORIN_SHACKLE
            * OLD_VARU_KEY
            * PERMAFROST_CHUNK
            * FIRE_SLUG
            * CALMNESS_SUPPRESSANT
            * TREESAP
            * RAGE_MUSHROOM
            * TRIXIAN_STEEL

### vt_barrel
* An explosive barrel

### vt_bat_spinner
* A bat that flies in a circle.
### vt_bell
* Ringing the bell creates a trigger event

    !!!info "Key Properties"
        * target
            * The entity that should be triggered when the bell is rung

### vt_blood_fountain
* A triggerable blood fountain. Shoots blood in the air when triggered

    !!!info "Key Properties"
        * targetname
            * When this targetname is triggered, blood will be shot into the air

### vt_bow_pickup
* A pickup that gives you either an explosive crossbow (arrow_type=1) or a Blood Tether (arrow_type = 2)

    !!!info "Key Properties"
        * arrow_type
            * 1: Grants Explosive crossbow
            * 2: Grants Blood Tether
        * targetname
            * When this targetname is triggered, this pickup will be picked up.

### vt_color_torch
* A torch that typically is used as a wall decoration. Can be any color.

    !!!info "Key Properties"
        * light_color
            * The color of the light emitted from this torch in RGB (0-1) format. Use the Trenchbroom Color Picker to set this value
        * color
            * The color of the particles of the torch in RGB (0-1) format.  Use the Trenchbroom Color Picker to set this value.
        * scale
        * visibility_range
            * How far away the pixel fire is visible. Useful if scale is very high.

### vt_crack
* Creates a crack decal. Typically used to indicate that a wall is breakable. Point it away from the wall for best results

### vt_decor_candle
* a candle purely for decoration

### vt_decor_smoke
* a smoke particle effect for decoration

### vt_enemy_shoot_point
* Deprecated, not really useful. There was a point in time where enemies could shoot barrels but this proved to be frustrating so it was removed.

### vt_environment
* Used to change the environment and skybox. Only use one per map

    !!!info "Key Properties"
        * environment
            * Use the dropdown to specify which level’s environment you want to use for your map.

### vt_eyeball_pickup
* An eye of Ogamahn.

    !!!info "Key Properties"


        * target
            * The entity that should be triggered when picked up
        * eyeball_name
            * Each eyeball must have a unique name in your map for saving

### vt_eyeball_shrine
* A shrine of Ogamahn.

### vt_fish_spinner
* A fish that spins in a circle

### vt_floating_candle
* a floating candle for decoration

### vt_fmod_sound
* A sound that plays on a loop in a particular spot

    !!!info "Key Properties"
        * guid
            * The GUID of the sound to play. Possible values are
                * ENEMY_SKULL_SKULL_NESTING_SOUND
                * AMBIENT_CRICKETS
                * PLAYER_HEART_BEAT_SPATIAL
                * EFFECTS_WATERFALL_LOOP
                * AMBIENT_BIRDS
                * AMBIENT_DEFAULT_AMBIENT_SPATIAL

### vt_generic_pickup
* A powerup pickup

    !!!info "Key Properties"
        * powerup_type
            * BOUNCY_DASH
            * EXPLOSIVE_AIR_DASH
            * SUPER_SPEED
            * SLIDE_TO_KILL
            * UNLIMITED_BLOOD
        * target
            * The target to trigger when this powerup is picked up
        * target_func
            * The function on the target to call when this is picked up

### vt_health_pickup
* A blood vial

    !!!info "Key Properties"
        * target
            * The entity that should be triggered when picked up

### vt_huddled_god
### vt_key_pickup
* A key that can be used to lock doors or parts of the map. See vt_trigger_area for usage.

    !!!info "Key Properties"
        * key_name
            * The unique name of this key (not shown to the player)
        * pick_up_message
            * A message that appears when this key is picked up
        * color
            * The RGB (0-1) color of the key. Use the Trenchbroom color picker to set this
        * display_name
            * The name of the key that is shown to the player when this key is picked up or when an area requiring this key is reached.

### vt_lantern
* Deprecated, lanterns are not used in isolation. See vt_mage

### vt_lever
* A triggerable lever

    !!!info "Key Properties"
        * scale
            * Levers are pretty small by default. Set this to 4 for example to multiply the size by 4
        * targetname
            * Set this to make the lever triggerable. When the lever is triggered, the rod will pivot downward and the specified target will be triggered
        * target
            * The entity that should be triggered when this lever is triggered

### vt_music
* Used to change the music of the map. Only use one per map
* Note: all songs are "programmed" in a unique way, where the game transitions to a different part of the song depending on the "Intensity" of the game, controlled by vt_intensity_change_area.

    !!!info "Key Properties"
        * song
            * use the dropdown to select the song you desire. Songs match the names of the songs in the Bloodthief OST

### vt_pain_vessel
* A vessel of pain. Hidden by default, must be triggered to appear

    !!!info "Key Properties"
        * targetname
            * will appear when this targetname is triggered
        * explosion_force
            * The force of the explosion when this vessel is killed
        * should_flash
            * 0: Will not flash
            * 1: Will flash

### vt_player_start
* The starting point of the player. The forward of this point entity matches the starting forward of the player

    !!!info "Key Properties"
        * targetname
            * If this property is specified, instead of being the “start level” position for the player, this point will be the “checkpoint spawn” position for the checkpoint with a matching “target” property set. So for example if checkpoint 1 has a target of “foo”, and this vt_player_start has a targetname of “foo”, when the player spawns at checkpoint 1, they will spawn at the location of this entity.

### vt_portcullis
* deprecated

### vt_robed_statue
* Can only be killed by players level 130 or higher
* When killed, will trigger entities specified as the target

    !!!info "Key Properties"
        * target
            * The entity that should be triggered when this statue dies

### vt_sentient_heart
* the sentient heart of theolmorin

### vt_soul_spinner
* A spinning soul
### vt_stone_god
* Theolmorin
### vt_sup_light
* The main light entity in bloodthief

    !!!info "Key Properties"

        * light_energy
            * The strength of the light
        * light_color
            * The color of the light, represented in RGB (0-1) format
            * Note you can use Trenchbroom’s color picker in “float” mode to set the value of this property
        * omni_range
            * The Omnidirectional range of the light
        * omni_attenuation
            * The attenuation of the light

### vt_swinging_ax
* A swinging ax that can be used as an obstacle

    !!!info "Key Properties"
        * scale

### vt_torch
* A decorative torch

    !!!info "Key Properties"
        * show_mesh
            * 0: Don’t show the little stick of the torch. Useful if you’re making a fireplace or a brazier or something
        * scale
        * light_indirect_energy
        * visibility_range
            * How far away the pixel fire is visible. Useful if scale is very high.

### vt_triggerable_toast
* A dialogue that will appear when triggered

    !!!info "Key Properties"
        * targetname
            * When this is triggered, the text will appear
        * toast_text
            * the text that should appear
        * should_pause
            * If the game should pause when the toast appears

### vt_tutorial_pickup
* A book that will show a tutorial when picked up

    !!!info "Key Properties"
        * tutorial_title
        * tutorial_desc
        * tutorial_data_path
            * Ignore this, not useful for custom maps

### vt_util_counter
* A triggerable entity that counts the amount of times it has been triggered and will emit a new trigger when the desired count is achieved

    !!!info "Key Properties"
        * trigger_count
            * how many times this entity should be triggered before emitting a new trigger
        * targetname
            * When this targetname is triggered, the counter increments the count
        * target
            * When trigger_count is reached, this target is triggered
        * target_func
            * The function on the target that should be called when the target is triggered

### vt_util_delayed_trigger
* A triggerable entity that will emit a new trigger after a delay

    !!!info "Key Properties"

        * targetname
            * When this targetname is triggered, target will be triggered after trigger_delay seconds
        * target
            * the entity that should be triggered trigger_delay seconds after this entity has been triggered
        * target_func
            * The function that should be called on target when it is triggered
        * trigger_delay
            * The delay in seconds that should be waited after this entity is triggered before target is in-turn triggered.
        * vt_waypoint
            * Not useful in custom maps right now

## Brush Entities
Brush entities are entities that are based on a brush, ie. some volume of space drawn in Trenchbroom.

### func_geo
* For the most part functions the same as worldspawn / default geometry, but with a few extra features

    !!!info "Key Properties"
        * surface_type
            * Impacts the sound your feet make when you walk on it. Use the dropdown
        * window_color
            * If using one of the window textures, you can set this to color the window. use RGB (0-1)
        * friction_multiplier
            * The friction of the surface
        * chain_speed
            * If using the chain texture, this determines how fast the chains will move
        * navigable
            * COMING SOON: Use this to designate a piece of geo as navigable by enemies. Right now all geo is navigable in custom maps which is not very optimized. If you are running into optimization issues let me know and I’ll prioritize this.

### func_detail
* Similar to func_geo but with less properties. The main difference is that func_detail do not have an occlusion shape built for them. You can use this entity as an optimization if your map has a bunch of little details that do not need occlusion shapes.

    !!!info "Key Properties"
        * window_color
        * navigable

### func_detail_illusionary
* Similar to func_geo, but has no collision. Use this for pieces of geometry that are purely visual and the player and enemies should not collide with it

    !!!info "Key Properties"
        * window_color

### vt_blood_area
* When the player is in this area, they rapidly increase the Blood bar and they move faster

### vt_breakable
* A breakable object

    !!!info "Key Properties"

        * breakable_type
            * Use the dropdown to specify the type of the breakable
        * gi_mode
            * Not relevant for mapping as there is only 1 gi_mode in custom maps
        * jib_count_multiplier
            * Multiplies how many jibs that should emit when broken
        * target
            * The entity that should be triggered when broken
        * target_func
            * The function on the entity that should be called when broken
        * use_fake_rigidbodies
            * 0: Don’t use fake rigidbodies
            * 1: Use fake rigidbodies (more optimized but looks worse)
        * bubble_shield_id
            * When this is broken all entities with this bubble shield ID will have their shields removed
        * has_painting_blend_effect
            * Does something interesting to sir_brian_tuke texture
        * jib_lifetime
            * The lifetime of jibs once broken
        * translation
            * If set, this breakable also will function as a mover. See vt_mover for additional properties to use
        * reverb_level
            * The reverb amount when broken (0-1 value)
        * should_jib
            * 0: Jibs will not be emitted when broken
            * 1: Jibs will be emitted when broken
        * has_collision:
            * 0: No collision
            * 1: Collision
        * navigable:
            * If this is navigable
            * 0: No
            * 1: Yes
        * jib_scale
            * The scale of jibs
        * jib_type
            * GORE, NON_GORE, GLASS, GOD
        * hide_after_checkpoint
            * The checkpoint index at which this breakable becomes hidden
        * friction_multiplier
            * The amount of friction the player’s movement has when standing on top of this breakable

### vt_checkpoint_area
* A checkpoint. When the player respawns at checkpoint if the current checkpoint matches this area’s checkpoint index, the player will spawn here at the bottom center of this area facing in the direction specified by the angle property.

    !!!info "Key Properties"
        * checkpoint_index
            * When a level starts, the player starts at checkpoint 0. When the player enters this area, the current checkpoint will be set to at least this index. So if this is set to 1, the player checkpoint will be set to checkpoint 1. When the player respawns at checkpoint, they will spawn at the bottom center of this checkpoint by default. Alternatively, a specific point in space can be specified, see target property.
        * checkpoint_region
            * An optional property that can be set to give your checkpoint a region. Regions can be used for “non-linear” maps that can be progressed in different orders. Perhaps the left path has a checkpoint with region “left” and checkpoint_index 1 and the right path has region “right” with checkpoint_index 1. This allows the checkpoints to be reached in any order and still work as expected.
        * angle
            * This is the direction the player should be facing when spawning at checkpoint if target property is not set. In trenchbroom the direction the player will face is shown by a little arrow in the center of the checkpoint area.
        * target
            * optional property. Can be set to a vt_player_start with the same targetname to specify the exact point where the player should spawn when respawning at this checkpoint
        * checkpoint_active_trigger_count
            * Zero by default. This is the amount of times this checkpoint must be triggered before it is reachable
        * targetname
            * When this targetname is triggered, the count corresponding to checkpoint_active_trigger_count is incremented.

### vt_damage_area
* If the player enters this area, they will die. Note enemies will not be impacted by damage movers.

    !!!info "Key Properties"
        * has_piranhas
            * If piranhas should emerge from the area when the player dies
            * 0: no
            * 1: yes

### vt_damage_mover
* Exactly the same as a vt_mover except it does damage when the player touches it.

    !!!info "Key Properties (incomplete, see vt_mover for other properties)"
        * has_spikes
            * Whether spikes should be generated within the volume of this entity.
            * Note: Spike generation looks for a nearby surface normal to determine the direction of the spikes. A proper vt_damage_mover placement with spikes would be a shallow (16-32 in depth) brush that is touching a vt_mover or a piece of solid geometry.
            * 0: No spikes
            1: Spikes
        * damage_type
            * LAVA, NORMAL, DAMAGE_AREA
        * hardcoded_normal
            * See has_spikes. This will be the direction of the spikes if this value is set.

### vt_end_level_area
* When this area is reached, the level ends

### vt_intensity_change_area
* When this area is reached, the intensity of the level is set to at least intensity_level. See vt_music.

    !!!info "Key Properties"
        * intensity_level (0-1): The intensity that the level should be set to when reached

### vt_launchpad
* A launchpad that bounces the player

    !!!info "Key Properties"
        * bounce_force
        * bounce_force_max
        * overwrite_velocity
            * 0: no
            * 1: yes
        * launch_dir
            * optional, use this if the launch dir is different from the nearby surface normal of the launch pad
        * translation
            * optional. Use this for the launchpad to also function as a vt_mover

### vt_lava
* lava

### vt_magnet_area
* a region that will very slightly magnetize the player toward the center

### vt_mover
* An entity that moves when triggered

    !!!info "Key Properties"

        * targetname
            * when this targetname is triggered, the mover moves
        * translation
            * The translation that should occur when triggered, in Godot Units / coordinate system. Do not specify this if tb_translation is already set
        * tb_translation
            * The translation that should occur when triggered, in Trenchbroom Units / coordinate system. Do not specify this if translation is already set
        * duration
            * How long in seconds the mover should take to perform the translation when triggered
        * auto_move_after_checkpoint
            * When the player respawns at checkpoint index >= this value, the mover will automatically teleport to its terminal position
        * auto_move_after_checkpoint_region
            * When the player respawns at checkpoint index >= auto_move_after_checkpoint  and region == this value, the mover will automatically teleport to its terminal position
        * move_delay
            * The delay that should be waited after targetname is triggered before this mover will start moving
        * trigger_count
            * How many times this mover should be triggered before moving. Default is 1
        * gt_mode
            * Not needed for custom maps
        * end_position_ratio_in_editor
            * not used in custom maps
        * play_sound
            * 0: Don’t play sound when moving
            * 1: Do play sound
        * start_motion_target
            * The target that should be triggered when motion of this mover begins
        * end_motion_target
            * The target that should be triggered when motion of this mover ends
        * end_motion_message
            * A message that should display when motion ends
        * start_motion_message
            * A message that should display when motion begins
        * move_on_start
            * If this mover should start moving right away
            * 1: yes
            * 0: no
        * oscillate
            * 1: Immediately reverse motion when motion is finished
            * 0: Stop when motion ends
        * delay_between_oscillation
            * Value in seconds that should be waited before reversing motion
        * match_speed_with_player
            * 0: Dont match speed with player. Simply move at speed corresponding to duration
            * 1: Move faster if player is moving faster
        * start_motion_shake
            * 0 to 1 value. The amount of shake that should happen when motion is started
        * end_motion_shake
            * 0 to 1 value. The amount of shake that should happen when motion is ended
        * constant_motion_shake
            * 0 to 1 value. The amount of shake that should happen when motion is playing
        * reverb_level
            * The amount of reverb that should play when moving. See play_sound
        * reverse_motion_duration
            * If reverse duration is different than duration, set this value
        * dont_play_stop_sound_for_reverse_motion
            * 1: Don’t play sound reverse motion
            * 0: Do play sound for reverse motion
        * end_motion_target_func
            * The function to be called on end_motion_target when motion is ended
        * should_knock
            * the mover will play a door knocking sound while untriggered, as if there is someone behind it
            * 1: play the sound
        * one_more_message
            * When trigger_count > 2 and the entity has been triggered trigger_count - 1 times, this message will be shown
        * disable_collider_on_move
            * Whether the collider should be disabled on move
        * should_loop
            * Similar to oscillate except it teleports back to the beginning and immediately starts again when it reaches its terminal position
        * ease_type
            * valid types are EASE_IN_OUT, EASE_OUT_IN, EASE_IN, EASE_OUT
        * trans_type
            * valid types are TRANS_BACK, TRANS_BOUNCE, TRANS_QUAD, TRANS_QUINT, TRANS_QUART, TRANS_ELASTIC
        * is_wet
            * Determines if a wet sound is played for this mover
            * 1: yes
        * player_only_world_collision
            * If the player is the only thing that should collide with this
            * 1: yes
            * 0: no

### vt_oob_area
* deprecated

### vt_secret_area
* Will notify the player that they found a secret when this area is entered

    !!!info "Key Properties"
        * secret_name
            * Required. Make sure to give it a unique name for the map.

### vt_spinner_solid
* A piece of geometry that will spin. Use the origin texture to set the origin of the geometry which determines the pivot of the spin. Otherwise it will just spin around the center of the geometry in the direction of the rotation_axis

    !!!info "Key Properties"
        * speed
        * radius
        * rotation_axis

### vt_toast_area
* An area that displays dialogue on the screen when the player enters the area

    !!!info "Key Properties"
        * toast_text
        * should_pause
        * time_scale
        * toast_type
            * use the dropdown
        * display_condition
            * Only displays if this condition has been met, possible options are
        * has_not_yet_been_triggered
        * has_not_yet_been_triggered_and_is_godly
        * is_tutorial
        * targetname
        * full_speed_action
        * should_squash


### vt_trigger_area
* an area that will trigger the specified target when entered

    !!!info "Key Properties"

        * target
            * The entity that should be triggered when this area is entered
        * target_func
            * the function on the target that should be called
        * trigger_dependency_count
            * The amount of times this area must be triggered before it will emit a trigger when entered
        * targetname
            * use this to trigger the area corresponding to trigger_dependency_count
        * required_keys_comma_sep
            * The keys that are required for this trigger area to trigger the target when entered. See key_name property on vt_key
        * required_artifacts_comma_sep
            * The artifact parts that must be collected for this trigger area to trigger the target when entered.
        * trigger_delay
        * show_locked_message
            * 0: Will not show any message when the player doesn’t have the required keys
        * trigger_once
            * 1: When this area is entered consecutive times, it will not trigger the target again
            * 0: When this area is entered consecutive times, it triggers the target each time
        * exit_target
            * The target to trigger when this area is exited
        * exit_target_func
            * The target function to call
        * is_enemy_trigger
            * 1: This trigger area triggers when enemies enter it, instead of when the player enters it.
        * vt_water
            * Creates water that the player can swim in
