# c-plus-plus-nested-template-example
Place holder for a useful snippet, a I invariably always struggle to
get this syntax correct. Hope it helps someone else.

```C++
#include <iostream>
#include <list>

template <typename T, template <typename, typename> class C>
class C2 {
  private:
    typedef C<T, std::allocator<T> > C1;
    C1 container;
  public:
    void push(T& item) {
        container.push_back(item);
    }

    T pop (void) {
        T item = container.front();
        container.pop_front();
        return item;
    }
};

int main() {
    int i = 1;
    C2<int, std::list > c;
    c.push(i);
    std::cout << c.pop() << std::endl;
}
```

And the equivalent to the above, but using value_type

```
#include <iostream>
#include <list>

template <typename T>
class C1 {
  private:
    T container;
    typedef typename T::value_type CT;
  public:
    void push(CT& item) {
        container.push_back(item);
    }

    CT pop (void) {
        CT item = container.front();
        container.pop_front();
        return item;
    }
};

int main() {
    int i = 1;
    C1<std::list<int> > c;
    c.push(i);
    std::cout << c.pop() << std::endl;
}
```
