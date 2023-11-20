*// Failure-Inducing Input
    @Test
    public void testReverseInPlaceFailure() {
        int[] input = {1, 2, 3, 4, 5};
        int[] expected = {5, 5, 5, 5, 5};
        reverseInPlace(input);
        assertArrayEquals(expected, input);
    }*

*// Non-Failure Inducing Input
    @Test
    public void testReverseInPlaceSuccess() {
        int[] input = {1, 2, 3, 4, 5};
        int[] expected = {5, 4, 3, 2, 1};
        reverseInPlace(input);
        assertArrayEquals(expected, input);
    }*

*// Bug Fix (Before)
static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}*

*// Bug Fix (After)
static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length / 2; i += 1) {
        int temp = arr[i];
        arr[i] = arr[arr.length - 1 - i];
        arr[arr.length - 1 - i] = temp;
    }
}*








The bug fix involves correcting the logic within the reverseInPlace method. Instead of 
assigning arr[i] to arr[arr.length-1-1] (which was causing all elements to be set to the 
second-to-last element), it now correctly swaps elements from the beginning and end of 
the array using a temporary variable (temp). The loop now iterates only up to half of the 
array, ensuring that the swap occurs symmetrically and the array is properly reversed.

4 grep command options:
Syntax: grep [options] pattern [files]
-e exp : Specifies expression with this option. Can use multiple times.
-f file : Takes patterns from file, one per line.
-E : Treats pattern as an extended regular expression (ERE)
-C n : Prints searched line and n lines after before the result.
Source Cite: https://www.geeksforgeeks.org/grep-command-in-unixlinux/

find ./technical -name "*.txt"
./technical/file1.txt
./technical/file2.txt
./technical/subdirectory/file3.txt
It's useful when you want to quickly find files with a specific extension or pattern 
in a large directory structure, helping you organize or manipulate specific types of files.

find ./technical -type d -name "docs"
./technical/docs
./technical/subdirectory/docs
It's useful when you need to locate specific directories based on their names, allowing 
you to navigate or perform operations on those directories directly.

