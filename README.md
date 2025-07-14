# .NET Reusable GitHub Workflows

This repository hosts reusable GitHub workflows to simplify running .NET clean, build, and unit tests on various platforms and configurations.

## Available Workflows

- **reusable-dotnet-test.yaml**: Base workflow that executes `dotnet clean`, `dotnet restore`, `dotnet build`, and `dotnet test` for a given test project on a single platform and configuration.
- **reusable-dotnet-test-ubuntu.yaml**: Workflow that calls `reusable-dotnet-test.yaml` with `ubuntu-latest` and `Release` configuration.
- **reusable-dotnet-test-matrix.yaml**: Workflow that calls `reusable-dotnet-test.yaml` across a matrix of platforms (`ubuntu-latest`, `windows-latest`, `macos-latest`) and configurations (`Debug`, `Release`).

## Workflow Details

### reusable-dotnet-test.yaml

#### Inputs

| Name               | Description                                                         | Required | Type   |
|--------------------|---------------------------------------------------------------------|----------|--------|
| `platform`         | The platform to run the tests on (e.g., `ubuntu-latest`)            | true     | string |
| `configuration`    | The build configuration (e.g., `Debug`, `Release`)                  | true     | string |
| `test-project-path`| The path to the test project                                        | true     | string |

### reusable-dotnet-test-ubuntu.yaml

#### Inputs

| Name               | Description                           | Required | Type   |
|--------------------|---------------------------------------|----------|--------|
| `test-project-path`| The path to the test project          | true     | string |

### reusable-dotnet-test-matrix.yaml

#### Inputs

| Name               | Description                           | Required | Type   |
|--------------------|---------------------------------------|----------|--------|
| `test-project-path`| The path to the test project          | true     | string |

## Usage

Include one of the workflows in your own `.github/workflows/*.yaml` file:

```yaml
jobs:
  test:
    uses: dusrdev/actions/.github/workflows/reusable-dotnet-test.yaml@main
    with:
      platform: ubuntu-latest
      configuration: Release
      test-project-path: path/to/YourProject.Tests.csproj
```

```yaml
jobs:
  test:
    uses: dusrdev/actions/.github/workflows/reusable-dotnet-test-ubuntu.yaml@main
    with:
      test-project-path: path/to/YourProject.Tests.csproj
```

```yaml
jobs:
  test:
    uses: dusrdev/actions/.github/workflows/reusable-dotnet-test-matrix.yaml@main
    with:
      test-project-path: path/to/YourProject.Tests.csproj
```

## Contributing

Contributions are welcome! Please open issues and submit pull requests.
