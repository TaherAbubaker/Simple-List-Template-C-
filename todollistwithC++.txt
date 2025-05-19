#include <iostream>
using namespace std;

template <class T>
class list {
public:
    const int maxsize = 100;
    T entry[100]; // fixed size
    int count = 0;

    void insert(int pos, T val) {
        if (pos < 0 || pos > count) {
            throw runtime_error("pos is out of range");
        }
        if (count == maxsize) {
            throw runtime_error("list is full");
        }
        for (int i = count; i > pos; i--) {
            entry[i] = entry[i - 1];
        }
        entry[pos] = val;
        count++;
    }

    void insertrand(int n) {
        if (count + n > maxsize) {
            throw runtime_error("list is full");
        }
        for (int i = 0; i < n; i++) {
            insert(count, rand()); // insert at the end
        }
    }

    void remove(int pos) {
        if (empty()) {
            throw runtime_error("list is empty");
        }
        if (pos < 0 || pos >= count) {
            throw runtime_error("pos is out of range");
        }
        for (int i = pos; i < count - 1; i++) {
            entry[i] = entry[i + 1];
        }
        count--;
    }

    bool empty() const {
        return count == 0;
    }

    int size() const {
        return count;
    }

    T getitem(int pos) const {
        if (empty()) {
            throw runtime_error("list is empty");
        }
        if (pos < 0 || pos >= count) {  // Use >= not > for 0-indexed
            throw runtime_error("pos is out of range");
        }
        return entry[pos];
    }

    bool contains(T val){
        if (empty()) {
            throw runtime_error("list is empty");
        }
        for (int i = 0; i<count;i++){
            if (entry[i] == val) return true;
        }
        return false;
    }

    int find(T val) const{
        if (empty()) {
            throw runtime_error("list is empty");
        }
        for (int i = 0; i<count;i++){
            if (entry[i] == val)
             return i;
        }
        return -1;
    }


    void clear() {
    count = 0;
}



    void print() const {
        for (int i = 0; i < count; i++) {
            cout<<entry[i]<<endl;
        }
        cout << endl;
    }
};

int main() {
list<string> todoList;

// Add new tasks
todoList.insert(todoList.size(), "Buy groceries");
todoList.insert(todoList.size(), "Finish homework");
todoList.insert(todoList.size(), "Call mom");

// Insert a task at the top priority
todoList.insert(0, "Pay bills");

// Remove a completed task
int pos = todoList.find("Finish homework");
if (pos != -1) {
    todoList.remove(pos);
}

// Print all tasks
todoList.print();
}
