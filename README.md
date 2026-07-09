# 🏨 Hotel Management System

A desktop hotel management application built with **JavaFX**. It provides a
simple tabbed interface to manage rooms, book guests into available rooms,
and check guests out — all with a dark, gold-accented UI theme.

## Features

- **Room Management** – Add rooms with a room number, type (Standard /
  Deluxe / Suite), and price. Rooms are displayed as styled cards showing
  live availability status.
- **Booking** – Select an available room from a dropdown, enter a guest
  name, and book it. Booked rooms are automatically removed from the
  available-rooms dropdown.
- **Checkout** – View all active bookings in a list and check out a
  selected guest, which frees up their room again.
- **Themed UI** – Custom dark gradient background, gold highlights, and
  styled buttons/cards via `style.css`.

## Project Structure

```
hotel-management-system/            (repo root)
├── Hotel_management/
│   ├── .vscode/
│   │   ├── launch.json             # VS Code run/debug configuration
│   │   └── settings.json           # Points VS Code to your JavaFX SDK jars
│   ├── Main.java                    # Application entry point + all UI logic
│   └── style.css                    # JavaFX stylesheet (dark theme, gold accents)
└── README.md
```

Important: Everything (the code, the .vscode config, and the
stylesheet) lives inside the Hotel_management folder — not in the
repo root. When you clone/download this repo, make sure you open the
Hotel_management folder itself in VS Code (File → Open Folder →
select Hotel_management), not the outer hotel-management-system
repo folder. Otherwise VS Code won't find .vscode/launch.json and the
"Run JavaFX" option won't appear.

## Prerequisites

You'll need the following installed **before** running this project:

| Requirement | Version | Notes |
|---|---|---|
| **JDK (Java Development Kit)** | 17 or newer | JavaFX 21 requires a reasonably recent JDK. [Download here](https://adoptium.net/) |
| **JavaFX SDK** | 21 | JavaFX is no longer bundled with the JDK — download separately from [gluonhq.com/products/javafx](https://gluonhq.com/products/javafx/) |
| **VS Code** | Latest | Your `.vscode` config files indicate this is being run through VS Code |
| **VS Code Extension: Extension Pack for Java** | Latest | Provides Java language support, debugging, and project management (search "Extension Pack for Java" by Microsoft in the Extensions tab) |

### JavaFX SDK setup (important)

Your config files currently point to:
```
C:/javafx-sdk-21/lib
```
This means:
1. Download the **JavaFX 21 SDK** (Windows version) as a zip.
2. Extract it so that the path `C:/javafx-sdk-21/lib` actually exists on
   your machine (i.e. extract directly to `C:\`, or update the paths in
   `.vscode/launch.json` and `.vscode/settings.json` to match wherever you
   extracted it).

If you're on **Mac or Linux**, update both `launch.json` and
`settings.json` to point to your actual JavaFX SDK `lib` folder instead of
the `C:/...` Windows path.

## Getting Started

1. **Install prerequisites** listed above.
2. **Clone or download** this project into a folder.
3. Make sure the folder structure looks like:
   ```
   your-project/
   ├── .vscode/
   │   ├── launch.json
   │   └── settings.json
   ├── Main.java
   └── style.css
   ```
4. Open the project folder in **VS Code**.
5. Confirm the Java and JavaFX paths in `.vscode/settings.json` and
   `.vscode/launch.json` match your actual JavaFX SDK install location.
6. Open `Main.java`, then either:
   - Click the **Run** ▶️ button above the `main` method, or
   - Go to **Run and Debug** (`Ctrl+Shift+D`) → select **"Run JavaFX"** →
     press Play.

### Running from the command line (alternative)

If you'd rather not use VS Code:

```bash
# Compile
javac --module-path "C:/javafx-sdk-21/lib" --add-modules javafx.controls,javafx.fxml Main.java

# Run
java --module-path "C:/javafx-sdk-21/lib" --add-modules javafx.controls,javafx.fxml Main
```
(Replace the module-path with your actual JavaFX `lib` folder location.)

## Usage

1. **Rooms tab** – Enter a room number and price, choose a room type, and
   click **Add Room**. It will appear as a card showing its status
   ("Available" in green).
2. **Booking tab** – Enter a guest name, pick an available room from the
   dropdown, and click **Book Room**. The room's status updates to
   "Booked" (shown in red on the Rooms tab).
3. **Checkout tab** – Select a booking from the list and click **Checkout
   Selected** to free up that room again.

## Troubleshooting

- **"Error: JavaFX runtime components are missing"** — This means the
  `--module-path` / `--add-modules` VM arguments aren't being applied.
  Double-check `.vscode/launch.json` has the correct path to your JavaFX
  `lib` folder, and that the file is valid JSON (no missing brackets).
- **UI shows up with no styling (no gold theme, no dark background)** —
  `style.css` isn't being found at runtime. Make sure it's in the same
  directory you're running the compiled `.class` file from, or update the
  path in `Main.java`'s `scene.getStylesheets().add("style.css")` call.
- **`settings.json` / `launch.json` "referencedLibraries" path not found`**
  — Update the `C:/javafx-sdk-21/lib/*.jar` path in both files to match
  wherever you actually extracted the JavaFX SDK.

## Tech Stack

- **Language:** Java
- **UI Framework:** JavaFX (Controls, FXML modules)
- **Styling:** JavaFX CSS
- **IDE:** VS Code with the Java Extension Pack

## Future Improvements

- Persist rooms/bookings to a database (e.g. SQLite/MySQL) instead of
  in-memory `ArrayList`s, so data isn't lost when the app closes.
- Add input validation (e.g. numeric-only price field, duplicate room
  number checks).
- Add a billing/invoice summary on checkout.
- Add search/filter for rooms by type or status.
