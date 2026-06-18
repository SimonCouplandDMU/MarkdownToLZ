## Code

Markdown supports inline code and code blocks with syntax highlighting.

---

### Inline code

You can highlight short snippets like this:

`print("Hello World")`

---

### Basic code block

```python
print("Hello World")
```

### Longer examples

Python

```python
class Student:
    def __init__(self, name: str, marks: list[int]):
        self.name = name
        self.marks = marks

    def average(self) -> float:
        return sum(self.marks) / len(self.marks)

    def grade(self) -> str:
        avg = self.average()
        if avg >= 70:
            return "First"
        elif avg >= 60:
            return "Upper Second"
        elif avg >= 50:
            return "Lower Second"
        else:
            return "Fail"


students = [
    Student("Alice", [70, 75, 80]),
    Student("Bob", [55, 60, 58]),
    Student("Charlie", [40, 45, 50])
]

for s in students:
    print(f"{s.name}: {s.average():.2f} → {s.grade()}")
```

Java

```java
public class Student {
    private String name;
    private int[] marks;

    public Student(String name, int[] marks) {
        this.name = name;
        this.marks = marks;
    }

    public double average() {
        int sum = 0;
        for (int mark : marks) {
            sum += mark;
        }
        return (double) sum / marks.length;
    }

    public String grade() {
        double avg = average();

        if (avg >= 70) return "First";
        else if (avg >= 60) return "Upper Second";
        else if (avg >= 50) return "Lower Second";
        else return "Fail";
    }

    public static void main(String[] args) {
        Student s = new Student("Alice", new int[]{70, 75, 80});
        System.out.println(s.name + ": " + s.average() + " → " + s.grade());
    }
}
```

C++

```cpp
#include <iostream>
#include <vector>
#include <numeric>
#include <string>

class Student {
private:
    std::string name;
    std::vector<int> marks;

public:
    Student(const std::string& name, const std::vector<int>& marks)
        : name(name), marks(marks) {}

    double average() const {
        int sum = std::accumulate(marks.begin(), marks.end(), 0);
        return static_cast<double>(sum) / marks.size();
    }

    std::string grade() const {
        double avg = average();

        if (avg >= 70) return "First";
        else if (avg >= 60) return "Upper Second";
        else if (avg >= 50) return "Lower Second";
        else return "Fail";
    }

    void print() const {
        std::cout << name << ": " << average() << " → " << grade() << std::endl;
    }
};

int main() {
    Student s("Alice", {70, 75, 80});
    s.print();
    return 0;
}
```