# reflectable_bug
This repository is just for showing a bug regarding the reflectable package of dart/flutter 


## Steps to reproduce

1. Clone this repository
2. Run `dart pub get`

## Success case

1. Run `dart run build_runner build`
2. Everything works fine and will output this:

```
[INFO] Generating build script completed, took 452ms
[WARNING] Throwing away cached asset graph because the build phases have changed. This most commonly would happen as a result of adding a new dependency or updating your dependencies.
[INFO] Cleaning up outputs from previous builds. completed, took 3ms
[INFO] Generating build script completed, took 105ms
[WARNING] Invalidated precompiled build script due to missing asset graph.
[INFO] Precompiling build script... completed, took 1.1s
[INFO] Building new asset graph completed, took 1.1s
[INFO] Checking for unexpected pre-existing outputs. completed, took 1ms
[INFO] Running build completed, took 2.1s
[INFO] Caching finalized dependency graph completed, took 30ms
[INFO] Succeeded after 2.2s with 1 outputs (6 actions)
```

## Failure case

1. Change the name of the `lib` folder to whatever else, in this case will be `main_dir`
2. Change in build.yaml the `lib` folder to the new name, in this case will be `main_dir`
3. Run `dart run build_runner build`
4. Nothing is going to happen and the build_runner will output this:

```
Built build_runner:build_runner.
[INFO] Generating build script completed, took 311ms
[WARNING] Throwing away cached asset graph because the build phases have changed. This most commonly would happen as a result of adding a new dependency or updating your dependencies.
[INFO] Cleaning up outputs from previous builds. completed, took 4ms
[INFO] Generating build script completed, took 56ms
[WARNING] Invalidated precompiled build script due to missing asset graph.
[INFO] Precompiling build script... completed, took 1.1s
[INFO] Building new asset graph completed, took 870ms
[INFO] Checking for unexpected pre-existing outputs. completed, took 1ms
[INFO] Running build completed, took 4ms
[INFO] Caching finalized dependency graph completed, took 30ms
[INFO] Succeeded after 49ms with 0 outputs (0 actions)
```

Doesn't matter if you change the name of the folder to something else, the build_runner will always output the same thing.