# Data Structures & Algorithms (DSA) Repository Standards

> 📄 **Official Specification Document**:  
> The canonical version of this document is maintained in the dedicated documentation repository:  
> 👉 [`dsa-course-docs/standards/STANDARDS.md`](../dsa-course-docs/standards/STANDARDS.md)

---

## 1. README Section Hierarchy

All README files across labs, checkpoints, and projects must follow a standardized top-level section hierarchy:

1. `# [Assignment Name]`
2. `## Overview` (or `## Purpose` for labs)
3. `## Learning Outcomes`
4. `## Problem Description` / `## Background Information`
5. `## Requirements & Specifications`
6. `## Code Organization`
7. `## Building and Testing`
   - Explicit instructions for compiling the application (`make main`).
   - Instructions for running individual test targets (`make test-1-...`).
   - Instructions for running the entire test suite (`make test-all`).
   - Instructions for running memory leak checks (`make test-mem`).
8. `## Submission & Autograding`

---

## 2. Makefile Design & Target Parity

All Makefiles must adhere to the following rules:

### Standard Variables
```makefile
SHELL := /bin/bash
CXX = g++
CXXFLAGS = -g -std=c++14 -Wall -Werror=return-type -Werror=uninitialized -Wno-sign-compare
RM = rm -rf
```

### Required Targets
1. `main`: Compiles the main student program executable.
2. `test-all`: Dependencies include all test targets (`$(TESTS)`).
3. Individual test targets (`test-1-...`, `test-2-...`, `test-query1`, `test-win`):
   - **Autograding 1-to-1 Parity Rule**: Every test performed in autograding (`tests.json`) MUST have a corresponding `Makefile` target.
4. `test-mem`: Valgrind / memory leak verification target.
5. `clean`: Removes all generated build artifacts.

---

## 3. `.gitignore` Rules

Executables (`main`, `test-*`), precompiled headers (`*.gch`), debug symbols (`*.dSYM`), object files (`*.o`), and temp output files (`output.txt`, `.DS_Store`) must be ignored.
