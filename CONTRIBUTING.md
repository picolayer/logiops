# Contributing to LogiOps

Thank you for your interest in contributing to LogiOps! This document provides guidelines and instructions for contributing to the project.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/logiops.git
   cd logiops
   git submodule update --init --recursive
   ```
3. **Create a new branch** for your feature or fix:
   ```bash
   git checkout -b feature/my-feature
   ```

## Development Setup

### Build Requirements

Ensure you have the following dependencies installed for your distribution:

**Arch Linux:**
```bash
sudo pacman -S base-devel cmake libevdev libconfig systemd-libs glib2
```

**Debian/Ubuntu:**
```bash
sudo apt install build-essential cmake pkg-config libevdev-dev libudev-dev libconfig++-dev libglib2.0-dev clang-format clang-tidy
```

**Fedora:**
```bash
sudo dnf install cmake libevdev-devel systemd-devel libconfig-devel gcc-c++ glib2-devel clang-tools-extra
```

### Building Locally

```bash
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_FLAGS="-Werror" ..
cmake --build . -j$(nproc)
```

For development with warnings-as-errors disabled:
```bash
cmake -DCMAKE_BUILD_TYPE=Debug ..
cmake --build .
```

## Code Style

This project follows specific style guidelines to maintain consistency:

### Formatting

The project uses **clang-format** for automatic code formatting. Before submitting a pull request, ensure your code is properly formatted:

```bash
find src -name '*.cpp' -o -name '*.h' | xargs clang-format -i
```

Or format a specific file:
```bash
clang-format -i src/logid/Device.cpp
```

### Static Analysis

The project uses **clang-tidy** for static code analysis. Run it on your changes:

```bash
cd build
cmake -DCMAKE_EXPORT_COMPILE_COMMANDS=ON ..
cmake --build .
run-clang-tidy -p . ../src/logid/YourFile.cpp
```

Or check all modified files:
```bash
run-clang-tidy -p . ../src/logid/
```

### Code Guidelines

- Use C++20 features appropriately
- Prefer `const` correctness
- Avoid raw pointers when possible; use smart pointers
- Keep functions small and focused
- Write clear, descriptive variable and function names
- Add comments for complex logic
- Follow the existing code structure and patterns

### EditorConfig

This project includes an `.editorconfig` file. If your editor supports it, it will automatically configure indentation and line endings. Most modern editors (VS Code, CLion, Sublime, etc.) support EditorConfig natively.

## Making Changes

1. **Make your changes** in your feature branch
2. **Test your changes** by building and running the application:
   ```bash
   cd build
   cmake --build .
   ```
3. **Check for code quality issues**:
   ```bash
   # Format your code
   clang-format -i src/logid/YourFile.cpp
   
   # Run static analysis (if possible with your setup)
   # run-clang-tidy -p . ../src/logid/YourFile.cpp
   ```

## Submitting a Pull Request

1. **Push your changes** to your fork:
   ```bash
   git push origin feature/my-feature
   ```
2. **Create a Pull Request** on GitHub with a clear description of:
   - What changes you made
   - Why you made them
   - How to test the changes
   - Any related issues

3. **Ensure CI passes**: GitHub Actions will automatically run tests on your PR

### PR Guidelines

- Keep PRs focused on a single feature or fix
- Provide a clear, descriptive title
- Reference any related issues
- Update documentation if needed
- Ensure code is formatted and passes basic quality checks

## Testing

If you've added new features or fixed bugs, consider:
- Testing on multiple Linux distributions (Ubuntu, Fedora, Arch)
- Testing with different Logitech devices if possible
- Checking for memory leaks and issues with sanitizers during development

## Reporting Issues

When reporting bugs, please include:
- Your distribution and version
- Logitech device model(s)
- Steps to reproduce
- Expected vs. actual behavior
- Relevant log output or error messages

## Code Review

All contributions go through code review. Reviewers may request:
- Changes for consistency
- Better documentation
- Performance improvements
- Additional test coverage

Please be receptive to feedback and willing to iterate on your changes.

## License

By contributing to LogiOps, you agree that your contributions will be licensed under the same license as the project (see LICENSE file).

## Questions?

Feel free to:
- Open an issue for questions
- Check existing issues and pull requests
- Review the project README and wiki for more information

Thank you for contributing to LogiOps!
