# open62541pp_vendor

A ROS 2 vendor package for [open62541pp](https://github.com/open62541pp/open62541pp), a C++ wrapper for the open62541 OPC UA library.

## Usage

### 1. `package.xml`

Add a dependency to your `package.xml`:

```xml
<depend>open62541pp_vendor</depend>
```

### 2. `CmakeLists.txt`

```
find_package(open62541pp_vendor REQUIRED)

add_executable(my_node src/node.cpp)

target_link_libraries(my_node open62541pp::open62541pp)
```

### 3. Code

```
#include <open62541pp/server.hpp>
#include <open62541pp/client.hpp>

int main() {
    opcua::Server server;
    return 0;
}
```
## License

This vendor package is licensed under MPL-2.0 to match the upstream open62541pp and open62541 licenses.