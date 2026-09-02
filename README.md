# 云计算实验项目 - Sobel边缘检测算法并行实现

## 项目简介

本项目是中国科学院大学工程科学学院云计算课程的实践项目，实现了Sobel边缘检测算法的多种并行化和分布式版本。该项目展示了如何在集群环境中编写高效的分布式并行程序，进行大规模图像处理。

**项目涵盖的主要内容：**

1. **CPU并行加速** - 基于OpenMP实现单节点上的Sobel边缘检测算法多核并行处理
2. **GPU并行加速** - 基于OpenCL和CUDA实现单节点上的GPU并行处理
3. **分布式并行处理** - 基于MPI在集群上实现分布式并行处理
4. **混合模式并行处理** - 基于MPI+OpenMP和MPI+CUDA实现多节点CPU+GPU混合并行处理

## 项目依赖

| 依赖项 | 说明 |
|------|------|
| **OpenMP** | 多线程共享内存并行编程API，用于单节点多核CPU加速 [openmp.org](https://www.openmp.org/) |
| **OpenCL** | 跨平台异构计算标准，支持各类加速器（CPU、GPU等）[khronos.org](https://www.khronos.org/opencl/) |
| **CUDA** | NVIDIA GPU计算工具包，用于GPU并行加速 [developer.nvidia.com](https://developer.nvidia.com/cuda-toolkit) |
| **MPI** | 分布式内存并行编程标准，推荐使用[Open MPI](https://www.open-mpi.org/)实现 |
| **FreeImage** | 开源图像处理库，支持JPEG、PNG、BMP等多种格式 [freeimage.sourceforge.io](https://freeimage.sourceforge.io/) |
| **CMake** | 跨平台自动化编译构建工具 |

## 开发环境配置

### 1. 安装依赖工具

| 工具 | 安装命令/说明 |
|-----|-----------|
| Git | 用于版本控制和代码管理 |
| C++编译器 | macOS: Clang; Linux: gcc; Windows: MSVC |
| CMake | `brew install cmake` (macOS) 或 `apt-get install cmake` (Linux) |
| OpenCL SDK | 根据GPU型号安装（如NVIDIA CUDA） |
| CUDA Toolkit | NVIDIA GPU用户安装 |
| MPI | Linux: `apt-get install openmpi-bin libopenmpi-dev` |
| FreeImage | 图像处理库，编译时需要 |

### 2. 项目编译

```bash
# 克隆项目
git clone https://github.com/JachynRen/Cloud-Computing-Experiment.git
cd Cloud-Computing-Experiment

# 使用CMake编译
mkdir build
cd build
cmake ..
make
```

## 实现版本说明

项目包含Sobel边缘检测算法的7个不同实现版本：

| 程序名 | 实现方式 | 适用场景 |
|--------|--------|--------|
| **sobel** | 串行版本 | 基准程序，用于性能对比 |
| **sobel_omp** | OpenMP多线程 | 单节点多核CPU加速 |
| **sobel_ocl** | OpenCL | 单节点异构计算加速 |
| **sobel_cuda** | NVIDIA CUDA | 单节点GPU加速 |
| **sobel_mpi** | MPI分布式 | 多节点集群计算 |
| **sobel_mpi_omp** | MPI + OpenMP混合 | 多节点CPU集群加速 |
| **sobel_mpi_cuda** | MPI + CUDA混合 | 多节点异构集群加速 |

## 技能学习收获

通过本项目的实现和实验，掌握以下关键技能：

✅ **并行编程** - 深入理解OpenMP、OpenCL、CUDA等并行编程模型  
✅ **分布式计算** - MPI编程与集群计算实践  
✅ **性能优化** - 算法优化与并行效率分析  
✅ **CMake工程管理** - 跨平台编译构建系统  
✅ **实际问题求解** - 从串行到并行的逐步优化过程  

## 项目结构

```
├── src/                    # 源代码目录
│   ├── sobel.cpp          # 串行版本
│   ├── sobel_omp.cpp      # OpenMP版本
│   ├── sobel_ocl.cpp      # OpenCL版本
│   ├── sobel_cuda.cu      # CUDA版本
│   ├── sobel_mpi.cpp      # MPI版本
│   ├── sobel_mpi_omp.cpp  # MPI+OpenMP版本
│   ├── sobel_mpi_cuda.cu  # MPI+CUDA版本
│   └── batchresize.cpp    # 批处理工具
├── include/               # 头文件目录
│   ├── sobel.h            # Sobel算法接口
│   ├── cudautils.h        # CUDA工具函数
│   ├── oclutils.h         # OpenCL工具函数
│   ├── imgutils.h         # 图像处理工具
│   └── logutils.h         # 日志工具
├── ocl/                   # OpenCL内核代码
│   └── sobel.cl
├── 3rdparty/              # 第三方库
│   └── FreeImage/         # FreeImage图像库
├── cmake/                 # CMake配置文件
└── CMakeLists.txt         # 项目构建配置
```

## 许可证

本项目采用GNU GPL v3许可证。详见[COPYING](COPYING)文件。

## 参考资源

- [OpenMP官方文档](https://www.openmp.org/)
- [Khronos OpenCL规范](https://www.khronos.org/opencl/)
- [NVIDIA CUDA文档](https://developer.nvidia.com/cuda-toolkit)
- [Open MPI项目](https://www.open-mpi.org/)
- [FreeImage库](https://freeimage.sourceforge.io/)
