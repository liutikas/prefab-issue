# Example of missing AGP prefab task dependencies

The following command should succeed without any errors/warnings:
```
./gradlew nativelib:bundleDebugLocalLintAar nativelib:prefabDebugConfigurePackage
```

but instead it shows:
```
> Task :nativelib:bundleDebugLocalLintAar
Execution optimizations have been disabled for task ':nativelib:bundleDebugLocalLintAar' to ensure correctness due to the following reasons:
  - Gradle detected a problem with the following location: '/ssd/ssd1/temp/PrefabIssue/nativelib/build/intermediates/prefab_package/debug/prefab'. Reason: Task ':nativelib:bundleDebugLocalLintAar' uses this output of task ':nativelib:prefabDebugConfigurePackage' without declaring an explicit or implicit dependency. This can lead to incorrect results being produced, depending on what order the tasks are executed. Please refer to https://docs.gradle.org/7.2/userguide/validation_problems.html#implicit_dependency for more details about this problem.
```

Another command should succeed also without any errors/warnings:
```
./gradlew nativelib:bundleReleaseAar nativelib:prefabReleaseConfigurePackage
```

but instead it shows:
```
> Task :nativelib:prefabReleaseConfigurePackage
Execution optimizations have been disabled for task ':nativelib:prefabReleaseConfigurePackage' to ensure correctness due to the following reasons:
  - Gradle detected a problem with the following location: '/ssd/ssd1/temp/PrefabIssue/nativelib/build/intermediates/prefab_package/release/prefab/prefab.json'. Reason: Task ':nativelib:bundleReleaseAar' uses this output of task ':nativelib:prefabReleaseConfigurePackage' without declaring an explicit or implicit dependency. This can lead to incorrect results being produced, depending on what order the tasks are executed. Please refer to https://docs.gradle.org/7.2/userguide/validation_problems.html#implicit_dependency for more details about this problem.

```
