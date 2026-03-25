# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
## 5. Implementation of one-dimensional array and multidimensional array.
## 6. Implementation of string manipulation.
# Ex.No:11
  Formulate a C program to convert a given decimal number into its binary equivalent and display it.

# Aim:
To formulate a C program to convert a decimal number into its binary equivalent and display it.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare variables: num (input number), rem (remainder), binary[] (array to store binary digits), and loop counters i and k.
### Step 4: 
  Read the decimal number from the user.
### Step 5: 
  Initialize i = 0.
### Step 6: 
  Repeat while num > 0:
  Divide num by 2 and store the remainder in binary[i].
  Increment i.
  Update num = num / 2.
### Step 7: 
  Display the binary digits in reverse order (from i-1 down to 0).
### Step 8: 
   Stop
# Program:
```
#include <stdio.h>
int main() {
    int decimal, temp;
    int binary[32]; 
    int i = 0;
    int j;
    printf("Enter a decimal number: ");
    scanf("%d", &decimal);
    temp = decimal; 
    if(decimal == 0) {
        printf("Binary of 0 is 0\n");
        return 0;
    }
    while(temp > 0) {
        binary[i] = temp % 2; 
        temp = temp / 2;
        i++;
    }
    printf("Binary of %d is: ", decimal);
    for(j = i-1; j >= 0; j--) {
        printf("%d", binary[j]);
    }
    printf("\n");
    return 0;
}
```


# Output:

<img width="487" height="277" alt="image" src="https://github.com/user-attachments/assets/81413938-1abc-4134-9c7f-cefbd72f9e38" />


# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:12
  Develop a C program to read a matrix and find its saddle point. A saddle point is an element that is the minimum in its row and also the maximum in its column. If such an element exists, display its position and value.

# Aim:
  To develop a C program that inputs a matrix, checks each row for its minimum element, verifies whether that element is also the maximum in its corresponding column, and displays the saddle point and its position if it exists.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
 Declare variables i, j, k, m, min, max and a position array pos[2][2].
### Step 4: 
 Read the order of the square matrix m.
### Step 5: 
 Declare an m × m matrix and read its elements.
### Step 6: 
 Display the matrix.
### Step 7: 
   For each row `i` from `0` to `m−1`:
- **Step 7.1:** Set `min` as the first element of the row.  
- **Step 7.2:** Scan the row to find its minimum element and store its position in `pos[0]`.  
- **Step 7.3:** Let `j` be the column of this minimum element.  
- **Step 7.4:** Set `max` as the first element of column `j`.  
- **Step 7.5:** Scan column `j` to find its maximum element and store its position in `pos[1]`.  
### Step 8: 
  Check if the row minimum equals the column maximum:
- If `min == max` **and their positions match**, then the element is a **saddle point**.
- Print the saddle point value and its position.
### Step 9: 
  Stop
# Program:
```
#include <stdio.h>
int main() {
    int m, n,i,j,k;
    printf("Enter number of rows: ");
    scanf("%d", &m);
    printf("Enter number of columns: ");
    scanf("%d", &n);
    int matrix[m][n];
    printf("Enter elements of the matrix:\n");
    for(i = 0; i < m; i++) {
        for( j = 0; j < n; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
    int saddleFound = 0;
    for(i = 0; i < m; i++) {
        int rowMin = matrix[i][0];
        int colIndex = 0;
        for(j = 1; j < n; j++) {
            if(matrix[i][j] < rowMin) {
                rowMin = matrix[i][j];
                colIndex = j;
            }
        }
        int isSaddle = 1;
        for(k = 0; k < m; k++) {
            if(matrix[k][colIndex] > rowMin) {
                isSaddle = 0;
                break;
            }
        }
        if(isSaddle) {
            printf("Saddle point found: %d at position (%d, %d)\n", rowMin, i, colIndex);
            saddleFound = 1;
        }
    }
    if(!saddleFound) {
        printf("No saddle point exists in the matrix.\n");
    }
    return 0;
}
```
# Output:

<img width="677" height="588" alt="image" src="https://github.com/user-attachments/assets/9ec6290f-55a2-4352-918c-b9e05bc42d3f" />


# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:13
  Formulate a C program to reverse a string entered by the user and display the reversed string.

# Aim:
  To formulate a C program that reads a string from the user, reverses it, and prints the reversed string.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare two character arrays: `s` to store the input string and `d` to store the reversed string.
### Step 4: 
  Read the string from the user using `scanf("%[^\n]s", s);`
### Step 5: 
  Find the length of the string `s` by traversing it until the null character `'\0'` is encountered.
### Step 6: 
  Initialize a counter `j` for the reversed string.
### Step 7: 
  Copy characters from the end of `s` to the beginning of `d` using a loop until all characters are copied in reverse order.
