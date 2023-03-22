# Active Directory Stress Test Script

This Python script is designed to stress test an Active Directory environment by creating a specified number of user accounts, adding them to specific groups, and generating logon events. It can be helpful in assessing the performance and stability of your Active Directory environment under load.

## Requirements

- Python 3.6 or later
- The following Python libraries:
  - `pyad`
  - `pypsrp`
  - `wmi`

To install the required libraries, run the following command:
'''powershell
python ad_stress_test.py
'''

## Modifiable Variables

There are no modifiable variables directly in the script. However, you can modify the input provided to the script to control the behavior:

- `domain_name`: Your domain name (e.g., example.local)
- `number_of_users`: The number of users to create
- `password`: The password for the new users

## How It Works

1. The script checks if it's running with administrative privileges. If not, it exits with an error message.
2. It prompts for the `domain_name`, `number_of_users`, and `password` from the user.
3. The script retrieves existing users that are members of the `StressTestAdmins` group.
4. It calculates the highest user number from the existing users.
5. The script creates the specified number of user accounts in the `Stress Test` OU, with usernames formatted as "userX", where X is an incremented number. It also sets the home directory, profile path, and adds the users to the `StressTestAdmins` and `Remote Desktop Users` groups.
6. After creating all the users, the script generates logon events for each existing user by running a PowerShell script that accesses the `C$` share of the local machine.
7. The script waits for all logon events to be generated and then exits.

## Usage

Run the script in a terminal or command prompt with administrative privileges:
'''powershell
python ida_stress_test.py
'''

Follow the prompts to enter your domain name, the number of users to create, and the password for the new users.


