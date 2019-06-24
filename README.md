KNIME node to calculate subfamily specific two entropy analysis (ss-TEA) score.

The ss-TEA can identify specific ligand binding residue positions for any receptor, predicated on high quality sequence information.

See reference at https://doi.org/10.1186/1471-2105-12-332 for a description of the score.

[![Build Status](https://travis-ci.org/3D-e-Chem/knime-sstea.svg?branch=master)](https://travis-ci.org/3D-e-Chem/knime-sstea)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/ac1953c0defd4b81bd0c12c37cede85f)](https://www.codacy.com/app/3D-e-Chem/knime-sstea?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=3D-e-Chem/knime-sstea&amp;utm_campaign=Badge_Grade)
[![DOI](https://zenodo.org/badge/19641/3D-e-Chem/knime-sstea.svg)](https://zenodo.org/badge/latestdoi/19641/3D-e-Chem/knime-sstea)

# Installation

Requirements:

* KNIME, https://www.knime.org

Steps install ss-TEA KNIME node:

1. Goto Help > Install new software ... menu
2. Press add button
3. Fill text fields with `https://3d-e-chem.github.io/updates`
4. Select --all sites-- in work with pulldown
5. Open KNIME 3D-e-Chem Contributions folder
6. Select ss-TEA
7. Install software & restart

# Usage

See example workflow at [examples/ss-TEA-example.zip](examples/ss-TEA-example.zip).

It can be run by importing it into KNIME as an archive.

# Build

```
mvn verify
```

Jar has been made in `/target` folder.
An Eclipse update site will be made in `p2/target/repository` repository.

# Development

Steps to get development environment setup based on https://github.com/knime/knime-sdk-setup#sdk-setup:

1. Install Java 8
2. Install Eclipse for [RCP and RAP developers](https://www.eclipse.org/downloads/packages/release/2018-12/r/eclipse-ide-rcp-and-rap-developers)
3. Configure Java 8 inside Eclipse Window > Preferences > Java > Installed JREs
4. Import this repo as an Existing Maven project
5. Activate target platform by going to Window > Preferences > Plug-in Development > Target Platform and check the `KNIME Analytics Platform (4.0) - nl.esciencecenter.e3dchem.knime.sstea.targetplatform/KNIME-AP-4.0.target` target definition.

During import the Tycho Eclipse providers must be installed.

## Tests

Tests for the node are in `tests/src` directory.
Tests can be executed with `mvn verify`, they will be run in a separate Knime environment.

### Unit tests

Unit tests written in Junit4 format can be put in `tests/src/java`.

### Workflow tests

See https://github.com/3D-e-Chem/knime-testflow#3-add-test-workflow

# New release

1. Update versions in pom files with `mvn org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=<version>` command.
2. Manually update version of "source" feature in `p2/category.xml` file.
3. Commit and push changes
3. Create package with `mvn package`, will create update site in `p2/target/repository`
4. Append new release to 3D-e-Chem update site
  1. Make clone of https://github.com/3D-e-Chem/3D-e-Chem.github.io repo
  2. Append release to 3D-e-Chem update site with `mvn install -Dtarget.update.site=<3D-e-Chem repo/updates>`
5. Commit and push changes in this repo and 3D-e-Chem.github.io repo
6. Make nodes available to 3D-e-Chem KNIME feature by following steps at https://github.com/3D-e-Chem/knime-node-collection#new-release
