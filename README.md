# SimplerMeshViewer
A Simple Mesh Viewer Tutorial with C++ Source

<br />

The original website is here: [A Simple Mesh Viewer Tutorial with C++ Source](https://www3.cs.stonybrook.edu/~gu/tutorial/MeshViewer.html)

## Build with CMake

```bash
cmake -DFREEGLUT_ROOT=<freeglut_dir> -S <src_dir> -B <build_dir> --install-prefix <install_dir>
```

`<src_dir>` is the root directory where you have stored this project, such as **C:/Downloads/SimpleMeshViewer-main**.

`<build_dir>` is the directory where you can build this project with Visual Studio, Makefile or Xcode, etc. For instance: **C:/Downloads/SimpleMeshViewer-main/build**.

`<install_dir>` is the directory where the project will generate the final executable. For instance: **C:/Downloads/SimpleMeshViewer-main/install**.
Note that the directory name should be **`install`**, because the demo will specify this directory hard-coded.

