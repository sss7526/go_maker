# Go Project Template with Makefile Automation

A template repository for automating Go project setup and management using a powerful `Makefile`. This repository simplifies the initialization of new Go projects, automatically generating a Hello World program and a test file, managing Go modules, and reinitializing the Git repository to unlink from the upstream template.

This setup is ideal for developers looking for a streamlined, repeatable workflow to bootstrap and manage Go projects.

---

## Features
- **Automated Go Installation**: Installs latest Go version, updates, and uninstalls as desired.
- **Automated Go Module Initialization**: Creates a `go.mod` file with the project name pre-configured.
- **Template Program**: Automatically generates a `main.go` file with a Go "Hello, World!" program.
- **Test File Generation**: Sets up a `main_test.go` file with a basic Go test to validate the Hello World program.
- **Git Reinitialization**: Automatically unlinks the `.git` directory from the original upstream template repository, initializing a fresh Git repository.
- **Idempotent Workflows**: Ensures that rerunning commands does not overwrite existing user-customized files or disrupt Git history.

---

## Initial Workflow

To get started, follow these steps:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/sss7526/go_maker.git
   ```
   Replace `<your-new-project-name>` with the desired name of your new project.

2. **Rename and Navigate:**
   ```bash
   mv go_maker <your-new-project-name>
   cd <your-new-project-name>
   ```

3. **Install Go (if not already installed):**
   Run the following command to ensure the latest version of Go is installed on your system:
   ```bash
   make install
   ```

4. **Initialize Your New Project:**
   Use the `mod-init` command to initialize your project:
   ```bash
   make mod-init
   ```
   This will:
   - Generate a `go.mod` file with your project's name.
   - Create a `main.go` file with a Hello World program.
   - Generate a `main_test.go` file to test the Hello World program.
   - Reinitialize the Git repository, unlinking it from the upstream template and starting with a fresh commit history.

You’re now ready to start building your Go project!

---

## Makefile Commands

The repository's Makefile provides several commands to manage and maintain the project. Below is a summary of the most notable commands: ```make help```

```plaintext
========================================================================================================

                   ██████╗  ██████╗       ███╗   ███╗ █████╗ ██╗  ██╗███████╗██████╗
                  ██╔════╝ ██╔═══██╗      ████╗ ████║██╔══██╗██║ ██╔╝██╔════╝██╔══██╗
                  ██║  ███╗██║   ██║█████╗██╔████╔██║███████║█████╔╝ █████╗  ██████╔╝
                  ██║   ██║██║   ██║╚════╝██║╚██╔╝██║██╔══██║██╔═██╗ ██╔══╝  ██╔══██╗
                  ╚██████╔╝╚██████╔╝      ██║ ╚═╝ ██║██║  ██║██║  ██╗███████╗██║  ██║
                   ╚═════╝  ╚═════╝       ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝

========================================================================================================
                              COMMANDS FOR GO PROJECT MANAGEMENT
========================================================================================================
     SOURCE: https://github.com/sss7526/go_maker

  🛠  SETUP AND MAINTENANCE:
      install       Install the latest Go version (if not installed).
      update        Update Go to the latest version (if needed).
      uninstall     Remove the currently installed Go version.

  📦 MODULE MANAGEMENT:
      mod-init      Initialize a new Go module in the current directory.
      mod-tidy      Ensure go.mod and go.sum are in a tidy state.
      mod-update    Update all project dependencies to their latest versions.

  🔍 CODE QUALITY & SECURITY:
      format        Format Go files to a consistent standard (via gofmt).
      lint          Perform rigorous code linting with golangci-lint.
      vulncheck     Analyze dependencies for vulnerabilities (via govulncheck).

  📖 MISCELLANEOUS:
      run           Run the project's main entry point (main.go)
      test          Run all tests recursively across all packages.
      build         Build the project and output the binary to ~/.local/bin/go_maker.
      ex            Execute the built binary.
      tree          Generate a directory structure summary and save it to tree.txt.
      clean         Remove the compiled binary from ~/.local/bin/.
      help          Display this help screen.

========================================================================================================
                                 INFO: Use 'make <target>' to run a command.
========================================================================================================
```

### Setup and Initialization

| Command          | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `make install`    | Installs the latest version of Go if it’s not already installed locally.   |
| `make mod-init`   | Initializes a new Go project, generates boilerplate code, and reinitializes Git. |

### Module Management

| Command          | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `make mod-init`   | Initializes a new Go module (`go.mod`).                                     |
| `make mod-tidy`   | Ensures `go.mod` and `go.sum` are in a tidy, consistent state.              |
| `make mod-update` | Updates all project dependencies to their latest compatible versions.       |

### Code Quality and Security

| Command          | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `make format`     | Formats Go files using `gofmt`.                                             |
| `make lint`       | Performs static analysis and linting with `golangci-lint`.                  |
| `make vulncheck`  | Checks for vulnerabilities in dependencies using `govulncheck`.             |

### Build, Test, and Run

| Command          | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `make build`      | Builds the Go project and places the binary in `~/.local/bin/<project-name>`.|
| `make run`        | Runs the `main.go` file of the project.                                     |
| `make test`       | Executes tests recursively (`go test ./...`).                               |

---

## Output Example (For `make mod-init`)

Here’s an example of the terminal output when running `make mod-init`:

```plaintext
Initializing Go module with name: my-project...
go.mod created.
Creating main.go with a Hello World program...
main.go created.
Creating main_test.go with a basic test...
main_test.go created.
The repository is currently linked to the template upstream (https://github.com/sss7526/go_maker.git).
Resetting .git and initializing a new Git repository...
Git repository has been reset and initialized.
```

This clear, color-coded output ensures a seamless and intuitive experience.

---

## File Structure

After running `make mod-init`, your project will have the following structure:

```plaintext
<project-name>/
├── Makefile
├── go.mod
├── main.go
├── main_test.go
├── .gitignore
└── .git/
```

---

## Adding Your First Commit

After running `make mod-init`, you will have your project's Git repository initialized with an empty commit history. To create your first commit, do the following:

```bash
git add .
git commit -m "Initial commit"
```

If you want to link your project to a remote repository, run:

```bash
git remote add origin <your-new-repository-url>
git push -u origin main
```

---

## Contributing

Contributions to this repository are welcome! If you have suggestions, feature requests, or improvements, please submit an issue or create a pull request.

---

## License

This project is licensed under the [MIT License](./LICENSE).

---

## Acknowledgments

This repository was designed with the goal of simplifying Go project workflows. Inspired by common challenges when bootstrapping new projects, the Makefile ensures repeatable, intuitive automation for both new and experienced developers. 
