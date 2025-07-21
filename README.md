<p align="center">
  <img src="./img/1751966323.png" alt="Procanchor Banner" width="500"/>
</p>

# ProcAnchor

**ProcAnchor** is a lightweight and powerful process supervision tool for Linux. It ensures that your application remains running by automatically restarting it after crashes, executable upgrades, or system reboots. A key feature of `ProcAnchor` is its ability to preserve the same Process ID (PID) for the supervisor process, providing stability for system integrations and management scripts.

## Features

*   **PID Preservation**: Maintains a consistent PID for the ProcAnchor process, simplifying integration with `systemd`, `upstart`, and other init systems.
*   **Automatic Restarts**: Monitors your application and automatically restarts it if it crashes or exits unexpectedly.
*   **Executable Upgrades**: Seamlessly handles upgrades of your application's executable without interrupting the ProcAnchor process.
*   **Minimalist Design**: Focuses on a core set of features, avoiding unnecessary bloat and complexity.
*   **User and Group Privilege Dropping**: Can drop root privileges for the supervised application, enhancing security.
*   **Cgroup-based Process Tracking**: Uses Linux Control Groups (cgroups) to reliably track the application's PID.

## Installation

To install `ProcAnchor`, you will need a C++ compiler and CMake.

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/xzero/ProcAnchor.git
    cd ProcAnchor
    ```

2.  **Create a build directory:**

    ```bash
    mkdir build
    cd build
    ```

3.  **Configure and build the project:**

    ```bash
    cmake ..
    make
    ```

4.  **Install the executable:**

    ```bash
    sudo make install
    ```

## Usage

```
procanchor: a process supervising tool
  (c) Suleman Arshad <algernonk4@gmail.com>

usage:
  procanchor [procanchor options] -- /path/to/app [app options ...]

options:
  -f, --fork              Fork procanchor into the background.
  -p, --pidfile=PATH      Location to store the current procanchor PID.
  -u, --user=NAME         Drop application user-privileges to the specified user.
  -g, --group=NAME        Drop application group-privileges to the specified group.
  -l, --delay-limit=N     Maximum delay (in seconds) to sleep between restarts. [Default: 80]
  -e, --restart-on-error  Restart the application on non-zero exit codes.
  -c, --restart-on-crash  Restart the application on crashes (e.g., SIGSEGV).
  -q, --quiet             Decrease verbosity level. Use -qq to suppress runtime errors.
  -v, --version           Print the program version and exit.
  -h, --help              Print this help message and exit.
```

## Examples

**Supervise a web server:**

```bash
sudo procanchor -- /usr/sbin/nginx -g "daemon off;"
```

**Supervise a background worker:**

```bash
sudo procanchor -p /var/run/my-worker.pid -- /usr/bin/my-worker
```

## License

This project is licensed under the MIT License.

