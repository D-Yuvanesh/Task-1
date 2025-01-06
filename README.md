Here's an example program for file management in Python. This program provides a menu to perform tasks like listing, creating, renaming, moving, or deleting files and directories.

Python Code: File Management Tool

import os
import shutil

def list_files_and_directories(path):
    print("\nContents of the directory:")
    for item in os.listdir(path):
        print(f"- {item}")

def create_file(path):
    filename = input("Enter the file name to create: ")
    full_path = os.path.join(path, filename)
    with open(full_path, 'w') as file:
        file.write("")
    print(f"File '{filename}' created successfully!")

def create_directory(path):
    dirname = input("Enter the directory name to create: ")
    full_path = os.path.join(path, dirname)
    os.makedirs(full_path, exist_ok=True)
    print(f"Directory '{dirname}' created successfully!")

def rename_item(path):
    old_name = input("Enter the name of the file/directory to rename: ")
    new_name = input("Enter the new name: ")
    old_path = os.path.join(path, old_name)
    new_path = os.path.join(path, new_name)
    os.rename(old_path, new_path)
    print(f"Renamed '{old_name}' to '{new_name}'!")

def delete_item(path):
    name = input("Enter the name of the file/directory to delete: ")
    full_path = os.path.join(path, name)
    if os.path.isfile(full_path):
        os.remove(full_path)
        print(f"File '{name}' deleted!")
    elif os.path.isdir(full_path):
        shutil.rmtree(full_path)
        print(f"Directory '{name}' deleted!")
    else:
        print(f"'{name}' does not exist!")

def main():
    path = input("Enter the directory path to manage: ")
    if not os.path.exists(path):
        print("Invalid path!")
        return

    while True:
        print("\nFile Management Tool")
        print("1. List files and directories")
        print("2. Create a file")
        print("3. Create a directory")
        print("4. Rename a file/directory")
        print("5. Delete a file/directory")
        print("6. Exit")
        
        choice = input("Enter your choice (1-6): ")
        
        if choice == '1':
            list_files_and_directories(path)
        elif choice == '2':
            create_file(path)
        elif choice == '3':
            create_directory(path)
        elif choice == '4':
            rename_item(path)
        elif choice == '5':
            delete_item(path)
        elif choice == '6':
            print("Exiting the program. Goodbye!")
            break
        else:
            print("Invalid choice! Please try again.")

if __name__ == "__main__":
    main()

Features:

1. Lists files and directories in a given path.


2. Creates new files or directories.


3. Renames files or directories.


4. Deletes files or directories.


5. User-friendly menu for navigation.



Usage:

1. Copy the code into a .py file, e.g., file_manager.py.


2. Run the program:

python file_manager.py


3. Follow the menu prompts to perform file management tasks.



Let me know if you need modifications!

