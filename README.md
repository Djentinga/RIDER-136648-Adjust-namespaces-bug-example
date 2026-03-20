Jetbrains Rider + Godot bug:

As soon as one project depends on the other, auto refactoring namespaces does not work.

Jetbrains debug logs:

```msbuild
08:58:20.016 |V| DaemonImpl                    | :2                 | DaemonStateChanged: C:\Users\Joachim Arting\source\repos\Spaceport Architect\Application\UseCases\Transport\Services\TransportDispatchService.cs IN_PROGRESS_LOCAL_SLOW Running slow analysis. Indicator: WorkingSlow Running slow analysis, Process: LONG_RUNNING_STAGES
08:58:20.016 |V| RiderDaemonHost               | :2                 | DaemonState -> IN_PROGRESS_LOCAL, HighlightingProgressState -> LONG_RUNNING_STAGES, Document: “C:\Users\Joachim Arting\source\repos\Spaceport Architect\Application\UseCases\Transport\Services\TransportDispatchService.cs”
08:58:20.257 |W| SolutionBuilderHost           | :2                 | Fire events
08:58:20.629 |V| AsyncCommitServiceImpl        | :2                 | Execute after commit actions
08:58:21.197 |V| SourceGeneratorMonitor        | Roslyn Host:53     | Start: Queueing new source generated files in 'Spaceport Architect' with target framework 'net10.0'
08:58:21.197 |V| SourceGeneratorMonitor        | Roslyn Host:53     | Start: Processing source generated files in 'Spaceport Architect' with target framework 'net10.0'
08:58:21.197 |V| SourceGeneratorMonitor        | Roslyn Host:53     | Finish: Queueing new source generated files in 'Spaceport Architect' with target framework 'net10.0'
08:58:21.197 |V| SourceGeneratorMonitor        | Roslyn Host:53     | Roslyn source generators were initialized for 'C:\Users\Joachim Arting\source\repos\Spaceport Architect\Spaceport Architect.csproj' [net10.0]
08:58:21.197 |V| SourceGeneratorMonitor        | JetPool(S) #1:9    | Initialized -> True: MonitorInitialized=True && (RoslynDisabled=False || (PendingProjects= && (PendingOperations=Processing source generated files in 'Spaceport Architect' with target framework 'net10.0' && Initialized=True))). Caller=OnOperation
08:58:21.197 |V| SourceGeneratorMonitor        | JetPool(S) #1:9    | UpToDate -> False: MonitorInitialized=True && (RoslynDisabled=False || (PendingProjects= && PendingOperations=Processing source generated files in 'Spaceport Architect' with target framework 'net10.0' && PendingSourceGeneratorsRequests=)). Caller=OnOperation
08:58:21.198 |V| SourceGeneratedFilesProvider  | .NET TP Worker:77  | Build data for C:\Users\Joachim Arting\source\repos\Spaceport Architect\Spaceport Architect.csproj
08:58:21.199 |V| SourceGeneratedFilesProvider  | .NET TP Worker:77  | Removed generated text for Godot.SourceGenerators\Godot.SourceGenerators.ScriptPathAttributeGenerator\Spaceport.Architect.Presentation.Spaceship.ActiveFlightAdapter_ScriptPath.generated.cs in project C:\Users\Joachim Arting\source\repos\Spaceport Architect\Spaceport Architect.csproj
08:58:21.210 |V| ProblemsViewDiagnosticsCollector| Roslyn Host:53     | [Warning] Generator 'ScriptPathAttributeGenerator' failed to generate sources: Generator 'ScriptPathAttributeGenerator' failed to generate source. It will not contribute to the output and compilation errors may occur as a result. Exception was of type 'InvalidOperationException' with message 'Property 'GodotProjectDir' is null or empty.'.
System.InvalidOperationException: Property 'GodotProjectDir' is null or empty.
   at Godot.SourceGenerators.ScriptPathAttributeGenerator.Execute(GeneratorExecutionContext context)
   at Microsoft.CodeAnalysis.SourceGeneratorAdaptor.<Initialize>b__6_5(SourceProductionContext productionContext, GeneratorContextBuilder contextBuilder) in Z:\BuildAgent\work\3b7ce003563d6f8f\src\Compilers\Core\Portable\SourceGeneration\GeneratorAdaptor.cs:line 68
   at Microsoft.CodeAnalysis.UserFunctionExtensions.<>c__DisplayClass3_0`2.<WrapUserAction>b__0(TInput1 input1, TInput2 input2, CancellationToken token) in Z:\BuildAgent\work\3b7ce003563d6f8f\src\Compilers\Core\Portable\SourceGeneration\UserFunction.cs:line 103
-----


System.InvalidOperationException: Property 'GodotProjectDir' is null or empty.
   at Godot.SourceGenerators.ScriptPathAttributeGenerator.Execute(GeneratorExecutionContext context)
   at Microsoft.CodeAnalysis.SourceGeneratorAdaptor.<Initialize>b__6_5(SourceProductionContext productionContext, GeneratorContextBuilder contextBuilder) in Z:\BuildAgent\work\3b7ce003563d6f8f\src\Compilers\Core\Portable\SourceGeneration\GeneratorAdaptor.cs:line 68
   at Microsoft.CodeAnalysis.UserFunctionExtensions.<>c__DisplayClass3_0`2.<WrapUserAction>b__0(TInput1 input1, TInput2 input2, CancellationToken token) in Z:\BuildAgent\work\3b7ce003563d6f8f\src\Compilers\Core\Portable\SourceGeneration\UserFunction.cs:line 103
```
