# Word-Counter
// 1.Prompt the user to enter a text or provide a file to count the words.
//  2. Read the input text or file and store it in a string.
//  3. Split the string into an array of words using space or punctuation as delimiters.
//  4. Initialize a counter variable to keep track of the number of words.
//  5. Iterate through the array of words and increment the counter for each word encountered.
//  6. Display the total count of words to the user.
//  You can further enhance the project by adding features such as:
//  7. Ignoring common words or stop words.
//  8. Providing statistics like the number of unique words or the frequency of each word.
//  9. Implementing input validation to handle empty inputs or file errors.
//  10. Adding a graphical user interface (GUI) for a more user-friendly experience.

import java.util.*;
public class Project2 {
    static int tcount = 0;
    static int ncount = 0;
    // break the user string to array
    public static int stringToArray(String str, String s1, String arr[]) {
        for (int i = 0; i < str.length(); i++) {
            if ((str.charAt(i) != ' ')) {
                if (Character.isDigit(str.charAt(i)) || Character.isLetter(str.charAt(i))) {
                    s1 = s1 + str.charAt(i);
                }
                if (i == (str.length() - 1)) {
                    arr[tcount] = s1;
                    tcount++;
                }
            } else {
                arr[tcount] = s1;
                tcount++;
                s1 = "";
            }
        }
        return tcount; // total words of user string
    }

    // finding unique words in array
    public static int UniqueString(String temp[], String arr[]) {
        temp[0] = arr[0];
        ncount++;
        for (int i = 0; i < tcount; i++) {
            int c = 0;
            for (int k = 0; k < ncount; k++) {
                if (temp[k].compareTo(arr[i]) != 0) {
                    c = 0;
                } else {
                    c = 1;
                    break;
                }
            }
            if (c == 0) {
                temp[ncount] = arr[i];
                ncount++;
            }

        }
        return ncount; // total count of unique words
    }

    // printing total count of array
    public static void fun1(String str, String s1, String arr[]) {
        System.out.println("                The Total No Of Words Are : " + (stringToArray(str, s1, arr) + "\n"));
        System.out.println("_\n");
    }

    // printing array of complete string
    public static void fun2(String arr[]) {
        System.out.println("                All The Words In A String :");
        for (int i = 0; i < tcount; i++) {
            System.out.println("                " + (i + 1) + ". " + arr[i] + "\n");
        }
        System.out.println("_\n");
    }

    // printing unique words
    public static void fun3(String temp[], String arr[]) {
        System.out.println("               Unique Words are :");
        int ncount = UniqueString(temp, arr);
        for (int i = 0; i < ncount; i++) {
            System.out.println("               " + (i + 1) + " " + (temp[i]) + "\n");
        }
        System.out.println("_\n");
    }

    // printing total count of unique words
    public static void fun4() {
        System.out.println("                The Total No Of Unique Words Are : " + ncount + "\n");
        System.out.println("_\n");
    }

    // printing unique words with their frequency
    public static void fun5(String temp[], String arr[]) {
        System.out.println("                Unique Words With Their Frequency : ");
        for (int i = 0; i < ncount; i++) {
            int count = 0;
            for (int k = 0; k < tcount; k++) {
                if (temp[i].compareTo(arr[k]) == 0) {
                    count += 1;
                }
            }
            System.out.println("                " + temp[i] + " " + count + "\n");

        }
        System.out.println("_\n");

    }

    // *********************************main function*************************
    public static void main(String args[]) {

        System.out.println("\n**WORD COUNTER*\n");
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the String : ");
        String str = sc.nextLine();
        String arr[] = new String[str.length()];
        int ch;
        String s1 = "";
        String temp[] = new String[100];

        do {
            System.out.println("\n*MENU*");
            System.out.println("1.Total No Of Words");
            System.out.println("2. Show The Words");
            System.out.println("3. Unique Words");
            System.out.println("4. Total No Of Unique Words");
            System.out.println("5. Unique Words With Frequency");
            System.out.println("6. Exit");

            System.out.println("\nSelect any one option : ");
            ch = sc.nextInt();
            System.out.println("_\n");

            switch (ch) {
                case 1:
                    fun1(str, s1, arr); // Total No Of Words
                    break;
                case 2:
                    fun2(arr); // Show The Words
                    break;
                case 3:
                    fun3(temp, arr); // Unique Words
                    break;
                case 4:
                    fun4(); // Total No Of Unique Words
                    break;
                case 5:
                    fun5(temp, arr); // Unique Words With Frequency
                    break;
            }

        } while (ch != 6);
    }
}
