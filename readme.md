# Jupyter Notebook with IRuby Kernel

This README provides instructions for setting up and running Jupyter Notebook with the IRuby kernel.

## Using Visual Studio Code Dev Containers

This setup works seamlessly with Visual Studio Code Dev Containers, allowing you to develop in a consistent and isolated environment.

### Steps to Use Dev Containers

1. **Install Prerequisites**:
   - Ensure you have [Visual Studio Code](https://code.visualstudio.com/) installed.
   - Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers).

2. **Clone the Repository**:
   Clone your project repository if you haven’t already:

   ```bash
   git clone https://github.com/JuanPabloGil/Jupyter-Ruby-DevContainer.git
   cd <your-repository-folder>
   ```


#### Open in Dev Container:

Open the folder in Visual Studio Code.

When prompted, click Reopen in Container. If not prompted, use the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P` on macOS) and select Remote-Containers: Reopen in Container.

Build and Register the IRuby Kernel: Inside the Dev Container terminal, run:
```bash
iruby register --force
```

Start the Jupyter Notebook Server: Start the server with:
```bash
jupyter notebook --ip 0.0.0.0 --port 8888 --no-browser --allow-root
```

Select the IRuby Kernel: Once the notebook interface is open in your browser, choose the IRuby kernel from the kernel selection menu.
