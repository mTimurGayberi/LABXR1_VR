# 📝 Development Log (DevLog)

A quick log of progress and updates. Please keep entries concise.

**Format:**
`- [YYYY-MM-DD] [Name (Role)]: Summary of work done`

---

## 📅 November 2026

### 2026-11-22
* **Timur (Dev):**
  * Created abstract base class `BP_GrabbableItem` with integrated magnetic distance-pull (Gravity Glove telekinesis), smooth flight interpolation (`VInterp To`), automatic `TryGrab` hand snap, and a 0.8s drop cooldown preventing immediate re-snapping.
  * Implemented forward-pointing VR raycast (`Sphere Trace For Objects`, radius 15cm, range 120cm) on `BP_XRPawn` for intuitive dual-hand aiming and distance-grabbing.
  * Built `OnItemCaught` hand-off event on `BP_XRPawn` ensuring true physical "hold-to-grip and ungrip-to-drop" ergonomics across both controllers.
  * Reparented `BP_OxygenTank` to inherit from `BP_GrabbableItem`, providing seamless ground reachability and magnetic retrieval without bending down to the physical floor.
  * Hardened `BP_OxygenStation` socket docking and ejection filters (`Other Comp == ItemMesh`) to eliminate trigger interference and socket re-snapping.

### 2026-11-14
* **Timur (Dev):**
  * Created interactive `BP_OxygenStation` with finite oxygen reserves, player refill trigger zone, and Action Button integration (`IA_Interact` on Quest 'A' button & 'E' keyboard).
  * Implemented physics-simulated grabbable `BP_OxygenTank` with dual-hand VR grab and throw capabilities.
  * Engineered magnetic socket docking system: seamless hand-release via `E_GrabType` bypass, snap attachment, latent release guard (`0.5s` delay with `Is Valid` protection), and natural pull-to-demount via `OnComponentEndOverlap`.
  * Guarded station transfer tick so gas can only be replenished when an actual physical tank is docked and loaded.
  * Added `CapsuleCollision` to `BP_XRPawn` enabling reliable station trigger detection and interact inputs.
  * Logged pending VR polish items: floor grab reachability / offset and socket Z alignment.

### 2026-11-12
* **Timur (Dev):**
  * Added dynamic exertion-based stamina recovery delay (`StaminaRegenDelayTimer`) using `Lerp` scaling between 0.5s (minor sprint) and 2.5s (total exhaustion).
  * Built physiological oxygen depletion system (`UpdateOxygen`): base drain calibrated to tank lifetime (10 minutes) with real-time breathing multiplier scaling up to 2.5x during stamina exertion.
  * Implemented oxygen replenishment API (`FullRefillOxygen` and `AddOxygen`) for station docking and portable canister interactions.
  * Fast-forward merged verified survival gameplay mechanics into `main`.

### 2026-11-11
* **Timur (Dev):**
  * Created dedicated `BP_PlayerStatsComponent` ActorComponent in `Content/_Shared/` to decouple survival statistics from pawn logic.
  * Configured core survival variables (O2 duration, stamina rates, flashlight battery, compass navigation).
  * Built live 360° VR compass heading normalizer and 8-cardinal direction calculator (`[N, NE, E, SE, S, SW, W, NW]`).
  * Implemented VR sprint locomotion via `IA_Sprint` mapped to Left Thumbstick Button across Quest, Index, Vive, and Left Shift.
  * Built modular `UpdateStamina(DeltaSeconds)` function with framerate-independent drain, clamped regen, and exhaustion auto-stop.
  * Cleanly merged `feature/vr-helmet-hud` into `main` to establish the station blockout + core survival gameplay baseline.

### 2026-11-09
* **Timur (Dev):**
  * Created physical Astronaut Helmet system (`HelmetRoot`) with realistic rotational inertia and head lag using damped `RInterp To` math.
  * Designed translucent helmet visor glass material (`M_VisorGlass_Warp`) with crystal-clear center vision and peripheral corner comfort vignette.
  * Modeled and integrated custom curved single-surface 3D astronaut visor mesh (`visor.uasset`) to wrap naturally around player's stereoscopic field of view.

### 2026-11-02
* **Timur (Dev):**
  * Implemented full 360° VR Smooth Locomotion on Left Thumbstick (`IA_Move` 2D Vector + head-oriented vector math).
  * Added obstacle collision sweeping (`bSweep`) and framerate-independent walking speed.
  * Implemented Main Menu movement auto-lock (`bAllowLocomotion`) based on level detection.
  * Added ambidextrous laser pointer interaction (`IA_Shoot_Left` & `IA_Shoot_Right`) with multi-headset bindings (Quest, Index, Vive, WMR).
  * Standardized Snap Turning to Right Thumbstick (`IA_Turn`) matching VR industry standards.

