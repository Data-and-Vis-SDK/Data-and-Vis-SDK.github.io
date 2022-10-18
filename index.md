# ECP Data and Visualization SDK
{:.no_toc}

The Data and Visualization SDK is an integration effort for the collection of
I/O, compression, visualization, and analysis software developed under the DOE's
Exascale Computing Program (ECP).  Software developed under ECP targets using
[Spack](https://spack.io), an HPC targeted source-based package manager, for
installation on HPC platforms.  The primary product of this project is the
[`ecp-data-vis-sdk` Spack meta-package][spack_package] which allows the set of
SDK member packages to be built together in a way that enables optimal features
for ECP target environments as well as interoperable features provided by other
packages within the SDK.

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
* [ZFP][ZFP]: An open-source library for compressed floating-point arrays that
  support high throughput read and write random access.

[SZ]: https://szcompressor.org
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
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="gray" markdown="span">([^1])</td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green" markdown="span">([^2])</td><!-- CUDA -->
      <td class="gray" markdown="span">([^3])</td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green" markdown="span">([^4])</td><!-- CUDA -->
      <td class="gray" markdown="span">([^5])</td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray" markdown="span">([^6])</td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="green"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray" markdown="span">([^7])</td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUD -->
      <td class="gray" markdown="span">([^8])</td><!-- ROCm -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="3">
        <table class="status_table_legend">
          <tr>
            <td class="green" style="color: white">Available</td>
            <td class="gray" style="color: white">Not Available</td>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

[^1]: ADIOS2: ROCm/HIP support is in progress

[^2]: Ascent: the lastest available verison in the spack package depends on an
      older version of VTK-m which doesn't properly implement CUDA with shared
      libraries, which is required by the SDK.

[^3]: Ascent: the lastest available verison in spack does not have support for
      ROCm, but it is in the Ascent upstream and planned for release before the
      end of 2022.

[^4]: ParaView: while CUDA can be enabled in ParaView it requires some recent
      patches to the `master` branch to work correctly.  We are iterating with the
      ParaView team to get this enabled in Spack.

[^5]: ParaView: ROCm support will be available in the 5.11.0 release.

[^6]: VisIt: VTK-m enabled GPU support is planned for VisIt by early 2023.

[^7]: SZ: GPU support for SZ will require the use of new libraries SZ stacks.

[^8]: ZFP: ROCm support is planned for EOY 2022

## ECP SDK Support

<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>CPU</th>
      <th>CUDA</th>
      <th>ROCm</th>
      <th markdown="span">OneAPI ([^9])</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="light_blue"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="light_blue"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="light_blue"></td><!-- CUDA -->
      <td class="light_blue"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="green"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="light_blue"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
      <td class="gray"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="4">
        <table class="status_table_legend">
          <tr>
            <th class="green" style="color: white;">Verified</th>
            <th class="light_blue" style="color: white;">In Progress</th>
            <th class="gray" style="color: white;">Not Applicable</th>
            <th class="red" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

[^9]:  OneAPI is currently not tested by the SDK. Plans to begin testing with OneAPI will begin
       when Aurora pre-release system become available.

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
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS2][ADIOS2]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="light_blue"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="light_blue"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="red" markdown="span">([^10])</td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="red" markdown="span">([^11])</td><!-- Pre-Frontier -->
      <td class="red" markdown="span">([^12])</td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="light_blue"></td><!-- Pre-Frontier -->
      <td class="light_blue"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="light_blue"></td><!-- Pre-Frontier -->
      <td class="light_blue"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="green"></td><!-- Desktop -->
      <td class="green"></td><!-- Docker -->
      <td class="green"></td><!-- Pre-Frontier -->
      <td class="green"></td><!-- Perlmutter -->
      <td class="gray"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="5">
        <table class="status_table_legend">
          <tr>
            <th class="green" style="color: white;">Verified</th>
            <th class="light_blue" style="color: white;">In Progress</th>
            <th class="gray" style="color: white;">Not Applicable</th>
            <th class="red" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

[^10]: UnifyFS: E4S Container deployment requires a downgrade to allow building dependencies of UnifyFS that
       require an older version of glibc.

[^11]: Ascent: the "+rocm" permutation of the SDK fails due conflicting version requirements with
       VTK-m. Ascent 0.9.0 will have fixes for this. The CPU version with Ascent in the SDK
       builds on Crusher (Pre-Frontier) with the older version of VTK-m.

[^12]: Ascent: The way MPI is set up on Perlmutter conflicts with Ascent's spack recipe and CMake. Fixes
       for this are being developed.

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
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="green"></td><!-- GCC + ROCm -->
      <td class="light_blue"></td><!-- CCE -->
      <td class="red" markdown="span">([^13])</td><!-- CCE + ROCm -->
      <td class="light_blue"></td><!-- AMD -->
      <td class="red" markdown="span">([^13])</td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="green"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="green"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + ROCm -->
      <td class="green"></td><!-- CCE -->
      <td class="gray"></td><!-- CCE + ROCm -->
      <td class="green"></td><!-- AMD -->
      <td class="gray"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="6">
        <table class="status_table_legend">
          <tr>
            <th class="green" style="color: white;">Verified</th>
            <th class="light_blue" style="color: white;">In Progress</th>
            <th class="gray" style="color: white;">Not Applicable</th>
            <th class="red" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>

[^13]: VTK-m: Spack configurations when using MPI + HIP (ROCm) are not yet compatible
       with the Cray compiler wrappers.

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
      <td class="green"></td><!-- GCC -->
      <td class="light_blue"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="light_blue"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="red" markdown="span">([^2])</td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="green" markdown="span"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="gray"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="green"></td><!-- GCC -->
      <td class="green"></td><!-- GCC + CUDA -->
      <td class="light_blue"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td style="background-color: #373737; color: white">Legend</td>
      <td colspan="3">
        <table class="status_table_legend">
          <tr>
            <th class="green" style="color: white;">Verified</th>
            <th class="light_blue" style="color: white;">In Progress</th>
            <th class="gray" style="color: white;">Not Applicable</th>
            <th class="red" style="color: white;">Failing</th>
          </tr>
        </table>
      </td>
    </tr>
  </tbody>
</table>


### Pre-Aurora Toolchains

In progress.

## Notes

<!-- NOTE: keep this last, we do not want anything between this header and the
     footnotes added at the bottom by jekyll. -->
