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
  and in transit data movement.
* [Darshan][Darshan]: An HPC I/O
  characterization tool.
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
          [hdf5-vol-log](https://github.com/DataLib-ECP/vol-log-based) **are
          planned to be installed** when `ecp-data-vis-sdk +hdf5` is installed.
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([1](#adios2_note_1))</td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- CUDA -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="failing" markdown="span">([3](#ascent_note_1))</td><!-- CUDA -->
      <td class="na" markdown="span">([4](#ascent_note_2))</td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified" markdown="span">([5](#paraview_note_1))</td><!-- CUDA -->
      <td class="in_progress" markdown="span">([6](#paraview_note_2))</td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na" markdown="span">([7](#visit_note_1))</td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="verified"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="na"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([8](#zfp_note_1))</td><!-- ROCm -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="3">
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
      <th markdown="span">OneAPI ([9](#one_api_note_1))</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([1](#adios2_note_1))</td><!-- ROCm --><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- CUDA -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="failing" markdown="span">([3](#ascent_note_1))</td><!-- CUDA -->
      <td class="na" markdown="span">([4](#ascent_note_2))</td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="in_progress" markdown="span">([5](#paraview_note_1))</td><!-- CUDA -->
      <td class="in_progress" markdown="span">([6](#paraview_note_2))</td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na" markdown="span">([7](#visit_note_1))</td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="verified"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="na"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="na"></td><!-- CPU -->
      <td class="in_progress"></td><!-- CUDA -->
      <td class="na"></td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- CPU -->
      <td class="verified"></td><!-- CUDA -->
      <td class="na" markdown="span">([8](#zfp_note_1))</td><!-- ROCm -->
      <td class="in_progress"></td><!-- OneAPI -->
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
      <th>Pre-Frontier</th>
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
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="failing" markdown="span">([11](#ascent_note_3))</td><!-- Pre-Frontier -->
      <td class="failing" markdown="span">([12](#ascent_note_4))</td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="verified"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="in_progress"></td><!-- Desktop -->
      <td class="in_progress"></td><!-- Docker -->
      <td class="na"></td><!-- Pre-Frontier -->
      <td class="in_progress"></td><!-- Perlmutter -->
      <td class="na"></td><!-- Pre-Aurora -->
      <td class="in_progress"></td><!-- Smoke Test -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- Desktop -->
      <td class="verified"></td><!-- Docker -->
      <td class="verified"></td><!-- Pre-Frontier -->
      <td class="verified"></td><!-- Perlmutter -->
      <td class="in_progress"></td><!-- Pre-Aurora -->
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

### Pre-Frontier

Pre-Frontier here means "Crusher", which is assumed to be a system that matches the system software and architecture
of the target facility system Frontier. On of the primary challenges on this system is handling the compiler wrappers
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
      <td>v1.1.1</td>  <!-- CCE Toolchain -->
      <td>v5.2.3</td>  <!-- AMD Toolchain -->
    </tr>
    <tr>
      <td>
        Cray MPICH
      </td>  <!-- Info -->
      <td>v8.2.3</td>  <!-- GCC Toolchain -->
      <td>v8.2.3</td>  <!-- CCE Toolchain -->
      <td>v8.2.3</td>  <!-- AMD Toolchain -->
    </tr>
    <tr>
      <td>
        ROCm
      </td>  <!-- Info -->
      <td>v5.2.3</td>  <!-- GCC Toolchain -->
      <td>v5.2.3</td>  <!-- CCE Toolchain -->
      <td>v5.2.3</td>  <!-- AMD Toolchain -->
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
      <td class="na" markdown="span">([1](#adios2_note_1))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na" markdown="span">([1](#adios2_note_1))</td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="na" markdown="span">([1](#adios2_note_1))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
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
      <td class="verified"></td><!-- AMD -->
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
      <td class="verified"></td><!-- AMD -->
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
      <td class="verified"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="in_progress" markdown="span">([4](#ascent_note_2))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="in_progress" markdown="span">([4](#ascent_note_2))</td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="in_progress" markdown="span">([4](#ascent_note_2))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="in_progress" markdown="span">([6](#paraview_note_2))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="in_progress" markdown="span">([6](#paraview_note_2))</td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="in_progress" markdown="span">([6](#paraview_note_2))</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="in_progress"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="in_progress"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="verified"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="verified"></td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="verified" ></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [cuSZ][cuSZ]
      </td>
      <td class="na"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + ROCm -->
      <td class="na"></td><!-- CCE -->
      <td class="na"></td><!-- CCE + ROCm -->
      <td class="na"></td><!-- AMD -->
      <td class="na"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([8](#zfp_note_1))</td><!-- GCC + ROCm -->
      <td class="verified"></td><!-- CCE -->
      <td class="na" markdown="span">([8](#zfp_note_1))</td><!-- CCE + ROCm -->
      <td class="verified"></td><!-- AMD -->
      <td class="na" markdown="span">([8](#zfp_note_1))</td><!-- AMD + ROCm -->
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
      <td class="in_progress"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="in_progress"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([2](#veloc_note_1))</td><!-- GCC + CUDA -->
      <td class="in_progress" markdown="span">([2](#veloc_note_1))</td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="failing" markdown="span">([3](#ascent_note_1))</td><!-- GCC + CUDA -->
      <td class="in_progress" markdown="span">([3](#ascent_note_1))</td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([5](#paraview_note_1))</td><!-- GCC + CUDA -->
      <td class="in_progress" markdown="span">([5](#paraview_note_1))</td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="na" markdown="span">([7](#visit_note_1))</td><!-- GCC + CUDA -->
      <td class="in_progress" markdown="span">([7](#visit_note_1))</td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="verified" markdown="span"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
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
      <td class="in_progress"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="verified"></td><!-- GCC -->
      <td class="verified"></td><!-- GCC + CUDA -->
      <td class="in_progress"></td><!-- NVHPC + CUDA -->
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

In progress.

## Notes

<!-- NOTE: we want to group the notes and link to them from the table, so we
     will be creating anchor "span"s with id attributes to href to above. -->

### ADIOS2

<span id="adios2_note_1">1. </span>ROCm/HIP support is not expected in near term release.

### VeloC

<span id="veloc_note_1">2. </span>GPU support for VeloC is anticipated to land
in February 2023.

### Ascent

<span id="ascent_note_1">3. </span> The lastest available verison in the spack
package depends on an older version of VTK-m which doesn't properly implement
CUDA with shared libraries, which is required by the SDK.

<span id="ascent_note_2">4. </span>The lastest available verison in spack does
not have support for ROCm, but it is in the Ascent upstream and planned for
release before the end of 2022.

<span id="ascent_note_3">11. </span> the "+rocm" permutation of the SDK fails
due conflicting version requirements with VTK-m. Ascent 0.9.0 will have fixes
for this. The CPU version with Ascent in the SDK builds on Crusher
(Pre-Frontier) with the older version of VTK-m.

<span id="ascent_note_4">12. </span> The way MPI is set up on Perlmutter
conflicts with Ascent's spack recipe and CMake. Fixes for this are being
developed.

### ParaView

<span id="paraview_note_1">5. </span> While CUDA can be enabled in ParaView it
requires some recent patches to the `master` branch to work correctly.  We are
iterating with the ParaView team to get this enabled in Spack (`spack install
paraview@master`).

<span id="paraview_note_2">6. </span>ROCm support is available in the
5.11.0 release.

### VisIt

<span id="visit_note_1">7. </span>VTK-m enabled GPU support is planned for VisIt
by early 2023.

### VTK-m

<span id="vtk_m_note_1">13. </span> Spack configurations when using MPI + HIP
(ROCm) are not yet compatible with the Cray compiler wrappers.

### ZFP

<span id="zfp_note_1">8. </span>ROCm support is planned for 2023.

### OneAPI

<span id="one_api_note_1">9. </span>OneAPI is currently not tested by the SDK.
Plans to begin testing with OneAPI will begin when Aurora pre-release system
become available.
