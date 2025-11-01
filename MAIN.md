@namespace
class SpriteKind:
    placment = SpriteKind.create()
# --- When the player presses LEFT, the background scrolls at -50 speed --

def on_left_pressed():
    scroller.scroll_background_with_speed(-50, 0)
controller.left.on_event(ControllerButtonEvent.PRESSED, on_left_pressed)

# --- When countdown ends (after intro), this function starts the actual game ---
# Starts at full health (100)

def on_countdown_end():
    global mySprite, statusbar
    # Create player's car sprite (red Ferrari image)
    mySprite = sprites.create(assets.image("""
        ferrari
        """), SpriteKind.player)
    controller.move_sprite(mySprite, 50, 70)
    # Enable movement with W A S D or arrow keys
    mySprite.set_stay_in_screen(True)
    # Keep the car inside the screen
    # Create a health bar (status bar) in the top left corner
    statusbar = statusbars.create(50, 4, StatusBarKind.health)
    statusbar.set_label("HP")
    # Shows "HP" text
    statusbar.set_bar_border(1, 1)
    # Adds a thin 1px border
    statusbar.position_direction(CollisionDirection.LEFT)
    statusbar.set_offset_padding(-55, 2)
    # Places it near top-left corner
    statusbar.value = 100
info.on_countdown_end(on_countdown_end)

# # --- ENTER EXTRA HARD MODE, when Score reach 10, which car spawn rate are now double ---
# # code loops every 20000ms

def on_on_score():
    global choice, projectile
    while True:
        choice = randint(1, 6)
        if choice == 1:
            projectile = sprites.create_projectile_from_side(assets.image("""
                ferrari0
                """), -60, 0)
        elif choice == 2:
            projectile = sprites.create_projectile_from_side(assets.image("""
                purple car
                """), -60, 0)
        elif choice == 3:
            projectile = sprites.create_projectile_from_side(assets.image("""
                ferrari2
                """), -60, 0)
        elif choice == 4:
            projectile = sprites.create_projectile_from_side(assets.image("""
                truck
                """), -60, 0)
        elif choice == 5:
            projectile = sprites.create_projectile_from_side(assets.image("""
                cop0
                """), -60, 0)
        else:
            projectile = sprites.create_projectile_from_side(img("""
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . b b . . . . . . .
                    . . . . . . b 5 5 b . . . . . .
                    . . . b b b 5 5 1 1 b b b . . .
                    . . . b 5 5 5 5 1 1 5 5 b . . .
                    . . . . b d 5 5 5 5 d b . . . .
                    . . . . c b 5 5 5 5 b c . . . .
                    . . . . c 5 d d d d 5 c . . . .
                    . . . . c 5 d c c d 5 c . . . .
                    . . . . c c c . . c c c . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    """),
                -60,
                0)
            projectile.set_kind(SpriteKind.food)
        projectile.set_position(160, 0)
        projectile.y = randint(15, 60)
        pause(2000)
info.on_score(10, on_on_score)

# --- When health bar reaches 0, game over (you lose) ---

def on_on_zero(status):
    game.game_over(False)
statusbars.on_zero(StatusBarKind.health, on_on_zero)

# --- When RIGHT is pressed, background scrolls faster (-100 speed) ---
# simulates "accelerating" the car

def on_right_pressed():
    scroller.scroll_background_with_speed(-100, 0)
controller.right.on_event(ControllerButtonEvent.PRESSED, on_right_pressed)

# when sprite overlaps with enermy, player lose healths by 1, while camera shakes for half a second

def on_on_overlap(sprite, otherSprite):
    statusbar.value += -1
    scene.camera_shake(4, 500)
sprites.on_overlap(SpriteKind.player, SpriteKind.projectile, on_on_overlap)

# when sprite overlaps with STAR(food) player add healths and score by 1 and star despawn.

def on_on_overlap2(sprite2, otherSprite2):
    sprites.destroy(otherSprite2)
    info.change_score_by(1)
    statusbar.value += 5
    sprite2.start_effect(effects.hearts, 100)
sprites.on_overlap(SpriteKind.player, SpriteKind.food, on_on_overlap2)

# when projectile overlaps with other projectile they despawn to avoid cars visually overlapping

def on_on_overlap3(sprite22, otherSprite22):
    sprites.destroy(otherSprite22)
sprites.on_overlap(SpriteKind.projectile, SpriteKind.projectile, on_on_overlap3)

# # --- ENTER HARD MODE, when Score reach 6, which oncoming car spawn rate are now double ---
# # code loops every 1000ms

def on_on_score2():
    global choice, projectile
    while True:
        choice = randint(1, 4)
        if choice == 1:
            projectile = sprites.create_projectile_from_side(assets.image("""
                truck 2
                """), -120, 0)
        elif choice == 2:
            projectile = sprites.create_projectile_from_side(assets.image("""
                ferrari3
                """), -120, 0)
        elif choice == 3:
            projectile = sprites.create_projectile_from_side(assets.image("""
                cop1
                """), -120, 0)
        else:
            projectile = sprites.create_projectile_from_side(assets.image("""
                purple car 2
                """), -120, 0)
        projectile.set_position(160, 0)
        projectile.y = randint(75, 110)
        pause(1000)
info.on_score(6, on_on_score2)

# # --- ENTER HARD MODE, when Score reach 5, which car spawn rate are now double ---
# # code loops every 1000ms

