import os

def rename_files(directory_path, prefix, extension):
    try:
        # Ensure the provided directory exists
        if not os.path.exists(directory_path):
            print(f"Directory '{directory_path}' does not exist.")
            return
        
        # List all files in the directory
        files = os.listdir(directory_path)
        
        for index, file_name in enumerate(files):
            if os.path.isfile(os.path.join(directory_path, file_name)):
                new_name = f"{prefix}_{index + 1}.{extension}"
                os.rename(os.path.join(directory_path, file_name), os.path.join(directory_path, new_name))
                print(f"Renamed '{file_name}' to '{new_name}'")
        
        print("File renaming completed.")
    
    except Exception as e:
        print(f"An error occurred: {str(e)}")

if __name__ == "__main__":
    directory_path = input("Enter the directory path: ")
    prefix = input("Enter the prefix for the new filenames: ")
    extension = input("Enter the file extension (e.g., 'txt', 'jpg'): ")
    
    rename_files(directory_path, prefix, extension)
