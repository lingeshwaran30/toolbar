# Develop an Android Application Implementing AppBar (Toolbar) and Options Menu

[← Back to Index](README.md)

## Menus, Dialogs and UI Interaction

**Practical No.:** 1  
**Project Name:** `ToolbarMenuDemo`

## Aim

To develop an Android application implementing an AppBar (Toolbar) and Options Menu to provide navigation and menu item selection.

## I. Filename: `activity_main.xml`

**Location:** `app/src/main/res/layout/activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <!-- Toolbar -->
    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:title="Toolbar Demo"
        app:titleTextColor="@android:color/white" />

    <!-- Main Content -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="AppBar and Options Menu Example"
        android:textSize="22sp"
        android:padding="20dp" />

</LinearLayout>
```

## II. Create a Menu Resource Directory

1. Right-click the `res` folder.
2. Select **New → Android Resource Directory**.
3. Set **Directory name** to `menu`.
4. Set **Resource type** to `menu`.
5. Click **OK**.

## III. Filename: `menu_main.xml`

**Location:** `app/src/main/res/menu/menu_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<menu
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <item
        android:id="@+id/menu_home"
        android:title="Home"
        app:showAsAction="never" />

    <item
        android:id="@+id/menu_settings"
        android:title="Settings"
        app:showAsAction="never" />

    <item
        android:id="@+id/menu_about"
        android:title="About"
        app:showAsAction="never" />

    <item
        android:id="@+id/menu_logout"
        android:title="Logout"
        app:showAsAction="never" />

</menu>
```

## IV. Filename: `MainActivity.java`

**Location:** `app/src/main/java/com/example/toolbarmenudemo/MainActivity.java`

```java
package com.example.toolbarmenudemo;

import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.widget.Toast;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;

public class MainActivity extends AppCompatActivity {

    Toolbar toolbar;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        toolbar = findViewById(R.id.toolbar);

        // Set Toolbar as AppBar
        setSupportActionBar(toolbar);
    }

    // Create Options Menu
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    // Handle Menu Item Click
    @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        int id = item.getItemId();

        if (id == R.id.menu_home) {
            Toast.makeText(
                this, "Home Selected", Toast.LENGTH_SHORT
            ).show();

        } else if (id == R.id.menu_settings) {
            Toast.makeText(
                this, "Settings Selected", Toast.LENGTH_SHORT
            ).show();

        } else if (id == R.id.menu_about) {
            Toast.makeText(
                this, "About Selected", Toast.LENGTH_SHORT
            ).show();

        } else if (id == R.id.menu_logout) {
            Toast.makeText(
                this, "Logout Selected", Toast.LENGTH_SHORT
            ).show();

        } else {
            return super.onOptionsItemSelected(item);
        }

        return true;
    }
}
```

## Explanation

1. **Toolbar:** Displays the application title and acts as the AppBar.
2. **`setSupportActionBar(toolbar)`:** Sets the Toolbar as the activity's support action bar.
3. **Menu Resource Directory:** Stores the XML file defining the Options Menu.
4. **`menu_main.xml`:** Defines Home, Settings, About, and Logout menu items.
5. **`onCreateOptionsMenu()`:** Loads the menu items into the Toolbar's Options Menu.
6. **`onOptionsItemSelected()`:** Handles menu item selections.
7. **Toast:** Displays a short message when the user selects a menu item.

## Output

The application displays a Toolbar with the title **Toolbar Demo** and the main text **AppBar and Options Menu Example**.

When the user opens the three-dot Options Menu, the following items appear:

- Home
- Settings
- About
- Logout

Selecting any item displays its corresponding Toast message, such as "Home Selected" or "Settings Selected".

## Result

Thus, an Android application implementing an AppBar (Toolbar) and Options Menu was developed successfully.

## Important Setup Notes

- Ensure the Java package name matches your project's actual package name.
- The project must include the AndroidX AppCompat dependency.
- Use an AppCompat-compatible theme that does not provide a competing default ActionBar when using this Toolbar as the support ActionBar.
- The menu items currently display Toast messages; they do not navigate to other screens or perform an actual logout.
