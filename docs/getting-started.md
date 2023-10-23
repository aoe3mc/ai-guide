# Getting Started

In this section, we will set up our environment to start making AI scripts.

## 1. Showing file extensions

Before we start, we need to make sure that file extensions are shown in the
file explorer.

=== "Windows 11"

    1. Press ++win+e++ to open the file explorer.
    2. Click on **View** at the top.
    3. Click on **Show**.
    4. Make sure **File name extensions** is checked.

=== "Windows 10 / 8.1 / 8"

    1. Press ++win+e++ to open the file explorer.
    2. Click on **View** at the top.
    3. Make sure **File name extensions** is checked.

=== "Windows 7"

    1. In the Start menu, type **folder options**.
    2. Click on **Folder Options**.
    3. Click on the **View** tab.
    4. Make sure **Hide extensions for known file types** is unchecked.

## 2. Enabling the AI Debugger

The AI Debugger will provide us with useful information about what's going on
in the AI script and in the AI's mind: what it sees, what it is currently
doing, etc.

1. Navigate to **User Folder > Startup**
2. Create a text file named **user.cfg**
3. Open it with your favorite text editor, paste the following lines
   and save:

```text title="user.cfg"
developer
aiDebug
showAIEchoes
```

## 3. Setting up a local mod

Since it is apparently not possible to load custom scripts made completely from
scratch in a scenario, we will have to set up a local mod to override one of the
default scripts.

1. Navigate to the **Local Mods Folder**.
2. Create a new folder with any name you want. This will be the name of the mod.
   In this guide, we will name it **Mods Guide AI**.
3. Inside the **Mods Guide AI** folder, create a folder named **Game**.
4. Inside the **Game** folder, create a folder named **AI**.

## 4. Creating and loading a script

### 4.1. For a custom scenario

#### 4.1.1. Creating a script

1. Navigate to **Mods Guide AI > Game > AI**.
2. Create a new text file named **Age3AI.xs**.
3. Open it with your favorite text editor, paste the following lines
   and save:

```cpp title="Age3AI.xs"
void main(void)
{
    aiEcho("The script is working!");
}
```

#### 4.1.2. Loading the script

1. Go to the scenario editor. For the purpose of this guide, we will generate a
   new scenario based on **New England**.

   1. At the top left, click on **File > New**.
   2. In the **Type** dropdown, select **new england**.
   3. Leave the rest of the settings as they are.
   4. Click on **Generate**.

2. At the top, click on **Scenario > Player Data**.
3. Under the **Control** column for the player you want to assign the script
   to, select **Computer**. In this guide, we will assign the script to
   all players.
4. Click on the **AI** button.
5. Find and select **AGE3AI.XS** in the list.
6. Click on **OPEN** at the bottom left.
7. In case the game says "Any unsaved progress will be lost. Continue?",
   click on **YES**.
8. Repeat steps 3 to 7 for all players.
9. Close the **Player Data** window.
10. Save the scenario as **AI Mods Guide Scenario**.

### 4.2. For a skirmish game

!!! warning "This will override the default AI script for all civilizations."

#### 4.2.1. Creating a script

1. Navigate to **Mods Guide AI > Game > AI**.
2. Create a new text file named **aiLoaderStandard.xs**.
3. Open it with your favorite text editor, paste the following lines
   and save:

```cpp title="aiLoaderStandard.xs"
void main(void)
{
    aiChat(1, "The script is working!");
}
```

#### 4.2.2. Loading the script

There's no need to load the script since it overrides the default **aiLoaderStandard.xs**.

## 5. Testing the script

### 5.1. For a custom scenario

1. In the main menu, click on **LOAD**.
2. In the dialog that appears, select **CUSTOM SCENARIO**.
3. Select **AI MODS GUIDE SCENARIO.AGE3YSCN**.
4. Click on **OPEN**.
5. Once in-game, press ++alt+q++ to open the AI Debugger.
6. If everything went well, you should see something like thos:

```text title="AI Debug Output"
00:00:00 (0): P#1 (Player 1) The script is working!
```

### 5.2. For a skirmish game

Just play a skirmish game as you normally would. If everything went well, AI
personalities should be chatting "The script is working!" at the start of the
game.

## 6. Conclusion

Congratulations! You have successfully created and loaded a custom AI script.
You can now start making your own AI scripts.
