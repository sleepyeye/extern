# extern
Collection of useful c++ libraries for personal usage.


Most of my personal project structure looks like this.

```
.
├── cmake
├── extern
│   ├── CMakeLists.txt
│   ├── eigen
│   ├── glad
│   ├── imgui
│   ├── lzfse
│   ├── stb
│   ├── tabulate
│   ├── tinyobjloader
│   └── tinyply
│   └── ...
├── include
└── src
└── CMakeLists.txt
```

I put small libraries in extern folder then use `add_subdirectory` command of CMake to include them.
Since I don't want to repeat this every time, I created this project.


# How to use it?

1. You can download the project and simply put it in desired folder in you project.
2. Use `add_subdirectory` from your root CMakeLists.txt to include the libraries.
3. Use `target_link_libraries` to link the library to your target. 

# List of libraries
TBD
