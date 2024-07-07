# How to Kill a Process Running on a Specific Port

_Last Updated: 2024-07-07_

In Linux, processes utilize ports for network communication. When a process occupies a port, it prevents others from using it. This guide demonstrates how to terminate such processes.

**Identifying and Terminating the Process**

1.  **Find the Process ID (PID):**

    - Use the `lsof` command (or alternatively, `fuser`) to identify the PID:

    Bash

    ```
    lsof -t -i:<port_number>  # Replace <port_number> with the actual port

    ```

    This command lists processes using the specified port, revealing their PIDs.

2.  **Terminate the Process:**

    - Employ the `kill` command with the `SIGKILL` signal (-9) to forcefully terminate the process:

    Bash

    ```
    sudo kill -9 <PID>  # Replace <PID> with the identified PID from step 1

    ```

**Combined Command (Optional):**

Combine `lsof` and `kill` for a single-step approach:

Bash

```
sudo kill -9 $(sudo lsof -t -i:<port_number>)

```

**Conclusion**

By following these steps, you can effectively terminate processes occupying specific ports in Linux, freeing them for other applications. This skill proves valuable for developers and system administrators managing network services.
