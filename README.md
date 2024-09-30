# ProtoWeaver

ProtoWeaver is a versatile CLI tool designed to streamline the development workflow for Protocol Buffer (protobuf) based projects. It simplifies code generation, compilation, and management across multiple domains and languages.

## Features

- **Multi-language Support**: Generate code for multiple programming languages from your .proto files.
- **Domain Management**: Easily manage and build separate domains within your protobuf project.
- **Dependency Handling**: Automatically resolve and manage dependencies between different domains.
- **Linting**: Ensure your .proto files adhere to best practices with built-in linting capabilities.
- **Flexible Configuration**: Customize your build process with a simple YAML configuration file.

## Installation

To install ProtoWeaver, follow these steps:

1. Ensure you have Go 1.16 or later installed on your system.
2. Clone the ProtoWeaver repository:
   ```
   git clone https://github.com/yourusername/protoweaver.git
   ```
3. Navigate to the ProtoWeaver directory:
   ```
   cd protoweaver
   ```
4. Build the ProtoWeaver binary:
   ```
   go build -o protoweaver
   ```
5. (Optional) Move the binary to a directory in your PATH for easy access:
   ```
   sudo mv protoweaver /usr/local/bin/
   ```

# Configuration

```
# ProtoWeaver Configuration Template

# Global settings
gen_dir: "./gen"  # Base directory for generated code
proto_dir: "./proto"  # Directory containing .proto files
buf_enabled: true  # Whether to use buf for proto management (optional)

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
    output_dir: "${gen_dir}/java"  # Output directory for Java code
    options:
      grpc: true  # Whether to generate gRPC code
      lite: false  # Whether to use protobuf-lite

  go:
    enabled: true
    output_dir: "${gen_dir}/go"
    options:
      grpc: true
      go_package_prefix: "github.com/yourorg/yourproject"  # Go package prefix

  python:
    enabled: false
    output_dir: "${gen_dir}/python"
    options:
      grpc: false
      mypy_enabled: true  # Whether to generate mypy stubs

  # Add more languages as needed
  # typescript:
  #   enabled: false
  #   output_dir: "${gen_dir}/ts"
  #   options:
  #     grpc-web: true

# Linting options
lint:
  enabled: true
  rules:
    - ENUM_NAMES_UPPER_SNAKE_CASE
    - FIELD_NAMES_LOWER_SNAKE_CASE
    - SERVICE_NAMES_UPPER_CAMEL_CASE

# Compilation options (if applicable)
compile:
  java:
    enabled: true
    target_dir: "${gen_dir}/java/classes"
```


