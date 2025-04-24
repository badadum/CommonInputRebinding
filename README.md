## Setting up Common UI

### Minimum Setup

To use **Common UI** with this plugin, follow these steps:

1. **Enable the Common UI Plugin**  
2. **Set your viewport to support Input Routing**
3. **Create `ControllerDataBrushHelper` assets** and assign them to specific types of controllers on specific platforms

### Optional Setup

- **Create Input Action Data Tables**  
  Map controller buttons to actions within your UI.

- **Set up Default Navigation Actions**  
  Support global click and back button functionality.

### More Information

More detailed information on using Common UI can be found in the Epic Documentation:  
**[Common UI Plugin for Advanced User Interfaces in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community](https://dev.epicgames.com/documentation/en-us/unreal-engine/common-ui-plugin-for-advanced-user-interfaces-in-unreal-engine)**

**Enabling the Common UI Plugin:**  
From the editor toolbar, select `Edit -> Plugins`, then search for **Common UI**, enable the plugin, and restart the editor.
![Screenshot 2025-04-24 084151](https://github.com/user-attachments/assets/8279ec6f-cbf7-4c9a-8816-c8c3b8a8ff73)
## Viewport Input Routing Setup

The **Viewport** is the base for all input routing in Common UI. When Common UI captures input, it sends it to the Viewport first, which then forwards it to the root node that is currently drawn on top. To support this functionality, perform the following setup steps:

1. Open `Edit > Project Settings > Engine > General Settings`
2. Set your **Game Viewport Client Class** to `CommonGameViewportClient`

---

## Controller Data Binding (Platform-Specific UI Elements)

**Controller Data Assets** associate key-actions with UI elements. Each asset is tied to an input type, gamepad, and platform. Common UI uses this data to automatically display the correct platform-specific UI elements depending on the current platform and input type.

Optionally, for platforms supporting multiple input types or unique gamepads, the system can dynamically switch the UI elements based on the user's input.

To expose controller images to the widget, this plugin uses a subclass called `ControllerDataBrushHelper`.

### Steps to Create a `ControllerDataBrushHelper` Asset:

1. Right-click in the **Content Browser** and select **Blueprint Class**
2. Search for `ControllerDataBrushHelper` and click **Select** to create the asset
3. Populate the asset with appropriate images and metadata for one of the controllers you plan to support
![Screenshot 2025-04-24 084328](https://github.com/user-attachments/assets/f6d37707-83f4-49d3-89e7-e5319712cfe8)
![Screenshot 2025-04-24 084353](https://github.com/user-attachments/assets/7b2a103e-c8dc-4210-8b18-6da07ed4f3c8)
Once you have created `ControllerData` for all input types you plan to support, you must assign them to their associated platforms:

1. Open `Project Settings > Game > Common Input Settings > Platform Input`
2. Add each `ControllerDataBrushHelper` class to the corresponding platform and input type
![Screenshot 2025-04-24 084450](https://github.com/user-attachments/assets/a2060fbe-79f5-4bbe-8476-cbaa8f79a07f)
## Common UI Widget Library and Widget Styling

Common UI includes a library of widgets, found under the **Common UI Plugin** section in UMG's **Palette**. These widgets offer commonly used UI functionality for games and applications, including:

- Specialized text blocks for displaying **dates**, **times**, and **numeric values**
- Navigation aids like **carousels** and **animated switchers**
- Platform aids such as a **loading guard** and **hardware visibility border**
- Basic widgets like **buttons** and **text blocks** that use style data assets for consistent styling

Unlike base UMG widgets, these Common UI widgets do not include individual styling options. Instead, they reference **Common Style Assets**, allowing you to maintain consistent visuals across all menus and HUDs. Updates to a style asset automatically affect every Common UI widget that uses it.

### Creating a Common Style Asset

1. Right-click in the **Content Browser**
2. Select **Blueprint Class**
3. Choose a class based on one of the `Common Style` types as the base


![Screenshot 2025-04-24 084535](https://github.com/user-attachments/assets/5969bec7-6da1-4082-849d-31dcc655327b)

2. Populate its **Details** panel with the styling information you want to apply to Common UI widgets.  
   These settings typically mirror the styling options found on standard UMG widgets.

![Screenshot 2025-04-24 084604](https://github.com/user-attachments/assets/70a58366-f36a-4414-b5ae-0c3ce7e6c125)

 Assign the style asset to a **Common UI widget** of the appropriate type.  
   For example, if you create a `Common Text Style` asset, assign it to the **Style** field in a `Common Text` widget.

   
![Screenshot 2025-04-24 084644](https://github.com/user-attachments/assets/b92fdba2-d1e4-482e-8baf-acccc644a6dd)

You can also assign style assets to the **Template Styles** section in  
`Project Settings > Plugins > Common UI Editor`.


![Screenshot 2025-04-24 084712](https://github.com/user-attachments/assets/fde9003b-9a9e-4865-9621-9c26d29110cb)

Any **Common UI widgets** that do not have a manually assigned style will automatically use the appropriate **Template Style** instead.  
This makes it easy to define a global default style for your application.

The `Project Settings > Plugins > Common UI Framework` menu includes several additional global assets, such as:

- **Default Throbber Material** – used in loading screens
- **Default Image Resource Object** – shown as a placeholder for UI assets that haven't been loaded

![Screenshot 2025-04-24 084732](https://github.com/user-attachments/assets/a3dc2ae4-42f1-4427-9bf8-3448af3d5cfb)


