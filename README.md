# c-plus-plus-nested-template-example
c++ template nested

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