def on_on_score3():
    global choice, projectile
    while True:
        choice = randint(1, 6)
        if choice == 1:
            projectile = sprites.create_projectile_from_side(assets.image("""
                ferrari0
                """), -60, 0)
        elif choice == 2:
            projectile = sprites.create_projectile_from_side(assets.image("""
                purple car
                """), -60, 0)
        elif choice == 3:
            projectile = sprites.create_projectile_from_side(assets.image("""
                ferrari2
                """), -60, 0)
        elif choice == 4:
            projectile = sprites.create_projectile_from_side(assets.image("""
                truck
                """), -60, 0)
        elif choice == 5:
            projectile = sprites.create_projectile_from_side(assets.image("""
                cop0
                """), -60, 0)
        else:
            projectile = sprites.create_projectile_from_side(img("""
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . b b . . . . . . .
                    . . . . . . b 5 5 b . . . . . .
                    . . . b b b 5 5 1 1 b b b . . .
                    . . . b 5 5 5 5 1 1 5 5 b . . .
                    . . . . b d 5 5 5 5 d b . . . .
                    . . . . c b 5 5 5 5 b c . . . .
                    . . . . c 5 d d d d 5 c . . . .
                    . . . . c 5 d c c d 5 c . . . .
                    . . . . c c c . . c c c . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    . . . . . . . . . . . . . . . .
                    """),
                -60,
                0)
            projectile.set_kind(SpriteKind.food)
        projectile.set_position(160, 0)
        projectile.y = randint(15, 60)
        choice = randint(1, 6)
        pause(1000)
info.on_score(5, on_on_score3)

projectile: Sprite = None
choice = 0
statusbar: StatusBarSprite = None
mySprite: Sprite = None
# --- Game Start: Intro scene before countdown begins ---
# Set background and slow scrolling speed (-50)
scene.set_background_image(assets.image("""
    myImage
    """))
scroller.scroll_background_with_speed(-50, 0)
# Custom dialog box frame (the pattern of 1s is just the frame design)
game.set_dialog_frame(img("""
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    111111111111111111111111111111111111111111111111
    """))
# Title splash
game.splash("Peak Hour Traffic SIM")
# Temporary placement sprite for showing the car before the countdown
mySprite2 = sprites.create(assets.image("""
    ferrari
    """), SpriteKind.placment)
mySprite2.change_scale(2, ScaleAnchor.BOTTOM)
# Makes the car bigger
# Show instructions to player (line by line)
game.show_long_text("use W A S D to control", DialogLayout.BOTTOM)
game.show_long_text("Survive as long as possible", DialogLayout.BOTTOM)
game.show_long_text("And Collect all the stars", DialogLayout.BOTTOM)
# Destroy the intro sprite once tutorial ends
sprites.destroy(mySprite2)
# Start a 3-second countdown before the actual game begins
info.start_countdown(3)
# --- Spawn traffic and stars every 500 ms (two lanes) ---
# Bottom lane spawner (75–110 y position)

def on_update_interval():
    global choice, projectile
    choice = randint(1, 4)
    if choice == 1:
        projectile = sprites.create_projectile_from_side(assets.image("""
            truck 2
            """), -120, 0)
    elif choice == 2:
        projectile = sprites.create_projectile_from_side(assets.image("""
            ferrari3
            """), -120, 0)
    elif choice == 3:
        projectile = sprites.create_projectile_from_side(assets.image("""
            cop1
            """), -120, 0)
    else:
        projectile = sprites.create_projectile_from_side(assets.image("""
            purple car 2
            """), -120, 0)
    projectile.set_position(160, 0)
    projectile.y = randint(75, 110)
game.on_update_interval(500, on_update_interval)

# --- Top lane spawner (75–110 y position) ---
# Similar logic, but includes chance of spawning a collectible star

def on_update_interval2():
    global choice, projectile
    choice = randint(1, 6)
    if choice == 1:
        projectile = sprites.create_projectile_from_side(assets.image("""
            ferrari0
            """), -60, 0)
    elif choice == 2:
        projectile = sprites.create_projectile_from_side(assets.image("""
            purple car
            """), -60, 0)
    elif choice == 3:
        projectile = sprites.create_projectile_from_side(assets.image("""
            ferrari2
            """), -60, 0)
    elif choice == 4:
        projectile = sprites.create_projectile_from_side(assets.image("""
            truck
            """), -60, 0)
    elif choice == 5:
        projectile = sprites.create_projectile_from_side(assets.image("""
            cop0
            """), -60, 0)
    else:
        projectile = sprites.create_projectile_from_side(img("""
                . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . .
                . . . . . . . b b . . . . . . .
                . . . . . . b 5 5 b . . . . . .
                . . . b b b 5 5 1 1 b b b . . .
                . . . b 5 5 5 5 1 1 5 5 b . . .
                . . . . b d 5 5 5 5 d b . . . .
                . . . . c b 5 5 5 5 b c . . . .
                . . . . c 5 d d d d 5 c . . . .
                . . . . c 5 d c c d 5 c . . . .
                . . . . c c c . . c c c . . . .
                . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . .
                . . . . . . . . . . . . . . . .
                """),
            -60,
            0)
        projectile.set_kind(SpriteKind.food)
    projectile.set_position(160, 0)
    projectile.y = randint(15, 60)
game.on_update_interval(500, on_update_interval2)

# --- Spawn traffic and stars every 500 ms (two lanes) ---
# Bottom lane spawner (15-60 y position)

def on_update_interval3():
    pass
game.on_update_interval(500, on_update_interval3)
