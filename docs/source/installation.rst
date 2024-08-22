Installation
=====


To use Napari Stereotyping, first install it creating a Conda environment:

.. code-block:: console

    conda create -n napari_stereotyping python=3.11

Then install Napari and the plugin:

.. code-block:: console

   pip install "napari[all]"

.. code-block:: console

   pip install napari-stereotyping

Creating a Launcher
====================

After installing Napari Stereotyping, you may want to create a desktop launcher for easy access. Below are instructions for creating a launcher on Linux, macOS, and Windows.

Linux
-----

To create a launcher on Linux, follow these steps:

1. **Create a `.desktop` File**:

   Navigate to the directory where you want to create the launcher and create a `.desktop` file (e.g., `napari_stereotyping.desktop`).

   .. code-block:: bash

      touch ~/Desktop/napari_stereotyping.desktop

2. **Edit the `.desktop` File**:

   Open the file in a text editor and add the following content:

   .. code-block:: ini

      [Desktop Entry]
      Version=1.0
      Type=Application
      Name=Napari Stereotyping
      Exec=gnome-terminal -- bash -c "source ~/.bashrc && mamba activate <your_conda_environment> && napari --with napari_stereotypage; exec bash"
      Icon=/path/to/your/icon/Image_accueil.png
      Terminal=true
      Comment=Launch Napari with the Stereotyping plugin
      Categories=Science;Graphics;

   Replace `<your_conda_environment>` with the name of your Conda environment, and `/path/to/your/icon/` with the path where your icon is stored.

3. **Make the File Executable**:

   Make sure the `.desktop` file is executable:

   .. code-block:: bash

      chmod +x ~/Desktop/napari_stereotyping.desktop

4. **Move to Applications** (optional):

   You can move the file to your applications directory to make it available in your system’s application menu.

   .. code-block:: bash

      mv ~/Desktop/napari_stereotyping.desktop ~/.local/share/applications/

macOS
-----

To create a launcher on macOS:

1. **Create an Automator Application**:

   - Open Automator from your Applications folder.
   - Select "Application" as the document type.
   - In the search bar, find and add "Run Shell Script" to the workflow.
   - Replace the default script with the following:

   .. code-block:: bash

      /path/to/conda/envs/napari_stereotyping/bin/napari --with napari_stereotypage

   Replace `/path/to/conda/envs/napari_stereotyping/bin/napari` with the path to your Napari installation.

2. **Save the Application**:

   - Save the Automator application with a name like "Napari Stereotyping" in your Applications folder.
   - You can now launch Napari Stereotyping directly from the Applications folder.

Windows
-------

To create a shortcut on Windows:

1. **Create a Shortcut**:

   - Right-click on your desktop and choose "New > Shortcut."
   - For the location, enter the path to your Napari executable:

   .. code-block:: text

      C:\Users\YourUsername\Miniconda3\envs\napari_stereotyping\Scripts\napari.exe --with napari_stereotypage

   - Click "Next" and give your shortcut a name, like "Napari Stereotyping."

2. **Set an Icon** (optional):

   - Right-click the shortcut and select "Properties."
   - Under the "Shortcut" tab, click "Change Icon" and choose an icon file if desired.

3. **Place the Shortcut in the Start Menu** (optional):

   - To add the shortcut to the Start Menu, move the shortcut to the following folder:

   .. code-block:: text

      C:\ProgramData\Microsoft\Windows\Start Menu\Programs

This will create a launcher on your system for Napari Stereotyping, making it easier to access the application directly from your desktop or start menu.