## 📅 October 2026

### 2026-10-31
* **Timur (Dev):**
  * Created `L_MainMenu` and 3D VR interface (`BP_MenuBoard` + `WBP_MainMenu`) styled with team UI tokens.
  * Implemented VR controller laser pointer & trigger click (`IA_Shoot_Right` on Meta Quest 2).
  * Added click debounce protection (`DoOnce` + button disable) to prevent duplicate level loads.
  * Verified end-to-end VR game loop: 3D Menu -> Quest 2 pointer click -> fade transition -> Campus load.

### 2026-10-22
* **Timur (Dev):**
  * Created `BP_VRGameInstance` for persistent VR comfort & volume settings.
  * Built camera fade transitions (`TransitionToLevel`, `OnLevelLoadedFadeIn`) to prevent VR motion sickness.
  * Created `BP_SaveGame` with auto save/load from disk on startup (`SaveSettingsToDisk`, `LoadSettingsFromDisk`).

### 2026-10-20
* **Team:**
  * Assigned team roles (Reference, Blockout, Art Direction, Concept Art, UI/UX, Narrative, 3D Art, Dev).
  * Project Miro board and Discord co-working channels set up.

### 2026-10-26
* **Can Berk (Level Designer)**
  * Created Sublevels for each building and Navigation
  * Did file management
  * Started on Building A Level 0 Blockout

### 2026-11-02
* **Can Berk (Level Designer)**
  * Started on Building B Level 0 Blockout

### 2026-11-05
* **Can Berk (Level Designer)**
  * Progress on Building A and B Blockout, Levels 1, 2, 3 and the elevated bridge in between.

### 2026-11-09
* **Can Berk (Level Designer)**
  * Progress on Building C, only the frame for now.

### 2026-11-26
* **Mehmet Timur Gayberi (Lead Dev):**
  * **Dynamic Carry Encumbrance (`BP_XRPawn`):**
    * Implemented pure function `GetSpeedMultiplier` querying `HeldComponentRight` and `HeldComponentLeft`.
    * Applied smooth speed scaling: 100% base speed (0 items), 75% speed (1 item held), 50% speed (2 items held).
  * **Modular Hand State Architecture (`IsHandBusy`):**
    * Created `IsHandBusy(EControllerHand Hand)` pure helper in `BP_XRPawn` for modular hand availability validation across interactive station components.
  * **Root Capsule Collision & Wall Clipping Fix:**
    * Promoted `Capsule` to RootComponent in `BP_XRPawn` (`VROrigin` offset set to `Z = -88.0` for 1:1 OpenXR floor alignment).
    * Configured collision response: `WorldStatic = Block`, `WorldDynamic = Block`, `Visibility = Ignore`, `Camera = Ignore`.
    * Set `PhysicsBody = Ignore` on the pawn capsule, resolving the blocking collision bug when holding objects (e.g. oxygen tanks) close to the chest.
    * Enabled `Sweep = True` on horizontal movement in `EventGraph`, preventing walking through station walls and doorways.
  * **Stair & Slope Locomotion Engine (`GetStepAdjustedDelta`):**
    * Designed dual-trace hybrid locomotion algorithm separating vertical terrain adjustment (`Sweep = False`) from horizontal movement (`Sweep = True`):
      * **Ahead Trace (Step-Up):** Casts 50 cm ahead with 2D-normalized movement vector, detecting steps ($+3.0\text{ cm to }+60.0\text{ cm}$) and lifting the capsule smoothly via `FInterp To` (Speed 40.0) before physical riser impact.
      * **Feet Trace (Step-Down):** Casts downward directly beneath capsule center, detecting ground drops ($-80.0\text{ cm to }-3.0\text{ cm}$) and smoothly lowering the capsule onto lower steps or downhill slopes.
      * **Anti-Hopping Conflict Resolution:** Added `NOT (Ahead Z > Feet Z + 5.0)` gate on the Feet Trace, resolving the "tug-of-war" hopping loop on tall 45 cm entrance steps.
  * **Station Tool Assets:**
    * Imported `Toy_FlashLight` modular assets in `Content/Fab/` in preparation for equippable station flashlight tool.
  * **Custom Astronaut VR Hands Integration:**
    * Successfully integrated custom astronaut gloves into `BP_XRPawn` mapped to `SK_MannequinsXR` VR skeleton.
    * Resolved Blender FBX armature naming (`Armature`) for seamless root bone merging with OpenXR standard.
    * Fixed right hand mirrored transform issues (baked negative scale transforms, recalculated normals outside, mirrored vertex groups to `_r`).
    * Verified dual-hand finger articulation, grip curling, and gestures in VR headset.



