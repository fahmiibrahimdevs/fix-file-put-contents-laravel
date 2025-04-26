## Fix: `file_put_contents(...) Failed to open stream: Permission denied`
![image](https://github.com/user-attachments/assets/440d82eb-5c60-49e9-b75e-8d54c56f0e57)


This error usually occurs when your PHP application (e.g., Laravel) cannot write to the `storage` or `bootstrap/cache` directories due to insufficient permissions.

### Solution

Run the following commands in your project root to fix the issue:

```bash
cd /path/your/projects/

sudo chown -R $USER:www-data storage
sudo chown -R $USER:www-data bootstrap/cache

sudo chmod -R 775 storage
sudo chmod -R 775 bootstrap/cache
```

### Explanation
- `chown -R $USER:www-data`: Changes ownership of the directories to your current user and the web server group (www-data).
- `chmod -R 775`: Grants read, write, and execute permissions to the user and group, and read and execute to others.

### When to Use This
- After cloning a fresh repository
- After pulling updates from Git
- When deploying to a new server
- If you encounter permission-related errors during runtime

### Additional Tips
- Make sure your web server (Apache/Nginx) is running under the www-data group.
- You can automate this in your deployment scripts for consistency.
