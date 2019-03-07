# FindLast
This program reads in numbers from a file into an array, then returns the final occurrence of the user's specified number in the file (if it does appear).

import java.util.Scanner;
import java.io.*;

public class FindLast {
    public static void main(String [] arg) throws IOException {
        Scanner sc = new Scanner(System.in);
        int [] numbers = new int [50];
        int size = readIn(numbers);
        System.out.println("Enter a number: ");
        while(sc.hasNext()) {
            int value = sc.nextInt();
            int position = findLast(value, numbers, size);
            if (position > 0)
                System.out.println(value + " last appears in the file at position " + (position + 1));
            else
                System.out.println(value + " does not appear in the file");
            System.out.println("Enter a number: ");
        }
    }
    public static int readIn(int [] array) throws IOException {
        Scanner inFile = new Scanner(new File("numbers.txt"));
        int size = 0;
        while(inFile.hasNext()) {
            array[size] = inFile.nextInt();
            size++;
        }
        inFile.close();
        return size;
    }
    public static int findLast(int val, int [] array, int size)  {
        int pos = 0;
        for(int i = 0; i < size; i++)
            if(array[i] == val)
                pos = i;
    return pos;
    }
}
