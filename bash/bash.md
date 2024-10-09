# Resources

- https://www.youtube.com/watch?v=2733cRPudvI&list=PLT98CRl2KxKGj-VKtApD8-zCqSaN2mD4w&pp=iAQB

# `chmod`

Change user permissions.

The following adds the execute (`x`) permission to the file, allowing it to be run as a script.

```bash
chmod +x create_directory.sh
```

After running this command, you (and other users) will be able to execute the script by declaring the location of the script. For example:

```bash
./create_directory.sh
```

# Variables

The following creates a subshell. Allows you to run a command in the background.

```bash
files=$(ls)
```

Call variables by appending with `$`.

System environment variables are in ALL CAPS. to find the list of all these variables and values, type: `env`.

# Create New Directory

```bash
mkdir hello_world
```

# Navigate Through Directories

```bash
cd ~/Documents/hello_world
```

# Navigate One Level Back

```bash
cd ..
```

# Print Working Directory

```bash
pwd
```

# Command-Line History

```bash
history
```

# Rerun Command by Number

```
!499
```

# List Directory Contents

```bash
ls
```

# Create Single File

```bash
touch file.txt
```

# Show File Path

```bash
readlink -f file.txt
```

# List Boot Options and Order

```bash
sudo efibootmgr
```

# Set Environment Variable in Shell

```bash
export SECRET_KEY=your_secret_key_here
```