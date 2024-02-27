#include <iostream>

using namespace std;

struct list {
    int number;
    list* next;
    list* prev;
};
struct list* top;

void push(int number) {
    struct list* tmp = new list;
    tmp->number = number;
    tmp->next = top;
    tmp->prev = NULL;
    if (top != NULL) top->prev = tmp;
    top = tmp;
}

void pop() {
    struct list* tmp;
    if (top == NULL) exit(1);
    tmp = top;
    if (top->next != NULL)top->next->prev = NULL;
    top = top->next;
    tmp->next = NULL;
    tmp->prev = NULL;
    free(tmp);
}

void partition(int n, int depth, int* size)
{
    int sum = 0;
    struct list* temp = top;
    for (unsigned i = 0; i < *size; i++) {
        sum += temp->number;
        temp = temp->next;
    }

    if (n == sum) {
        struct list* temp = top;
        for (int i = 0; i < *size - 1; i++) {
            temp = temp->next;
        }
        cout << temp->number;
        temp = temp->prev;
        for (int i = 1; i < *size; i++) {
            cout << "+" << temp->number;
            temp = temp->prev;
        }
        pop();
        (*size)--;
        cout << "\n";
    }
    else {
        if (sum < n) {
            for (int i = 2; i <= depth; i++)
            {
                bool prime = true;
                for (int j = 2; j < i; j++)
                    if (i % j == 0)
                        prime = false;
                if (!prime) continue;
                push(i);
                (*size)++;
                partition(n, i, size);
            }
            if (*size != 0) {
                pop();
                (*size)--;
            }
        }
        else {
            pop();
            (*size)--;
        }
    }
}

int main()
{
    int x;
    int n, k;
    cin >> x;
    for (int i = 0; i < x; i++)
    {
        cin >> n;
        cin >> k;
   
        bool prime = true;
        if (n == 1)
            continue;
        for (int j = 2; j < k; j++)
            if (k % j == 0)
                prime = false;
        if (!prime) continue;
        push(k);
        int size = 1;
        partition(n,k, &size);
    }
}
