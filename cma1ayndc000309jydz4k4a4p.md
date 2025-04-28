---
title: "Don't create virtual environment python in 2025"
seoTitle: "Skip Virtual Environments in Python 2025"
seoDescription: "Discover how the 'uv' tool is transforming Python project management by automating virtual environments and simplifying dependency handling"
datePublished: Mon Apr 28 2025 16:38:32 GMT+0000 (Coordinated Universal Time)
cuid: cma1ayndc000309jydz4k4a4p
slug: dont-create-virtual-environment-python-in-2025
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1745858054045/c195aa00-d21b-4060-ba2e-30dde566560f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1745858245335/a7ac2e8c-49fc-4702-aba4-f5c3331bfcb7.png
tags: python, npm, fastapi, uv, python-venv

---

For years, the first step in any Python project, big or small, has often been the same opening your terminal and typing something like `python -m venv venv` . This manually creating virtual environments has become so ingrained that it feels like a mandatory part of the Python development lifecycle. But what if I told you that in the near future, this step could become a thing of the past?

---

## *Inroduction of uv*

An extremely fast Python package and project manager, written in Rust. [**uv**](https://docs.astral.sh/uv/) **is presented as a modern tool that aims to revolutionize the way you manage *Python projects and their dependencies.*** It introduces a new ecosystem for Python project management that is designed to be more organized and efficient.

---

## *Uv features*

uv provides essential features for Python development — from installing Python and hacking on simple scripts to working on large projects that support multiple Python versions and platforms. When you come from the JavaScript ecosystem, it is similar to npm.

uv's interface can be broken down into sections, which are usable independently or together.

1. ### Python versions
    
    Installing and managing Python itself.
    
    * `uv python install`: Install Python versions.
        
    * `uv python list`: View available Python versions.
        
    * `uv python find`: Find an installed Python version.
        
    * `uv python uninstall`: Uninstall a Python version.
        
    
2. ### Scripts
    
    Executing standalone Python scripts, e.g., [`example.py`](http://example.py).
    
    * `uv run`: Run a script.
        
    * `uv add --script`: Add a dependency to a script
        
    * `uv remove --script`: Remove a dependency from a script
        
    
3. ### Projects
    
    Creating and working on Python projects, i.e., with a `pyproject.toml`.
    
    * `uv init`: Create a new Python project.
        
    * `uv add`: Add a dependency to the project.
        
    * `uv remove`: Remove a dependency from the project.
        
    * `uv run`: Run a command in the project environment.
        
    * `uv build`: Build the project into distribution archives.
        
    

---

## *Practical use case*

One of the most significant shifts uv introduces is the **automatic creation of virtual environments** . Forget the manual steps of using **venv** or **other tools**. uv handles this for you the moment you run your first script in a project.

Let's dive into some practical examples to see uv in action.

**Working with Python Projects:** Imagine you're starting a new web project. Traditionally, you would do something like this:

```bash
python -m venv .venv

source .venv/bin/activate  # On macOS/Linux

.venv\Scripts\activate  # On Windows

pip install <your_dependencies>
```

### **Working on Python Projects with**

For larger Python projects, uv offers a project structure managed through a `pyproject.toml` file, which is similar to `package.json` in JavaScript.

1. **Initializing a Project :**
    
    To start a new project with uv, go to your project directory in the terminal and run:
    
    ```bash
    uv init <project_name>
    ```
    
    For example:
    
    ```bash
    uv init example-app
    ```
    
    The project includes a `pyproject.toml`, a sample file ([`main.py`](http://main.py)), a readme, and a Python version pin file (`.python-version`).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1745854929739/660b495e-9f71-4376-9b48-9ae7a867de56.png align="center")
    
    The `pyproject.toml` includes basic metadata. It does not include a build system, it is not a package and will not be installed into the environment:
    
    ```ini
    # pyproject.toml
    [project]
    name = "example-app"
    version = "0.1.0"
    description = "Add your description here"
    readme = "README.md"
    requires-python = ">=3.13"
    dependencies = []
    ```
    
    The sample file defines a `main` function with some standard boilerplate:
    
    ```python
    # main.py
    def main():
        print("Hello from example-app!")
    
    if __name__ == "__main__":
        main()
    ```
    
    Python files can be executed with `cd example-app <project_name>` after run this cmd `uv run main.py`:
    
    ```bash
    # output
    Hello from example-app!
    ```
    
2. **Adding Dependencies :**
    
    To add dependencies to your project, you can update the `dependencies` list in the `pyproject.toml` file. This is similar to adding packages in a `package.json` file in JavaScript. Once you have added your dependencies, make sure to run the appropriate command to install them in your environment.
    
    **use the** `uv add` **command followed by the package names.**
    
    ```bash
    uv add fastapi
    ```
    
    This command not only installs the fastapi package and its dependencies but also automatically updates your pyproject.toml file to include fastapi under the \[tool.uv.dependencies\] section. For example, after adding fastapi, your pyproject.toml might look like this:
    
    ```ini
    [project]
    name = "example-app"
    version = "0.1.0"
    description = "Add your description here"
    readme = "README.md"
    requires-python = ">=3.13"
    dependencies = [
        "fastapi>=0.115.12", # added fastapi package sucessfully
    ]
    ```
    
    A `uv.lock` file (similar to `package-lock.json`) is also created to **ensure consistent dependency versions** **across different environments**. You generally shouldn't edit this file directly.
    

---

*<mark>Example Code with FastAPI :</mark>*

```python
from typing import Union

from fastapi import FastAPI
import uvicorn

def main():
    print("Hello from uv-python-no-create-venv!")
    uvicorn.run("main:app", port=5000, log_level="info")

app = FastAPI()

@app.get("/")   
def read_root():    
    return {"Hello": "World"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}

if __name__ == "__main__":
    main()
```

To run this **FastAPI application** (assuming you have uvicorn installed, which you can add using `uv add uvicorn`), you can use a command like:

```bash
uv run main.py --app main:app --reload
```

---

### **Building a Distributable Package** Using `uv build`

To distribute your project to others (e.g. to upload it to an index like PyPI), you'll need to build it into a distributable format.

Python projects are typically distributed as both source distributions (sdists) and binary distributions (wheels). The former is typically a `.tar.gz` or `.zip` file containing the project's source code along with some additional metadata, while the latter is a `.whl` file containing pre-built artifacts that can be installed directly.

```bash
uv build
ls dist/
```

You can build the project in a different directory by providing a path to `uv build`, e.g., `uv build path/to/project`.

`uv build` will first build a source distribution, and then build a binary distribution (wheel) from that source distribution.

---

### **Conclusion**

In summary, uv revolutionizes Python project management by automating virtual environments and simplifying dependency handling, making development more efficient and organized.

If you found this blog post helpful, please consider sharing it with others who might benefit. You can also follow me for more content on Python, Fastapi , JavaScript, React.js, Next.js and other **web Development** and **AI topics**.

For *Paid collaboration*, *Web Development, AI Agent freelancing* *work*, mail me at: [**krishdesai044@gmail.com**](mailto:krishdesai044@gmail.com)

Connect with me on [**Twitter**](https://x.com/DKB972), [**LinkedIn**](https://www.linkedin.com/in/krishdesai117/), and [**GitHub**](https://github.com/dkcoder02).

Thank you for Reading

**Happy Coding**

![](https://media.giphy.com/media/YlBXLAlJ1alpuYb7FM/giphy.gif?cid=ecf05e47wecfd8tv2wxenrb9zmihhry8fqstlx56buw6y7df&ep=v1_gifs_search&rid=giphy.gif&ct=g align="center")