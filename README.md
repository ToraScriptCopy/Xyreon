
# Xyreon UI Library v3.0 - API Reference

Official documentation for the Xyreon UI Library. This guide provides a comprehensive overview of all available methods and parameters for interface development.

---

## Core API

Methods for managing the library lifecycle and window creation.

### Library:Init()
Initializes and displays the user interface.
- **Note:** This must be called exactly once after all windows, tabs, and elements have been configured.

### Library:CreateWindow(options)
Creates a new root window object. Returns a Window object.

**Parameters (options):**
| Key | Type | Description |
| :--- | :--- | :--- |
| **Title** | string | (Required) The window title. |
| **Tag** | string | (Optional) A small label displayed next to the title. |
| **Tabs** | table | (Optional) An array of strings defining tab names. |

### Library:Close()
Toggles the global visibility of all library windows.

---

## Key System

### Library:CreateKeyDialog(options)
Creates a modal authentication window. Returns a dialog object with :Show() and :Hide() methods.

**Parameters (options):**
| Key | Type | Description |
| :--- | :--- | :--- |
| **Title** | string | Window title. Defaults to "Authentication Required". |
| **CheckKey** | function | A predicate function to verify the key. Takes a key (string) and must return a boolean. Supports asynchronous calls. |
| **OnSuccess** | function | Callback executed after successful authentication. |
| **OnFailure** | function | Callback executed after 3 failed attempts. Defaults to kicking the player. |

---

## Tabs Management

If a window is created with the Tabs parameter, use the :Tab(tabName) method to add elements to specific pages.

### window:Tab(tabName)
Returns the interface for adding elements to the specified tab.
- **tabName** (string): The name of the tab, which must exist in the initial Tabs array.
