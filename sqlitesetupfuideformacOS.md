import streamlit as st

def app_intro():
    st.title("SQLite Setup Guide for macOS")
    st.write("""
    Welcome to the SQLite Setup Guide for macOS! This guide will walk you through the process of setting up SQLite on macOS 10.15.7 using precompiled binaries. 
    You'll learn how to download, extract, and run SQLite, as well as how to handle common issues related to macOS security settings.
    """)

def download_and_extract():
    st.header("Step 1: Download and Extract SQLite Tools")
    st.write("""
    1. **Download the SQLite Precompiled Binaries**: 
       - Visit the [SQLite download page](https://www.sqlite.org/download.html) and download the `sqlite-tools-osx-x64-3460100.zip`.
    2. **Locate the Downloaded File**:
       - The file will be in your `Downloads` folder, named `sqlite-tools-osx-x64-3460100.zip`.
    3. **Extract the Contents**:
       - Double-click the file to extract it. This will create a folder with the extracted tools.
    """)

def terminal_commands():
    st.header("Step 2: Run SQLite in Terminal")
    st.write("""
    1. **Open Terminal**:
       - Search for Terminal in Spotlight (press `Cmd + Space`, type `Terminal`, and press Enter).
    2. **Navigate to the Directory**:
       - Use the following command to navigate to the directory where you extracted the SQLite tools:
       ```bash
       cd ~/Downloads/sqlite-tools-osx-x64-3460100
       ```
    3. **Run SQLite**:
       - Try running the `sqlite3` command:
       ```bash
       ./sqlite3
       ```
    4. **Handle Security Warning**:
       - If you see a message saying "sqlite3 cannot be opened because the developer cannot be verified," proceed to the next step.
    """)

def bypass_security():
    st.header("Step 3: Bypass macOS Security")
    st.write("""
    To allow the `sqlite3` binary to run, follow one of these methods:

    **Method 1: Using the `xattr` Command**
    - Remove the quarantine attribute with this command:
    ```bash
    xattr -d com.apple.quarantine sqlite3
    ```

    **Method 2: Using the `spctl` Command**
    - Disable Gatekeeper checks for this binary:
    ```bash
    spctl --add --label "SQLite3" ./sqlite3
    spctl --enable --label "SQLite3"
    ```

    **Method 3: Using Finder**
    - Navigate to the folder where `sqlite3` is located.
    - Right-click on the `sqlite3` binary and select `Open`.
    - Confirm you want to open the file when prompted.
    """)

def main():
    app_intro()
    download_and_extract()
    terminal_commands()
    bypass_security()

if __name__ == "__main__":
    main()
