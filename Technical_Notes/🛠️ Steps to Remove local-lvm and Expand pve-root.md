
### 🛠️ Steps to Remove `local-lvm` and Expand `pve-root`

1. **Access the Datacenter**
    
    - Open the Proxmox GUI.
    - Navigate to `Datacenter` > `Storage`.
2. **Remove `local-lvm`**
    
    - Select `local-lvm` from the list.
    - Click `Remove` to delete the reference.
3. **Open the Shell**
    
    - Launch the terminal or use the built-in shell in the GUI.
4. **Remove the Logical Volume**
    
    ```bash
    lvremove /dev/pve/data
    ```
    
    - This removes the `data` logical volume to free up space.
5. **Resize the Root Volume**
    
    ```bash
    lvresize -l +100%FREE /dev/pve/root
    ```
    
    - Expands the root volume (`pve-root`) to use all available space.
6. **Resize the Filesystem**
    
    ```bash
    resize2fs /dev/mapper/pve-root
    ```
    
    - Adjusts the filesystem to match the new logical volume size.
7. **Verify Storage Changes**
    
    ```bash
    df -h
    ```
    
    - Confirms that the root filesystem has expanded successfully.

8. Add Container and VM support on local
	- go to local->Edit->General->Content->Enable All