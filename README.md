Binary Search Implementation

This C program performs binary search on an array of integers read from an input file. It calculates the average of the numbers, searches for the average in the array using binary search, and prints whether the average exists in the array and its index.
Code Structure

The program consists of the following key components:
search Function

The search function implements binary search on a sorted array. It returns the index of the element if found, otherwise -1.

c

int search(int numbers[], int low, int high, int value)
{
    int mid = (low + high) / 2;

    if (low <= high) {
        if (numbers[mid] == value) {
            return mid;
        }
        else if (numbers[mid] < value) {
            return search(numbers, mid + 1, high, value);
        }
        else if (numbers[mid] > value) {
            return search(numbers, low, mid - 1, value);
        }
    }
    return -1;
}

printArray Function

The printArray function prints the elements of the number array.

c

void printArray(int numbers[], int sz)
{
    int i;
    printf("Number array : ");
    for (i = 0; i < sz; ++i) {
        printf("%d ", numbers[i]);
    }
    printf("\n");
}

main Function

The main function serves as the entry point. It reads input from a file, calculates the average, searches for the average in the array, and prints the result.

c

int main(void)
{
    int i, numInputs;
    float average;
    int value;
    int index;
    int* numArray = NULL;
    int countOfNums;
    FILE* inFile = fopen("input.txt", "r");

    fscanf(inFile, " %d\n", &numInputs);

    while (numInputs-- > 0)
    {
        fscanf(inFile, " %d\n", &countOfNums);
        numArray = (int*)malloc(countOfNums * sizeof(int));
        average = 0;

        for (i = 0; i < countOfNums; i++)
        {
            fscanf(inFile, " %d", &value);
            numArray[i] = value;
            average += numArray[i];
        }

        printArray(numArray, countOfNums);
        value = average / countOfNums;
        index = search(numArray, 0, countOfNums - 1, value);

        if (index >= 0)
        {
            printf("Item %d exists in the number array at index %d!\n", value, index);
        }
        else
        {
            printf("Item %d does not exist in the number array!\n", value);
        }

        free(numArray);
    }

    fclose(inFile);
    return 0;
}

Usage

Ensure you have an input file named "input.txt" with the appropriate data format. Compile and run the program, and it will display the results of binary search for each dataset.

bash

$ gcc your_program.c -o your_program
$ ./your_program

Feel free to adapt and integrate this binary search implementation into your projects as needed.
ChatGPT can make mistakes. Consider checking importan
