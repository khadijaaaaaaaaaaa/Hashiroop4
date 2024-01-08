# Hashiroop4

question # 2 part 1

#include <iostream>
#include <vector>
#include <algorithm> // Include the algorithm header

struct Product {
    int id;
    std::string name;
    double price;
};

class Inventory {
private:
    std::vector<Product> products;

public:
    void addProduct(const Product& newProduct) {
        products.push_back(newProduct);
        std::cout << "Product added to the inventory." << std::endl;
    }

    void removeProductById(int productId) {
        auto it = std::remove_if(products.begin(), products.end(),
                                 [productId](const Product& p) { return p.id == productId; });

        if (it != products.end()) {
            products.erase(it, products.end());
            std::cout << "Product removed from the inventory." << std::endl;
        } else {
            std::cout << "Product not found in the inventory." << std::endl;
        }
    }

    void displayInventory() const {
        std::cout << "Inventory:\n";
        for (const auto& product : products) {
            std::cout << "ID: " << product.id << "\tName: " << product.name << "\tPrice: $" << product.price << std::endl;
        }
    }
};

int main() {
    Inventory inventory;

    inventory.addProduct({1, "Laptop", 999.99});
    inventory.addProduct({2, "Smartphone", 499.99});
    inventory.addProduct({3, "Headphones", 79.99});

    inventory.displayInventory();

    inventory.removeProductById(2);

    inventory.displayInventory();

    return 0;
}

part 2

#include <iostream>
#include <vector>
#include <chrono>
#include <algorithm>

void bubbleSort(std::vector<int>& arr) {
    int n = arr.size();
    bool swapped;
    do {
        swapped = false;
        for (int i = 0; i < n - 1; ++i) {
            if (arr[i] > arr[i + 1]) {
                std::swap(arr[i], arr[i + 1]);
                swapped = true;
            }
        }
    } while (swapped);
}

int main() {
    const int size = 100000;
    std::vector<int> data(size);

    for (int i = 0; i < size; ++i) {
        data[i] = size - i;
    }

    auto startTime = std::chrono::high_resolution_clock::now();

    bubbleSort(data);

    auto endTime = std::chrono::high_resolution_clock::now();

    auto duration = std::chrono::duration_cast<std::chrono::microseconds>(endTime - startTime);

    std::cout << "Bubble Sort Execution Time: " << duration.count() << " microseconds\n";

    std::cout << "First 10: ";
    for (int i = 0; i < 10; ++i) {
        std::cout << data[i] << " ";
    }

    std::cout << "\nLast 10: ";
    for (int i = size - 10; i < size; ++i) {
        std::cout << data[i] << " ";
    }

    return 0;
}

second code 

#include <iostream>
#include <vector>
#include <algorithm>
#include <chrono>

int main() {
    const int size = 100000;
    std::vector<int> data(size);

    for (int i = 0; i < size; ++i) {
        data[i] = size - i;
    }

    auto startTime = std::chrono::high_resolution_clock::now();

    std::sort(data.begin(), data.end());

    auto endTime = std::chrono::high_resolution_clock::now();

    auto duration = std::chrono::duration_cast<std::chrono::microseconds>(endTime - startTime);

    std::cout << "STL Sort Execution Time: " << duration.count() << " microseconds\n";

    std::cout << "First 10: ";
    for (int i = 0; i < 10; ++i) {
        std::cout << data[i] << " ";
    }

    std::cout << "\nLast 10: ";
    for (int i = size - 10; i < size; ++i) {
        std::cout << data[i] << " ";
    }

    return 0;
}

