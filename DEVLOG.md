# 📝 Development Log (DevLog)

A quick log of progress and updates. Please keep entries concise.

**Format:**
`- [YYYY-MM-DD] [Name (Role)]: Summary of work done`

---

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
