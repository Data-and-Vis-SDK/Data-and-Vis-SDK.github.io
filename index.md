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

* [ADIOS][ADIOS]: An adaptable framework for HPC I/O supporting files, in situ,
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

[ADIOS]: https://csmd.ornl.gov/software/adios2
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
        [ADIOS][ADIOS]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
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
      <td class="gray"></td><!-- CUDA -->
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
      <td class="gray" markdown="span">([^1])</td><!-- CUDA -->
      <td class="gray" markdown="span">([^1])</td><!-- ROCm -->
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
      <td class="green" markdown="span">([^2])</td><!-- CUDA -->
      <td class="gray" markdown="span">([^3])</td><!-- ROCm -->
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
      <td class="gray"></td><!-- CUDA -->
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
      <td class="gray"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="green"></td><!-- CPU -->
      <td class="green"></td><!-- CUDA -->
      <td class="gray"></td><!-- ROCm -->
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

[^1]: Ascent: the lastest available verison in the spack package depends on an
      older version of VTK-m which doesn't properly implement CUDA and ROCm.
      This creates a conflict with being able to enable the latest versions of
      all packages with GPU features enabled.  The most recent upstream Ascent
      release uses an appropriately newer version of VTK-m but it has not yet
      made it to the spack package.

[^2]: ParaView: while CUDA can be enabled in ParaView it requires some recent
      patches to the `master` branch to work correctly.  We are iterating with the
      ParaView team to get this enabled in Spack.

[^3]: ParaView: ROCm support will be available in the 5.11.0 release.

## ECP SDK Support

<table class="status_table">
  <thead>
    <tr>
      <th>Project</th>
      <th>CPU</th>
      <th>CUDA</th>
      <th>ROCm</th>
      <th>OneAPI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td markdown="span">
        [ADIOS][ADIOS]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="dark_pink"></td><!-- CPU -->
      <td class="dark_pink"></td><!-- CUDA -->
      <td class="dark_pink"></td><!-- ROCm -->
      <td class="dark_pink"></td><!-- OneAPI -->
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

## Extreme-scale Scientific Software Stack (E4S)

### E4S Deployment

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
        [ADIOS][ADIOS]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="dark_pink"></td><!-- Desktop -->
      <td class="dark_pink"></td><!-- Docker -->
      <td class="dark_pink"></td><!-- Pre-Frontier -->
      <td class="dark_pink"></td><!-- Perlmutter -->
      <td class="dark_pink"></td><!-- Pre-Aurora -->
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

### Pre-Frontier

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
        [ADIOS][ADIOS]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink" markdown="span">([^4])</td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + ROCm -->
      <td class="dark_pink"></td><!-- CCE -->
      <td class="dark_pink"></td><!-- CCE + ROCm -->
      <td class="dark_pink"></td><!-- AMD -->
      <td class="dark_pink"></td><!-- AMD + ROCm -->
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

[^4]: VTK-m: several versions of the AMD compiler are known to crash when
      building VTK-m.

### Perlmutter Toolchains (CUDA)

Perlmutter is pinned to GCC X.Y.Z and CUDA A.B.C.

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
        [ADIOS][ADIOS]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Darshan][Darshan]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [HDF5][HDF5]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [PNetCDF][PNetCDF]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [UnifyFS][UnifyFS]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VeloC][VeloC]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Ascent][Ascent]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [Cinema][Cinema]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ParaView][ParaView]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [SENSEI][SENSEI]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VisIt][VisIt]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [VTK-m][VTK-m]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink" markdown="span">([^5])</td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [SZ][SZ]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
    </tr>
    <tr>
      <td markdown="span">
        [ZFP][ZFP]
      </td>
      <td class="dark_pink"></td><!-- GCC -->
      <td class="dark_pink"></td><!-- GCC + CUDA -->
      <td class="dark_pink"></td><!-- NVHPC + CUDA -->
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

[^5]: VTK-m: several versions of the NVIDIA CUDA compiler are known to crash
      when building VTK-m.

### Pre-Aurora Toolchains

In progress.

## Notes

<!-- NOTE: keep this last, we do not want anything between this header and the
     footnotes added at the bottom by jekyll. -->
