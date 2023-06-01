# ECP Data and Visualization SDK
{:.no_toc}

The Data and Visualization SDK is an integration effort for the collection of
I/O, compression, visualization, and analysis software developed under the
[DOE's Exascale Computing Program (ECP)][doe_ecp].  Software developed under ECP
targets using [Spack](https://spack.io), an HPC targeted source-based package
manager, for installation on HPC platforms.  The primary product of this project
is the [`ecp-data-vis-sdk` Spack meta-package][spack_package] which allows the
set of SDK member packages to be built together in a way that enables optimal
features for ECP target environments as well as interoperable features provided
by other packages within the SDK.

[doe_ecp]: https://www.exascaleproject.org/
[spack_package]: https://github.com/spack/spack/blob/develop/var/spack/repos/builtin/packages/ecp-data-vis-sdk/package.py

* TOC bullet point is replaced by kramdown to generate table of contents.
{:toc}

## Included Projects

The following projects are included as part of the Data and Visualization SDK:

### I/O and Data Management

* [ADIOS2][ADIOS2]: An adaptable framework for HPC I/O supporting files, in situ,
  and in transit data movement. ADIOS2 also generates an HDF5 VOL Adapter.
* [Darshan][Darshan]: An HPC I/O characterization tool.
* [HDF5][HDF5]: A data model, library, and file format for storing and managing
  data.
    * CUDA support (where applicable) is provided by the [HDF5 GPUDirect Storage
      VFD](https://github.com/hpc-io/vfd-gds).  Refer to the documentation for
      more information on enabling GDS VFD for your application.  The SDK will
      install the package and populate `HDF5_PLUGIN_PATH` (only).
    * [HDF5 VOL](https://docs.hdfgroup.org/hdf5/develop/group___h5_m.html)
      plugins will be installed with `HDF5_PLUGIN_PATH` populated:
        * [ADIOS2][ADIOS2]: when `ecp-data-vis-sdk +adios2 +hdf5` is installed,
          the ADIOS2 VOL is installed (by the `adios2` package).
        * [hdf5-vol-cache](https://github.com/hpc-io/vol-cache),
          [hdf5-vol-async](https://github.com/hpc-io/vol-async), and
          [hdf5-vol-log](https://github.com/DataLib-ECP/vol-log-based) are
          installed** when `ecp-data-vis-sdk +hdf5 ^hdf5@1.14:` is installed.
          ([6](#hdf5_vols_oneapi))
        * [hdf5-vol-daos](https://github.com/HDFGroup/vol-daos) is a VOL adapter
          used for direct interfacing with the Distributed Asynchronous Object
          Storage (DAOS) system, bypassing both MPI I/O and POSIX for efficient
          and scalable I/O. This VOL adapter is currently being tested on Pre-Aurora
          systems with DAOS support.
* [PNetCDF][PNetCDF]: A high-performance parallel I/O library for accessing
  Unidata's NetCDF, files in classic formats, specifically the formats of CDF-1,
   2, and 5.
* [UnifyFS][UnifyFS]: A filesystem for burst buffers.
* [VeloC][VeloC]: A multi-level checkpoint-restart runtime for HPC
  supercomputing infrastructures and large-scale data centers.

[ADIOS2]: https://csmd.ornl.gov/software/adios2
[Darshan]: https://www.mcs.anl.gov/research/projects/darshan/
[HDF5]: https://www.hdfgroup.org/solutions/hdf5/
[PNetCDF]: https://parallel-netcdf.github.io/
[UnifyFS]: https://unifyfs.readthedocs.io/en/latest/
[VeloC]: https://veloc.readthedocs.io/en/latest/

### Visualization and Analysis

* [Ascent][Ascent]: An open source many-core capable lightweight in situ
  visualization and analysis infrastructure for multi-physics HPC simulations.
* [Cinema][Cinema]: An image-based approach to extreme scale in situ
  visualization and analysis.
* [ParaView][ParaView]: An open-source, multi-platform data analysis and
  visualization application.
* [SENSEI][SENSEI]: An interface for scalable in situ analysis and visualization
  of simulation data.
* [VisIt][VisIt]: An open source, interactive, scalable, visualization,
  animation and analysis tool.
* [VTK-m][VTK-m]: A toolkit if scientific visualization algorithms for emerging
  processor architectures.

[Ascent]: https://github.com/Alpine-DAV/ascent
[Cinema]: https://cinemascience.github.io
[ParaView]: https://paraview.org
[SENSEI]: https://sensei-insitu.org/
[VisIt]: https://visit-dav.github.io/visit-website/
[VTK-m]: https://m.vtk.org

### Compression

* [SZ][SZ]: An error-bounded lossy data compressor for floating-point and
  integer datasets.
* [cuSZ][cuSZ]: A CUDA based implementation of the [SZ][SZ] lossy compressor.
* [ZFP][ZFP]: An open-source library for compressed floating-point arrays that
  support high throughput read and write random access.

[SZ]: https://szcompressor.org
[cuSZ]: https://github.com/szcompressor/cuSZ
[ZFP]: https://computing.llnl.gov/projects/zfp

# Integration Status

## General Spack Support

<!-- colored tables must be done in html not markdown -->
<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>CPU</th>
      <th>CUDA</th>
      <th>ROCm</th>
      <th markdown="span">SYCL ([*](#oneapi_sycl))</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([1](#adios2_rocm))</td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na" markdown="span">([13](#veloc_cuda))</td><!-- CUDA -->
      <td class="na" markdown="span">([14](#veloc_rocm))</td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="failing" markdown="span">([2](#ascent_cuda_raja))</td><!-- CUDA -->
      <td class="in_progress" markdown="span">([3](#ascent_rocm))</td><!-- ROCm -->
      <td class="na" markdown="span">([22](#ascent_no_sycl))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="verified"></td><!-- ROCm -->
      <td class="na" markdown="span">([7](#paraview_oneapi_sycl))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="verified" markdown="span">([10](#sensei_ospray))</td><!-- CPU -->
      <td class="na" markdown="span">([11](#sensei_kokkos))</td><!-- CUDA -->
      <td class="na" markdown="span">([11](#sensei_kokkos))</td><!-- ROCm -->
      <td class="na" markdown="span">([11](#sensei_kokkos))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified" markdown="span">([16](#visit_vtkm_support))</td><!-- CUDA -->
      <td class="verified" markdown="span">([16](#visit_vtkm_support))</td><!-- ROCm -->
      <td class="na" markdown="span">([16](#visit_vtkm_support))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="verified"></td><!-- ROCm -->
      <td class="failing" markdown="span">([17](#vtkm_oneapi_sycl))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="na"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([20](#zfp_rocm))</td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="4">
        <table class="status_table_legend">
          <tr>
            <td class="verified" style="color: white">Available</td>
            <td class="na" style="color: white">Not Available</td>
            <td class="failing" style="color: white">Failing</td>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

## ECP DAV SDK Support

<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>CPU</th>
      <th>CUDA</th>
      <th>ROCm</th>
      <th markdown="span">SYCL ([*](#oneapi_sycl))</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([1](#adios2_rocm))</td><!-- ROCm --><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na" markdown="span">([13](#veloc_cuda))</td><!-- CUDA -->
      <td class="na" markdown="span">([14](#veloc_rocm))</td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="failing" markdown="span">([2](#ascent_cuda_raja))</td><!-- CUDA -->
      <td class="in_progress" markdown="span">([3](#ascent_rocm))</td><!-- ROCm -->
      <td class="na" markdown="span">([22](#ascent_no_sycl))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="in_progress"></td><!-- CUDA -->
      <td class="verified"></td><!-- ROCm -->
      <td class="in_progress" markdown="span">([7](#paraview_oneapi_sycl))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- CPU -->
      <td class="in_progress" markdown="span">([11](#sensei_kokkos)) ([12](#sensei_catalyst_backend))</td><!-- CUDA -->
      <td class="in_progress" markdown="span">([11](#sensei_kokkos)) ([12](#sensei_catalyst_backend))/td><!-- ROCm -->
      <td class="in_progress" markdown="span">([11](#sensei_kokkos)) ([12](#sensei_catalyst_backend))/td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- CPU -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- CUDA -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- ROCm -->
      <td class="na" markdown="span">([7](#paraview_oneapi_sycl))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="verified"></td><!-- ROCm -->
      <td class="in_progress" markdown="span">([17](#vtkm_oneapi_sycl))</td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="na"></td><!-- CPU -->
      <td class="in_progress"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([20](#zfp_rocm))</td><!-- ROCm -->
      <td class="na"></td><!-- SYCL -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="4">
        <table class="status_table_legend">
          <tr>
            <th class="verified" style="color: white;">Verified</th>
            <th class="in_progress" style="color: white;">In Progress</th>
            <th class="na" style="color: white;">Not Applicable</th>
            <th class="failing" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

## Extreme-scale Scientific Software Stack (E4S)

### E4S Deployment

This table is an overview of the status of the different deployments of the Data and Vis SDK via E4S. Some items may be
marked as "In Progress" but have fully completed specific stacks on those systems. The following tables will fill in
more details on the facility deployments.

<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>Desktop</th>
      <th>Docker</th>
      <th>Frontier</th>
      <th>Perlmutter</th>
      <th>Pre-Aurora</th>
      <th>Smoke Test</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress" markdown="span">([6](#hdf5_vols_oneapi))</td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="in_progress" markdown="span">([21](#ascent_find_mpi_frontier))</td><!-- Frontier -->
      <td class="failing" markdown="span">([4](#ascent_perlmutter_mpi))</td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress" markdown="span">([5](#cinema_oneapi_python))</td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress" markdown="span">([8](#paraview_no_ospray)) ([9](#paraview_oneapi_python))</td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- Desktop -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- Docker -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- Frontier -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- Perlmutter -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- Desktop -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- Docker -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- Frontier -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- Perlmutter -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress" markdown="span">([17](#vtkm_oneapi_sycl))</td><!-- Pre-Aurora -->
      <td class="verified"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="na"></td><!-- Desktop -->
      <td class="na"></td><!-- Docker -->
      <td class="na"></td><!-- Frontier -->
      <td class="na"></td><!-- Perlmutter -->
      <td class="na"></td><!-- Pre-Aurora -->
      <td class="na"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="verified"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="6">
        <table class="status_table_legend">
          <tr>
            <th class="verified" style="color: white;">Verified</th>
            <th class="in_progress" style="color: white;">In Progress</th>
            <th class="na" style="color: white;">Not Applicable</th>
            <th class="failing" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

### Frontier

One of the primary challenges on Frontier is handling the compiler wrappers
for the CCE and AMD compilers, in particular how they wrap MPI and HIP.

<table class="toolchain_table">
  <thead>
    <tr>
      <th>Info</th>
      <th>GCC Toolchain</th>
      <th>CCE Toolchain</th>
      <th>AMD Toolchain</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        Version
      </td>  <!-- Info -->
      <td>v11.2</td>  <!-- GCC Toolchain -->
      <td>v14.0.2</td>  <!-- CCE Toolchain -->
      <td>v5.3.0</td>  <!-- AMD Toolchain -->
    </tr>
    <tr>
      <td>
        Cray MPICH
      </td>  <!-- Info -->
      <td>v8.1.23</td>  <!-- GCC Toolchain -->
      <td>v8.1.23</td>  <!-- CCE Toolchain -->
      <td>v8.1.23</td>  <!-- AMD Toolchain -->
    </tr>
    <tr>
      <td>
        ROCm
      </td>  <!-- Info -->
      <td>v5.3.0</td>  <!-- GCC Toolchain -->
      <td>v5.3.0</td>  <!-- CCE Toolchain -->
      <td>v5.3.0</td>  <!-- AMD Toolchain -->
    </tr>
  </tbody>
</table>

<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>GCC</th>
      <th>GCC + ROCm</th>
      <th>CCE</th>
      <th>CCE + ROCm</th>
      <th>AMD</th>
      <th>AMD + ROCm</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([1](#adios2_rocm))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na" markdown="span">([1](#adios2_rocm))</td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na" markdown="span">([1](#adios2_rocm))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([14](#veloc_rocm))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="in_progress" markdown="span">([3](#ascent_rocm))</td><!-- GCC + ROCm -->
      <td class="in_progress" markdown="span">([21](#ascent_find_mpi_frontier))</td><!-- CCE -->
      <td class="in_progress" markdown="span">([3](#ascent_rocm))</td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="in_progress" markdown="span">([3](#ascent_rocm))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="verified"></td><!-- GCC + ROCm -->
      <td class="verified" markdown="span">([8](#paraview_no_ospray))</td><!-- CCE -->
      <td class="verified" markdown="span">([8](#paraview_no_ospray))</td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="in_progress"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- GCC -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- GCC + ROCm -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- CCE -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- CCE + ROCm -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- AMD -->
      <td class="in_progress" markdown="span">([12](#sensei_catalyst_backend))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- GCC -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- GCC + ROCm -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- CCE -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- CCE + ROCm -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- AMD -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="verified" markdown="span">([18](#vtkm_rocm_openmp))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="verified" markdown="span">([18](#vtkm_rocm_openmp)) ([19](#vtkm_cray_wrapper_workaround))</td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="in_progress" markdown="span">([18](#vtkm_rocm_openmp)) ([19](#vtkm_cray_wrapper_workaround))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([20](#zfp_rocm))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na" markdown="span">([20](#zfp_rocm))</td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na" markdown="span">([20](#zfp_rocm))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="6">
        <table class="status_table_legend">
          <tr>
            <th class="verified" style="color: white;">Verified</th>
            <th class="in_progress" style="color: white;">In Progress</th>
            <th class="na" style="color: white;">Not Applicable</th>
            <th class="failing" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

### Perlmutter Toolchains (CUDA)

<table class="toolchain_table">
  <thead>
    <tr>
      <th>Info</th>
      <th>GCC Toolchain</th>
      <th>NVHPC Toolchain</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        Version
      </td>  <!-- Info -->
      <td>v11.2</td>  <!-- GCC Toolchain -->
      <td>v22.4</td>  <!-- NVHPC Toolchain -->
    </tr>
    <tr>
      <td>
        Cray MPICH
      </td>  <!-- Info -->
      <td>v8.2.3</td>  <!-- GCC Toolchain -->
      <td>v8.2.3</td>  <!-- NVHPC Toolchain -->
    </tr>
    <tr>
      <td>
        CUDA
      </td>  <!-- Info -->
      <td>v11.3</td>  <!-- GCC Toolchain -->
      <td>v11.3</td>  <!-- NVHPC Toolchain -->
    </tr>
  </tbody>
</table>

<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>GCC</th>
      <th>GCC + CUDA</th>
      <th>NVHPC + CUDA</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([13](#veloc_cuda))</td><!-- GCC + CUDA -->
      <td class="na" markdown="span">([13](#veloc_cuda))</td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="failing" markdown="span">([2](#ascent_cuda_raja))</td><!-- GCC + CUDA -->
      <td class="na" markdown="span">([2](#ascent_cuda_raja))</td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na" markdown="span"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="na"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- GCC -->
      <td class="na" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- GCC + CUDA -->
      <td class="na" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="verified" markdown="span"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="na"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="verified"></td><!-- GCC + CUDA -->
      <td class="na"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="3">
        <table class="status_table_legend">
          <tr>
            <th class="verified" style="color: white;">Verified</th>
            <th class="in_progress" style="color: white;">In Progress</th>
            <th class="na" style="color: white;">Not Applicable</th>
            <th class="failing" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>


### Pre-Aurora Toolchains

<table class="toolchain_table">
  <thead>
    <tr>
      <th>Info</th>
      <th>OneAPI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        Version
      </td>  <!-- Info -->
      <td>v2023.0.0</td>  <!-- OneAPI Toolchain -->
    </tr>
  </tbody>
</table>

<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>OneAPI</th>
      <th markdown="span">SYCL ([*](#oneapi_sycl))</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="in_progress" markdown="span">([6](#hdf5_vols_oneapi))</td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="in_progress" markdown="span">([5](#cinema_oneapi_python))</td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="in_progress" markdown="span">([8](#paraview_no_ospray)) ([9](#paraview_oneapi_python))</td><!-- OneApi -->
      <td class="in_progress" markdown="span">([7](#paraview_oneapi_sycl))</td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="in_progress" markdown="span">([10](#sensei_ospray)) ([12](#sensei_catalyst_backend))</td><!-- OneApi -->
      <td class="in_progress" markdown="span">([11](#sensei_kokkos)) ([12](#sensei_catalyst_backend))</td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict))</td><!-- OneApi -->
      <td class="failing" markdown="span">([15](#visit_hdf5_conflict)) ([16](#visit_vtkm_support))</td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="in_progress" markdown="span">([17](#vtkm_oneapi_sycl))</td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- OneApi -->
      <td class="na"></td><!-- OneApi -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="2">
        <table class="status_table_legend">
          <tr>
            <th class="verified" style="color: white;">Verified</th>
            <th class="in_progress" style="color: white;">In Progress</th>
            <th class="na" style="color: white;">Not Applicable</th>
            <th class="failing" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

## Notes

<!-- NOTE: we want to group the notes and link to them from the table, so we
     will be creating anchor "span"s with id attributes to href to above. -->

<span id="oneapi_sycl">\* </span>SYCL extensions are implemented and tested using OneAPI.


### ADIOS2

<span id="adios2_rocm">1. </span>ROCm/HIP support is not expected in near term release.

### Ascent

<span id="ascent_cuda_raja">2. </span> Blocked by build errors in RAJA package.

<span id="ascent_rocm">3. </span>The spack recipe does not have support for ROCm.
It is in under development in the Alpine Spack fork.

<span id="ascent_perlmutter_mpi">4. </span> The way MPI is set up on Perlmutter
conflicts with Ascent's spack recipe and CMake. Fixes for this are being
developed.

<span id="ascent_find_mpi_frontier">21. </span>Using the CCE toolchain has issues locating
MPI with CMake.

<span id="ascent_no_sycl">22. </span>Ascent currently does not have any known plans for explicit
SYCL support.

### Cinema

<span id="cinema_oneapi_python">5. </span>Failure to build a number of Python modules with OneAPI.

### HDF5

<span id="hdf5_vols_oneapi">6. </span>HDF5 v1.14 builds with OneAPI, but the
async, cache, and log VOL adapters are currently disabled due to build errors.

### ParaView

<span id="paraview_oneapi_sycl">7. </span>ParaView and VisIt do not support building SYCL kernels for VTKm
filters in released versions.

<span id="paraview_no_ospray">8. </span>OSPRay support has been disabled due to build errors.

<span id="paraview_oneapi_python">9, </span>Failure to build a number of Python modules with OneAPI.

### SENSEI

<span id="sensei_ospray">10, </span>SENSEI is developing native OSPRay rendering support.

<span id="sensei_kokkos">11. </span>SENSEI is developing Kokkos support for ROCm, CUDA, and SYCL interop.

<span id="sensei_catalyst_backend">12. </span>SENSEI is developing updates to support ParaView v5.11 and Catalyst 2.

### VeloC

<span id="veloc_cuda">13. </span>CUDA support for VeloC is under development.

<span id="veloc_rocm">14. </span>Kokkos/ROCm support for VeloC is experimental in [kokkos-resilience](https://github.com/kokkos/kokkos-resilience)

### VisIt

<span id="visit_hdf5_conflict">15. </span>VisIt utilizes a VTK version locked to a Python that
is not compatible with the Python requirements of PyH5, the HDF5 python interface used by Cinema.

<span id="visit_vtkm_support">16. </span>VTK-m enabled GPU support is available VisIt, but
is not officially tested as part of the Data and Vis SDK due to ([15](#visit_hdf5_conflict)).

### VTK-m

<span id="vtkm_oneapi_sycl">17. </span>VTKm does not fully support building SYCL kernels
in currently released versions, but has some support on the "master" branch.

<span id="vtkm_rocm_openmp">18. </span>Spack ROCm does not provide OpenMP correclty for VTKm HIP
modules.

<span id="vtkm_cray_wrapper_workaround">19. </span>Frontier requires additional workarounds in the Spack
recipe for VTKm that are specific to the Cray wrappers on Frontier.
[patch](https://github.com/spack/spack/pull/34427)

### ZFP

<span id="zfp_rocm">20. </span>ROCm support is under development.
