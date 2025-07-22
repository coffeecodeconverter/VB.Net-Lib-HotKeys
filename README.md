# VB.Net-Lib-HotKeys
Create Customised Global Hotkeys For Anything - VB.net (Module and Form) 


# 🔥 Global Hotkey Assignment Manager (.NET WinForms)

A **fully customizable global hotkey assignment manager** for Windows Forms applications — designed to be easily **plugged into any existing VB.NET project**.

---

## 📦 What It Is

This is a lightweight, self-contained module + UI system that lets you:

- Assign **global hotkeys** (that work outside the app)
- Map them to any function/action in your app
- Enable/disable hotkeys at runtime
- Export and import hotkey settings via JSON
- Manage assignments visually through a built-in form

---

<img width="459" height="661" alt="image" src="https://github.com/user-attachments/assets/72e24cfa-9cbf-4957-abb8-fda062e1fac7" />


## 🚀 Features

✅ Global hotkey support (system-wide, even when app is not focused)  
✅ Supports modifiers: `Ctrl`, `Alt`, `Shift` (Win key optional with small tweak)  
✅ Visual manager form with:
  - Function list
  - Key/modifier pickers
  - Assignment and deletion
  - Live hotkey toggling  
✅ JSON import/export (backups & shareable configs)  
✅ Auto-backup toggle  
✅ Conflict detection with smart reassignment options  
✅ Built-in search/filter in UI  
✅ Designed for .NET Framework **4.5.1+** (for broad compatibility)

---

## 🧰 What’s Included

### `CustomHotKeys.vb` (Module)
- Handles all the hotkey logic
- Manages registration/unregistration
- Includes helpers for serialization, parsing, conflict detection

### `Form1.vb` (Preset UI)
- Fully working UI to test/manage hotkeys
- Can be reused directly or adapted to your own forms

---

## 🧩 Use Cases

- Power-user tools
- Admin panels
- Background utilities
- Macro runners
- Productivity tools
- In-app hotkey customization system

---

## ⚙️ Requirements

- **.NET Framework 4.5.1 or higher**
- Windows Forms-based application
- Visual Studio 2015 or later recommended

---

## 🔌 Getting Started

1. Add `CustomHotKeys.vb` to your project.
   
3. Use the included form (`Form1.vb`) or create your own UI.
   
5. On your main form (or any single form):
   - Override `WndProc` to listen for `WM_HOTKEY`
   - Assign `mainFormReference = Me` on form load


```vb
Protected Overrides Sub WndProc(ByRef m As Message)
    If m.Msg = WM_HOTKEY Then
        Dim id As Integer = m.WParam.ToInt32()
        If hotkeyIdMap.ContainsKey(id) Then
            hotkeyIdMap(id).Invoke()
        End If
    End If
    MyBase.WndProc(m)
End Sub
