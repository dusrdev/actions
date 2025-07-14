# .NET Reusable GitHub Workflows

This repository hosts reusable GitHub workflows to simplify running .NET clean, build, and unit tests on various platforms and configurations.

## Available Workflows

- **reusable-dotnet-test.yaml**: Base workflow that executes `dotnet clean`, `dotnet restore`, `dotnet build`, and `dotnet test` for a given test project on a single platform.
- **reusable-dotnet-test-mtp.yaml**: same thing just used `dotnet run` to work with MTP (Microsoft Testing Platform)

## Workflow Details

### reusable-dotnet-test.yaml & reusable-dotnet-test-mtp.yaml

#### Inputs

| Name               | Description                                                         | Required | Type   |
|--------------------|---------------------------------------------------------------------|----------|--------|
| `platform`         | The platform to run the tests on (e.g., `ubuntu-latest`)            | true     | string |
| `dotnet-version`   | The version of dotnet to use (e.g., `9.0.x`)                        | true     | string |
| `test-project-path`| The path to the test project                                        | true     | string |

## Usage

Include one of the workflows in your own `.github/workflows/*.yaml` file:

```yaml
jobs:
  test:
    uses: dusrdev/actions/.github/workflows/reusable-dotnet-test.yaml@main
    with:
      platform: ubuntu-latest
      dotnet-version: 9.0.x
      test-project-path: path/to/YourProject.Tests.csproj
```

## Contributing

Contributions are welcome! Please open issues and submit pull requests.
