# FMITest
Library of Modelica models to test connected FMUs in a Modelica tool

Library FMITest is a Modelica package providing models to test connected FMUs (Functional Mockup Units), especially during event iteration and during initializaton. The connection classes are structured in packages in different categories according to the underlying basic difficulty (such as "package LinearSystems: linear systems of equations occur over the connected FMUs").

All examples are organized in packages. The details of an example are given in the package description text or package documentation but not in the models in the package. Every package has the following structure:

- *Reference* is the underlying Modelica model that shall be simulated and that can be successfully simulated in a Modelica tool.

- *WithFMUsReference* is the same model as Reference but it is re-structured so that the structure corresponds to the one when replacing some of the components with FMUs. These are still pure Modelica models and should simulate successfully in any Modelica tool. The components of this model that shall be exported as FMUs are store in the sub-package FMUModels. All models stored here shall be exported as FMUs.

- *WithFMUs* is the same model as WithFMUsReference but some of the component instances (marked in the icon with the text "toFMU") are replaced by imported FMUs. Since importing is tool dependent, the version here just provides a copy of WithFMUsReference at this place and the tester has to replace the marked component instances with FMUs imported with the underlying used tool.

The tests are mostly provided for *FMI-for-ModelExchange*. The tests of *FMITest.SimpleConnections*
should also work for *FMI-for-CoSimulation*.