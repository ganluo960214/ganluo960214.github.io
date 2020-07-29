更新UE使用C++标准方式

修改文件:

*.Target.cs
```c#
// Copyright Epic Games, Inc. All Rights Reserved.

using UnrealBuildTool;
using System.Collections.Generic;

public class ProjectTarget : TargetRules
{
	public ProjectTarget( TargetInfo Target) : base(Target)
	{
		Type = TargetType.Game;
		DefaultBuildSettings = BuildSettingsVersion.V2;
		ExtraModuleNames.AddRange( new string[] { "Project" } );

		// add CppStandard begin
		CppStandard = CppStandardVersion.Cpp17;
		// add CppStandard end
	}
}
```

*Editor.Target.cs
```c#
// Copyright Epic Games, Inc. All Rights Reserved.

using UnrealBuildTool;
using System.Collections.Generic;

public class ProjectEditorTarget : TargetRules
{
	public ProjectEditorTarget( TargetInfo Target) : base(Target)
	{
		Type = TargetType.Editor;
		DefaultBuildSettings = BuildSettingsVersion.V2;
		ExtraModuleNames.AddRange( new string[] { "Project" } );

		// add CppStandard begin
		bOverrideBuildEnvironment = true;
		CppStandard = CppStandardVersion.Cpp17;
		// add CppStandard end
	}
}
```

Source/*.Build.cs
```c#
// Copyright Epic Games, Inc. All Rights Reserved.

using UnrealBuildTool;

public class Project : ModuleRules
{
	public Project(ReadOnlyTargetRules Target) : base(Target)
	{
		PCHUsage = PCHUsageMode.UseExplicitOrSharedPCHs;

		PublicDependencyModuleNames.AddRange(new string[] { "Core", "CoreUObject", "Engine", "InputCore" });

		PrivateDependencyModuleNames.AddRange(new string[] {  });

		// Uncomment if you are using Slate UI
		// PrivateDependencyModuleNames.AddRange(new string[] { "Slate", "SlateCore" });

		// Uncomment if you are using online features
		// PrivateDependencyModuleNames.Add("OnlineSubsystem");

		// To include OnlineSubsystemSteam, add it to the plugins section in your uproject file with the Enabled attribute set to true

		// add CppStandard begin
		CppStandard = CppStandardVersion.Cpp17;
		// add CppStandard end
	}
}

```

更改项目VS属性

NMake -> IntelliSense -> Additional Options : /std:c++17
