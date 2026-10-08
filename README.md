# LABXR1 VR Campus Project

Welcome to the LABXR1 VR Project! This repository contains our Unreal Engine VR project where we are recreating our campus (3 buildings with different art styles and sidequests). 

**🚨 IMPORTANT: This project is built using Unreal Engine 5.7.4. Please ensure you are using this exact version to avoid compatibility issues.**

This repository is primarily managed by the lead programmer for syncing between workstations. **If you would like to become a direct contributor on Git, please reach out to me personally.** Any team member contributing directly to the project files should read the rules below.

## ⚠️ CRITICAL: Git LFS (Large File Storage)

Unreal Engine uses large binary files (`.uasset`, `.umap`, textures, models). You **MUST** have Git LFS installed before you clone this repository, otherwise, the project will be broken.

**How to install Git LFS:**
1. Download and install Git LFS from here: [https://git-lfs.com/](https://git-lfs.com/)
2. Open your terminal or command prompt and run:
   ```bash
   git lfs install
   ```
3. You only need to run this command once per computer. After that, Git will handle large files automatically when you pull/push.

## 🌍 World Partition

This project utilizes Unreal Engine's **World Partition** system. 
Instead of saving the entire map as a single `.umap` file (which causes massive merge conflicts), World Partition saves each object in the world as its own file. 
*   **Do not disable World Partition.** 
*   It allows us to place assets in the level without constantly stepping on each other's toes.

## 📁 Naming Conventions

To keep our `Content` folder clean and organized, please adhere to the standard Unreal Engine naming conventions when importing or creating assets:

*   **Blueprints:** `BP_ObjectName` (e.g., `BP_Elevator`)
*   **Static Meshes:** `SM_ObjectName` (e.g., `SM_Desk`)
*   **Materials:** `M_MaterialName` (e.g., `M_Wood`)
*   **Material Instances:** `MI_MaterialName` (e.g., `MI_Wood_Dark`)
*   **Textures:** `T_TextureName_Suffix` (e.g., `T_Wood_D` for Diffuse, `T_Wood_N` for Normal)
*   **Levels/Maps:** `L_MapName` (e.g., `L_BuildingA`)

## 🏗️ Folder Structure

When adding assets, please place them in their respective folders:
*   `BuildingA/` - Assets specifically for Building A
*   `BuildingB/` - Assets specifically for Building B
*   `BuildingC/` - Assets specifically for Building C
*   `_Shared/` - Generic assets used across multiple buildings (e.g., player character, basic UI)

If you are an artist providing raw files (`.blend`, `.psd`, `.fbx`), it's generally best to provide them via Google Drive or another share, and the lead programmer will import them into the engine to ensure they are configured correctly. If you are importing them yourself, follow the naming rules!

## 🔄 Workflow Reminder

**Friendly Reminder:** Always `git pull` (or fetch and pull) before you start working for the day! This ensures you have the latest changes and minimizes the chance of merge conflicts.

## 📞 Support & Contact

If you have any issues with this project, need help with Git, or are stuck on Unreal Engine setup, please contact **Mehmety Timur Gayberi**:
*   **Email:** [s37288@pjwstk.edu.pl](mailto:s37288@pjwstk.edu.pl)
*   **Discord:** `m.timur`
