# Godot Tutorials Series, by Davide Pesce

## Knowledge
- Collision objects
  - Collision Detection
  - Collision Response

- 4 kinds of collision objects
  1. KinematicBody2D - no movement after collision
    - For player
    - Use `move_and_collide()` or `move_and_slide()` to move
      - `move_and_collide()`:`KinematicCollision2D`
    - **TIPS**: Inspector > Z Index = 1, to ensure the player is always drawn above the environmental objects
  2. StaticBody2D - do not move
     - For environmental elements
  3. RigidBody2D - simulated 2D physics with gravity, impluses, etc.
     - Usually you do not control it directly.
     - Set world's propertiesat Project Settings > Physics
     - For top-down RPG that don't need gravity:
       Inspector > Gravity Scale=0; Linear > Damp=10; Angular > Damp=5 to add friction
  4. Area2D - to detect overlap with other collision objects (enter or exit events)
     - Node > Area2D > `body_entered` > connect to itself (Area2D)
       ```
       func _on_Flowers_body_entered(body):
       	if body.name == "Player":
       		get_tree().queue_delete(self)
       ```
       to remove flowers itself when the player move over it.

- TextureRegion
  - Rather then using the whole image, you could sepcify only a small region from a big ImageTexture.
  - Sprite object > Inspector: Region > Enabled = On
  - **TIPS**: Snap Mode: Grid Snap

