# rubiks-cube-solver

A C++ Rubik's Cube solver implementing several search algorithms and a corner pattern database generator.

**Features:**
- Implements solvers: DFS, BFS, IDDFS, IDA*.
- Corner pattern database utilities and a `CornerDBMaker` for generating databases.
- A `CubeScanner` (OpenCV) example that reads a physical cube and solves it using IDA* with a pattern database.

**Repository layout:**
- `Model/` — cube models and pattern database interfaces.
- `PatternDatabases/` — pattern database implementations and helpers.
- `PatternDatabases/CornerDBMaker.cpp` — tool to build the corner DB file (stored under `Databases/`).
- `Solver/` — solver implementations (`DFSSolver`, `BFSSolver`, `IDDFSSolver`, `IDAstarSolver`).
- `Scanner/` — `CubeScanner` (uses OpenCV) example code.
- `Databases/` — prebuilt database files (e.g. `cornerDepth5V1.txt`).

Prerequisites
- CMake (>= 3.20)
- A C++ compiler with C++14 support
- OpenCV (required by the scanner example)

Build
1. Create a build directory and run CMake:

```bash
mkdir -p build
cd build
cmake ..
make
```

2. The produced executable will be `build/rubiks_cube_solver`.

Running
- By default `main.cpp` contains example invocations (camera scanner + IDA* using a pattern database). The database path in `main.cpp` is currently set as a Windows absolute path — update it to the project-local database file if you want to run the example:

- Project database path: `Databases/cornerDepth5V1.txt`
- Example run (from the repo root after building):

```bash
./build/rubiks_cube_solver
```

Notes
- The scanner example uses OpenCV and a physical camera; if you don't have a camera or OpenCV available, comment out the `CubeScanner` usage in `main.cpp` and use the solver test code blocks instead (there are commented examples in `main.cpp`).
- To generate or regenerate the corner pattern database, use `PatternDatabases/CornerDBMaker.cpp` — update the target filename and run the program (requires adequate runtime/memory to bfs/store the database).


