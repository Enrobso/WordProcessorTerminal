import java.util.Scanner;
import java.io.*;

/*
This is a simple word press program to run in terminal.
A .txt document is created to the desired location.
Title: Word Press Terminal
Author: Ephream Osborne
Contact: ephreamo@gmail.com
Last Update: 16/5/2019
 */

public class WordProcessor{
    private static Scanner keyboard = new Scanner(System.in);
    private static String UserInput = "Begin Program";
    private static String fileName = "";
    private static String printToScreenName = "";
    private static int max = 101;
    private static int j;
    private static int k;
    private static String[] exportText = new String[max];
    private static int editImportedText = 0;
    
    public static void main (String [] args){
        for (int i = 0; i < exportText.length; i++){
            exportText[i] = new String();
        }
        System.out.println("Welcome to Word Press Terminal.");
        System.out.println("Do you wish to create a new .txt file or import an existing one?");
        
        boolean endProgram = UserInput.equals("3");
        while (!endProgram){
            System.out.println("1- Create");
            System.out.println("2- Import");
            System.out.println("3-End Program.");
            UserInput = keyboard.nextLine();
            switch (UserInput){
                case "1":
                    CreateDocument();
                    break;
            
                    case "2":
                    ReadDocument();
                    break;
                    
                    case "3":
                        System.out.println("Thankyou for using Word Press Terminal.");
                        UserInput = "3";
                        endProgram = UserInput.equals("3");
                    break;
                    
                    default:
                    System.out.println("Sorry, enter \"1\" or \"2\"");
                    break;
                }
            }
    }
    
    public static void CreateDocument(){
        //Once the user is happy to finish the .txt document, it is saved as a file.
        //If the user is editing the text without importing from a previous file, the if statement will run.
        //Otherwise, the user can edit an imported .txt document.
        PrintWriter outputStream = null;
        if(editImportedText == 0){
            fileName = "";
            System.out.println("Enter the name of the new file:");
            fileName = keyboard.nextLine();
            fileName = fileName+".txt";
        }   
            
            try{
                if(fileName.contains("\\"))
                    outputStream = new PrintWriter(fileName);
                else
                    outputStream = new PrintWriter("C:\\Users\\CapnM\\OneDrive\\Documents\\Word Documents\\"+fileName);
            }
            catch(FileNotFoundException e){
                System.out.println("Error opening the file "+fileName);
                System.exit(0);
            }
        
        
        System.out.println("C- copy a line and paste to another line");
        System.out.println("E- edit previously typed line");
        System.out.println("P-print document to screen");
        System.out.println("F- finished document");
        //Initially the text is saved in an array.
        //The user can edit the file easily.
        k = 1;
        int endText = 0;
        if (editImportedText == 1){
            k = j;
        }
        while(endText == 0){
            exportText[k] = keyboard.nextLine();
            
            if (exportText[k].equals("C")){
                    
            }
            else if (exportText[k].equals("E")){
                //The user can access a previous line and edit it.
                k--;
                editLine(k);
            }
            else if (exportText[k].equals("P")){
                k--;
                printToScreen(k);
            }
            else if (exportText[k].equals("F")){
                exportText[k] = "";
                k-=2;
                endText = 1;
            }
            k++;
            increaseExportArray(k);
        }
        if (editImportedText == 1){
            for (int i = 1; i <= k; i++){
                outputStream.println(exportText[i]);
                editImportedText = 0;
            }
            
        }
        else{
            for (int i = 1; i <= k; i++){
                outputStream.println(exportText[i]);
            }
        }
        
        outputStream.close();
        System.out.println("The lines were written to the text file "+fileName);
        returnToMenu();
    }
    public static void editLine(int arrayLength){
        System.out.println("The text so far:");
        for (int j = 1; j <= arrayLength; j++){
            System.out.println(j+" "+exportText[j]);
        }
        System.out.println();
        System.out.println("Type the number of the line you wish to edit:");
        int lineToEdit = keyboard.nextInt();
        
        System.out.println(exportText[lineToEdit]);
        System.out.println("Edit:");
        keyboard.nextLine();
        exportText[lineToEdit] = keyboard.nextLine();
        
        System.out.println("C- copy a line and paste to another line");
        System.out.println("E- edit previously typed line");
        System.out.println("P-print document to screen");
        System.out.println("F- finished document");
    }
    public static void increaseExportArray(int logicalSize){
        if (logicalSize == max){
            max += 1;
            String[] arrayCopy = new String[max];
            for (int i = 1; i < exportText.length; i++){
                arrayCopy[i] = exportText[i];
            }
            exportText = arrayCopy;
        }
    }
    public static void printToScreen(int logicalSizeOfArray){
        System.out.println("C- copy a line and paste to another line");
        System.out.println("E- edit previously typed line");
        System.out.println("P-print document to screen");
        System.out.println("F- finished document");
        System.out.println();
        System.out.println("The document will be printed. You can then begin typing immediately after.");
        System.out.println();
        for (int i = 1; i <= logicalSizeOfArray; i++){
            System.out.println(i+" "+exportText[i]);
        }
    }
    
    
    
    public static void ReadDocument(){
        System.out.println("Enter the full location or the name of the file you wish to import:");
        fileName = keyboard.nextLine();
        
        printToScreenName = fileName.substring(fileName.lastIndexOf("\\")+1);
        
        
        Scanner inputStream = null;
        try{
            inputStream = new Scanner(new File(fileName));
        }
        catch(FileNotFoundException e){
            System.out.println("There was an error in opening the file "+printToScreenName);
            System.exit(0);
        }
        
        System.out.println("The file "+printToScreenName+" contains the following lines:");
        j = 1;
        while(inputStream.hasNextLine()){
            exportText[j] = inputStream.nextLine();
            System.out.println(j+" "+exportText[j]);
            j++;
            increaseExportArray(j);
        }
        inputStream.close();
        System.out.println("Do you wish to edit this file?");
        System.out.println("Yes, or No:");
        UserInput = keyboard.nextLine();
        
        if(UserInput.equalsIgnoreCase("yes")){
            editImportedText = 1;
            CreateDocument();
        }
        else{
            returnToMenu();
        }
    }
    
    public static void returnToMenu(){
        System.out.println("\nEnter any character to continue:");
        String enterChar = keyboard.nextLine();
    }
    
}
