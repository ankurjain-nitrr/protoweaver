# ProtoWeaver

ProtoWeaver is a versatile CLI tool designed to streamline the development workflow for Protocol Buffer (protobuf) based projects. It simplifies code generation, compilation, and management across multiple domains and languages.

## Features

- **Multi-language Support**: Generate code for multiple programming languages from your .proto files.
- **Domain Management**: Easily manage and build separate domains within your protobuf project.
- **Dependency Handling**: Automatically resolve and manage dependencies between different domains.
- **Linting**: Ensure your .proto files adhere to best practices with built-in linting capabilities.
- **Flexible Configuration**: Customize your build process with a simple YAML configuration file.
- **gRPC Integration**: Seamless support for gRPC code generation across all supported languages.


To install ProtoWeaver, follow these steps:

1. Ensure you have Go 1.16 or later installed on your system.
2. Run the following command to install ProtoWeaver:
   ```
   go install github.com/yourusername/protoweaver@latest
   ```

Alternatively, you can build from source:

1. Clone the ProtoWeaver repository:
   ```
   git clone https://github.com/yourusername/protoweaver.git
   ```
2. Navigate to the ProtoWeaver directory:
   ```
   cd protoweaver
   ```
3. Build the ProtoWeaver binary:
   ```
   go build -o protoweaver
   ```
4. (Optional) Move the binary to a directory in your PATH for easy access:
   ```
   sudo mv protoweaver /usr/local/bin/
   ```

# Configuration

```
# ProtoWeaver Configuration Template

# Global settings
gen_dir: "./gen"  # Base directory for generated code
proto_dir: "./proto"  # Directory containing .proto files

# List of domains in your project
domains:
  - user
  - product
  - order

# Language-specific settings
languages:
  java:
    enabled: true  # Whether to generate Java code
    version: "11"  # Java version to target
    output_dir: "${gen_dir}/java
    package: "com.yourorg.yourproject"

  go:
    enabled: true
    output_dir: "${gen_dir}/go"
    options:
      grpc: true
      go_package_prefix: "github.com/yourorg/yourproject"  # Go package prefix

  python:
    enabled: false
    output_dir: "${gen_dir}/python/

  # Add more languages as needed
  # typescript:
  #   enabled: false
  #   output_dir: "${gen_dir}/ts"


# Linting options
lint:
  enabled: true
  rules:
    - ENUM_NAMES_UPPER_SNAKE_CASE
    - FIELD_NAMES_LOWER_SNAKE_CASE
    - SERVICE_NAMES_UPPER_CAMEL_CASE
```

Save this configuration as `protoweaver.yaml` in your project root directory.

## Usage

To use ProtoWeaver, run the following command in your project directory:

```
protoweaver generate
```

This will generate code for all enabled languages based on your .proto files and configuration.

For more options and commands, run:

```
protoweaver --help
```

## License

This project is licensed under the MIT License. See the LICENSE file for details.