### Step 8: 
  Terminate the reversed string `d` with the null character `'\0'`.
### Step 9: 
  Print the reversed string.
### Step 10: 
  Stop
# Program:

```
#include <stdio.h>
#include <string.h>
int main() {
    char str[100];  
    int length, i;
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);
    length = strlen(str);
    if(str[length - 1] == '\n') {
        str[length - 1] = '\0';
        length--;  
    }
    char reversed[100];
    for(i = 0; i < length; i++) {
        reversed[i] = str[length - 1 - i];
    }
    reversed[length] = '\0';  
    printf("Reversed string: %s\n", reversed);
    return 0;
}
```

# Output:

<img width="558" height="198" alt="image" src="https://github.com/user-attachments/assets/891e9e4e-4f05-4a0c-bcec-4fd39e888c1b" />


# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.

# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:14
  Formulate a C program to count the frequency of each character in a given string and display the count of every character.

# Aim:
  To formulate a C program that accepts a string from the user and calculates the frequency of each character in the string.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare a character array `s[100]` to store the input string, an integer array `visited[256]` initialized to `0`, and variables `i`, `n`, and `count`.
### Step 4: 
  Read the string from the user using `scanf("%[^\n]", s);`
### Step 5: 
  Calculate the length of the string using `strlen(s)` and store it in `n`.
### Step 6: 
 For each character `s[i]` in the string (from `i = 0` to `n - 1`):
 - If `visited[(unsigned char)s[i]] == 0` (character not yet counted):  
  - Initialize `count = 0`.  
  - Loop through the string again and increment `count` for every occurrence of `s[i]`.  
  - Print `s[i]` and its count.  
  - Set `visited[(unsigned char)s[i]] = 1` to mark it as counted.
### Step 7: 
  Repeat Step 6 for all characters.
### Step 8:
  Stop
# Program:
```
#include <stdio.h>
#include <string.h>
#define MAX 256  
int main() {
	int i;
    char str[1000];
    int freq[MAX] = {0};  
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);
    int len = strlen(str);
    if(str[len - 1] == '\n') {
        str[len - 1] = '\0';
        len--;
    }
    for(i = 0; i < len; i++) {
        unsigned char ch = str[i];  
        freq[ch]++;
    }
    printf("\nCharacter frequencies:\n");
    for( i = 0; i < MAX; i++) {
        if(freq[i] != 0) {
            printf("'%c' : %d\n", i, freq[i]);
        }
    }
    return 0;
}
```
# Output:

<img width="555" height="486" alt="image" src="https://github.com/user-attachments/assets/ccdc3cb6-f622-45ad-aa44-d3885d0adaad" />


# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M3
# IAPR-3- Module 3 - FoC
# Ex.No:15
  Formulate a C program to remove duplicate words from a given string and display the string with only unique words.

# Aim:
  To formulate a C program to remove duplicate words from a given string and display the string with only unique words.
# Algorithm:
### Step 1:
  Start
### Step 2: 
  Include the standard input-output library: #include<stdio.h>.
### Step 3: 
  Declare a character array `str` to store the input string and a 2D array `words` to store individual words.
### Step 4: 
  Read the input string using `scanf("%[^\n]s", str);`
### Step 5: 
 Split the string into words:
 - Traverse the string character by character.  
 - When a space is encountered, terminate the current word with `'\0'` and move to the next row in `words`.  
 - Otherwise, copy the character into the current word.
### Step 6: 
  Compare each word with all other words to detect duplicates:
  - If a duplicate is found, mark it by setting the first character to `'\0'`.
### Step 7: 
  Print all words that are not marked as duplicates.
### Step 8: 
  Stop
# Program:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#define MAX 1000
int isDuplicate(char wordList[][50], int count, char word[]) {
	int i;
    for(i = 0; i < count; i++) {
        if(strcmp(wordList[i], word) == 0) {
            return 1; 
        }
    }
    return 0; 
}
int main() {
	int i;
    char str[MAX];
    char word[50];
    char wordList[100][50]; 
    int wordCount = 0;
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);
    int len = strlen(str);
    if(str[len - 1] == '\n') {
        str[len - 1] = '\0';
    }
    char *token = strtok(str, " "); 
    while(token != NULL) {
        strcpy(word, token);
        if(!isDuplicate(wordList, wordCount, word)) {
            strcpy(wordList[wordCount], word);
            wordCount++;
        }
        token = strtok(NULL, " "); 
    }
    printf("\nString after removing duplicates:\n");
    for( i = 0; i < wordCount; i++) {
        printf("%s ", wordList[i]);
    }
    printf("\n");
    return 0;
}
```

# Output:

<img width="651" height="455" alt="image" src="https://github.com/user-attachments/assets/3ea2f138-22a9-4e91-a80c-df9d773c5310" />


# Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.

