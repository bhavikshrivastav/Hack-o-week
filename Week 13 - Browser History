#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Colors
#define RESET   "\033[0m"
#define RED     "\033[1;31m"
#define GREEN   "\033[1;32m"
#define YELLOW  "\033[1;33m"
#define CYAN    "\033[1;36m"

// Stack Node
struct Node {
    char url[100];
    struct Node* next;
};

// Two stacks
struct Node* backStack = NULL;
struct Node* forwardStack = NULL;
char current[100] = "Home";

// Push
void push(struct Node** top, char url[]) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    strcpy(newNode->url, url);
    newNode->next = *top;
    *top = newNode;
}

// Pop
char* pop(struct Node** top) {
    if (*top == NULL) return NULL;

    struct Node* temp = *top;
    *top = temp->next;

    char* url = (char*)malloc(100);
    strcpy(url, temp->url);

    free(temp);
    return url;
}

// Visit new page
void visit(char url[]) {
    push(&backStack, current);  // save current to back stack
    strcpy(current, url);

    // clear forward stack
    while (forwardStack != NULL) {
        pop(&forwardStack);
    }

    printf(GREEN "\n✔ Visited: %s\n" RESET, current);
}

// Go Back
void goBack() {
    if (backStack == NULL) {
        printf(YELLOW "\n⚠ No pages in back history!\n" RESET);
        return;
    }

    push(&forwardStack, current);
    char* url = pop(&backStack);
    strcpy(current, url);

    printf(CYAN "\n⬅ Back to: %s\n" RESET, current);
}

// Go Forward
void goForward() {
    if (forwardStack == NULL) {
        printf(YELLOW "\n⚠ No pages in forward history!\n" RESET);
        return;
    }

    push(&backStack, current);
    char* url = pop(&forwardStack);
    strcpy(current, url);

    printf(CYAN "\n➡ Forward to: %s\n" RESET, current);
}

// Show Current Page
void showCurrent() {
    printf(GREEN "\n🌐 Current Page: %s\n" RESET, current);
}

// Menu
void menu() {
    printf(CYAN "\n======= 🌐 BROWSER HISTORY MENU =======\n" RESET);
    printf("1. Visit New Page\n");
    printf("2. Back\n");
    printf("3. Forward\n");
    printf("4. Show Current Page\n");
    printf("5. Exit\n");
    printf("======================================\n");
}

// Main
int main() {
    int choice;
    char url[100];

    while (1) {
        menu();
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {

        case 1:
            printf("Enter URL: ");
            scanf("%s", url);
            visit(url);
            break;

        case 2:
            goBack();
            break;

        case 3:
            goForward();
            break;

        case 4:
            showCurrent();
            break;

        case 5:
            printf(GREEN "\nExiting Browser...\n" RESET);
            exit(0);

        default:
            printf(RED "\nInvalid choice!\n" RESET);
        }
    }

    return 0;
}
