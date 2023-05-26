# How-to-enable-auto-GPT-to-pick-up-where-it-left-off-after-connection-failure

# Import os module to work with files and directories
import os

# Define the path to the Auto-GPT folder
auto_gpt_path = "Auto-GPT"

# Define the path to the backupRestore.txt file
backup_restore_path = os.path.join(auto_gpt_path, "backupRestore.txt")

# Define the path to the logs folder
logs_path = os.path.join(auto_gpt_path, "logs")

# Define the path to the activity.txt file
activity_path = os.path.join(logs_path, "activity.txt")

# Check if the backupRestore.txt file exists
if os.path.exists(backup_restore_path):
    # Open the backupRestore.txt file in append mode
    backup_restore_file = open(backup_restore_path, "a")
else:
    # Create and open the backupRestore.txt file in write mode
    backup_restore_file = open(backup_restore_path, "w")

# Check if the activity.txt file exists
if os.path.exists(activity_path):
    # Open the activity.txt file in read mode
    activity_file = open(activity_path, "r")
    # Read the last line of the activity.txt file
    last_line = activity_file.readlines()[-1]
    # Write the last line to the backupRestore.txt file
    backup_restore_file.write(last_line)
    # Close the activity.txt file
    activity_file.close()
else:
    # Print an error message
    print("The activity.txt file does not exist.")

# Close the backupRestore.txt file
backup_restore_file.close()
