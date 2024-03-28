# Assemblies

- Managing assemblies in C#.
  - **The Assembly Manifest:** Each assembly contains a manifest that provides metadata about the assembly, including version information, culture, and information about the resources and types it contains.
  - **Resources and Satellite Assemblies:** Assemblies can embed resources such as images and strings. Satellite assemblies are used to manage resources for different cultures and languages, facilitating localization.
  - **Assembly Loading:** The CLR loads assemblies into an application domain when the application requires them. This process can be controlled and customized through the use of various load methods.
  - **Assembly Resolution:** When an assembly references another assembly, the CLR must resolve the location and version of the referenced assembly. This process can be customized using configuration files or programmatically via the **`AppDomain.AssemblyResolve`** event.
  - **Assembly Load Contexts:** .NET Core introduced the concept of assembly load contexts to provide isolation between different parts of an application and to support dynamic loading and unloading of assemblies.
  - **AssemblyDependencyResolver:** Introduced in .NET Core 3.0, it helps in resolving assembly and native library paths during dynamic loading, based on the dependencies specified in a .deps.json file.
