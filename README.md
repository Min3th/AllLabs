// StackArray //Implementing a Stack with the use of arrays #include #include using namespace std; using namespace std::chrono;

#define SIZE 10 int arr[SIZE]; int top = -1;

bool isEmpty() { if(top==-1) return true; else return false; }

void Pop() { if(isEmpty()) cout<<"Stack Underflow"<<endl; else top--; }

void StackTop() { if(isEmpty()) cout<<"Stack is empty!"<<endl; else cout<<"Element at top is: "<<arr[top]<<endl;

}

void isFull() { if(top==SIZE-1) { cout<<"Stack Overflow"<<endl; exit(1); } }

void Push(int value) { isFull();

top++; arr[top]=value;

}

void Display() { if(isEmpty()) { cout<<"Stack is empty"<<endl; } else { for(int i=0 ; i<=top; i++) cout<<arr[i]<<" "; cout<<endl;

}

}

int main() {

auto start = high_resolution_clock::now();

Push(8); Push(10); Push(5); Push(11); Push(15); Push(23); Push(6); Push(18); Push(20); Push(17); Display(); Pop(); Pop(); Pop(); Pop(); Pop(); Display(); Push(4); Push(30); Push(3); Push(1); Display();

auto stop = high_resolution_clock::now();

auto duration = duration_cast(stop - start);

cout << "Time taken by function: "
     << duration.count() << " microseconds" << endl;
}





// StackLinkedlist //Implementing a stack with the use of a Linkedlist

#include #define SIZE 10 #include using namespace std; using namespace std::chrono;

struct Node { int data;

Node *link; }; Node *top = NULL;

bool isEmpty() { if(top == NULL){ return true; }

else{ return false; }

}

bool isFull(int StackSize) { struct Node* ptr = top; int count = 0; while (ptr != NULL) { count++; ptr = ptr->link; } if (count >= StackSize) { return true; } }

void Push (int value) {

//if isFull(SIZE){
  //  cout<<"Stack overflow";
   // exit(1);
// } //else{ Node *ptr = new Node(); ptr->data = value; ptr->link = top; top = ptr; }

//}

//Function to delete an element from the stack void Pop ( ) {

if ( isEmpty() ) cout<<"Stack underflow"; else { Node *ptr = top; top = top -> link; delete(ptr); } }

// Function to show the element at the top of the stack void StackTop() { if ( isEmpty() ) cout<<"Stack is Empty"; else cout<<"Element at top is : "<< top->data; }

// Function to Display the stack void Display() { if ( isEmpty() ) cout<<"Stack is Empty"; else { Node *temp=top; while(temp!=NULL) { cout<data<<" "; temp=temp->link; } cout<<"\n"; } }

// Main function int main() {

auto start = high_resolution_clock::now();

Push(8); Push(10); Push(5); Push(11); Push(15); Push(23); Push(6); Push(18); Push(20); Push(17); Display(); Pop(); Pop(); Pop(); Pop(); Pop(); Display(); Push(4); Push(30); Push(3); Push(1); Display();

auto stop = high_resolution_clock::now();

auto duration = duration_cast(stop - start);

cout << "Time taken by function: "
     << duration.count() << " microseconds" << endl;
return 0; }






#include using namespace std;

struct node { int key; struct node *left, *right; };

struct node* createNode(int element) { struct node* temp = (struct node*)malloc(sizeof(struct node)); temp->key = element; temp->left = temp->right = NULL; return temp; }

void traverseInOrder(struct node *root) {

if (root != NULL) {
    traverseInOrder(root->left);
    printf("%d ", root->key);
    traverseInOrder(root->right);
}
}

// Insert a node struct node *insertNode(struct node *node, int key) {

if (node == NULL){
    return createNode(key);
}

if (key<node->key){
    node->left = insertNode(node->left,key);
}

else if (key>node -> key){

    node ->right = insertNode(node -> right,key);

}

return node;
}

struct node* minimum(struct node* node) { struct node* current = node;

while (current && current->left != NULL)
    current = current->left;

return current;
}

// Deleting a node struct node *deleteNode(struct node *root, int key) {

if (root== NULL){
    return root;
}


if (key > root -> key){
    root -> right = deleteNode(root->right,key);
}

else if (key < root -> key){
    root -> left = deleteNode(root ->left,key);
}

else{

if (root->left == NULL
         && root->right == NULL){

            return NULL;
         }
else if (root->left = NULL){

    struct node*temp = root -> right;
    free(root);
    return temp;
}

else if (root ->right = NULL){

    struct node*temp = root -> left;
    free(root);
    return temp;


}

struct node* temp = minimum(root->right);


    root->key = temp->key;


    root->right = deleteNode(root->right, temp->key);
}

return root;

}

// Driver code int main() { struct node *root = NULL;

int operation; int operand; cin >> operation;

while (operation != -1) { switch(operation) { case 1: // insert cin >> operand; root = insertNode(root, operand); cin >> operation; break; case 2: // delete cin >> operand; root = deleteNode(root, operand); cin >> operation; break; default: cout << "Invalid Operator!\n"; return 0; } }

traverseInOrder(root); }








#include using namespace std;

// function to heapify the tree void heapify(int arr[], int n, int root) { int largest = root; int a = 2 * root + 1; int b = 2 * root + 2;

if (a < n && arr[a] > arr[largest])
    largest = a;


if (b < n && arr[b] > arr[largest])
    largest = b;


if (largest != root) {
    swap(arr[root], arr[largest]);


    heapify(arr, n, largest);
}
}

// implementing heap sort void heapSort(int arr[], int n) { for (int j = n / 2 - 1; j >= 0; j--) heapify(arr, n, j);

for (int j = n - 1; j >= 0; j--) {

    swap(arr[0], arr[j]);


    heapify(arr, j, 0);
}
}

/* print contents of array */ void displayArray(int arr[], int n) { for (int i=0; i<n; ++i) cout << arr[i] << " "; cout << "\n"; }

// main program int main() { int heap_arr[] = {4,17,3,12,9,6}; int n = sizeof(heap_arr)/sizeof(heap_arr[0]); cout<<"Input array"<<endl; displayArray(heap_arr,n);

heapSort(heap_arr, n);

cout << "Sorted array"<<endl; displayArray(heap_arr, n); }
