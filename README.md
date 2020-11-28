# flutter-cplusplus-interop
## flutter C++ interop

This source code has more of a C++ class than this tutorial https://flutter.dev/docs/development/platform-integration/c-interop 

```c++
#include <iostream>

using namespace std;

extern "C" {
  __attribute__((visibility("default"))) __attribute__((used))
  class Add {
    public:
      Add() {
        cout << "initial" << endl;
      }

      ~Add() {
        cout << "destroy" << endl;
      }

      int execute(int x, int y) {
        return x + y;
      }
  };

  __attribute__((visibility("default"))) __attribute__((used))
  int32_t native_add(int32_t x, int32_t y) {
    Add* add = new Add();
    int value = add->execute(x, y);
    delete add;
    cout << value << endl;
    return value;
  }
};
```