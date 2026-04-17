# LUnit Coverage Analysis

This LUnit add-on adds coverage analysis to LUnit.
In LUnit versions prior to 2.0, there was rudimentary coverage analysis functions included in the framework.
As of version 2.0, these features have been migrated into this new project to allow it to live independently of the main framework.
The functionality and useabilty was also improved on significantly.
The add-on also enables report genration using the Cobertura xml format.

## Installation

Released versions are available from VIPM and are installed as regular packages.
Since this is a free standing add-on to LUnit, it requires LUnit to be installed.
Pre-release versions are available on GitHub and are genereated for each tagged version.

Once the add-on is installed, it is activated through the LUnit `Tools->Reporting...` menu.

## Configuration

The add-on allows for configuration of VI:s to measure.
It is required that the VI:s are configured to have Debugging enabled for the measurement to work.
In the Reporting configuration dialog, select Configure to open up the configuration dialog.
In the window, you can select which VI:s you want to measure coverage for and the list is saved as a text file called coverage_include.txt.
The path to the file is calculated from the location of the test case classes and cannot be changed. 
This is to ensure that the file can be located even if called from the CLI outside the context of a project.

## Result View

If enabled from the configuration window, a result view will show the coverage as a percentage for each VI which has been selected for measurement.
The result view shows a the VI:s in the project tree and VI:s can be opened through double clicking on them.

## XML Report

An XML report can be generated using the Cobertura XML format, to be digested by any common continuous integration (CI) system.
To activate the report format using the [LUnit CLI](https://github.com/astemes/astemes-lunit-cli), you need the add-on installed on the CI runner.
You then need to pass the report format as a custom report using the LUnit CLI, as described in documentation. 
Below is an example where the coverage report and the native xml report are both generated into the *c:\logs* directory by passing the arguments `-CustomReports "XML Report,Coverage Report"`.

```
LabVIEWCLI -OperationName LUnit -ProjectPath c:\tests -ReportPath c:\logs -CustomReports "XML Report,Coverage Report"
```
