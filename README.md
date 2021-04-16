/**
 * @file project_main.c
 * @author Anupam (you@domain.com)
 * @brief main function of the program
 * @version 0.1
 * @date 2021-04-16
 * 
 * @copyright Copyright (c) 2021
 * 
 */
#include"library_management.h"

/**
 * @brief main function of the project
 * 
 * @return int 
 */
int main(){
    int task, success, ID, new_member_id;
    char new_status[10], new_date_of_issue[10], new_due_date[10], new_member_first_name[10],new_member_last_name[10], new_title[20];
    test_values (*function_pointer1)(int , char []) = enter_new_record;
    test_values (*function_pointer2)(int) = delete_record;
    test_values (*function_pointer3)(int) = view_a_record;
    test_values (*function_pointer4)(int, char [], char [], char [], char [],char [], int) = update_record;
    test_values (*function_pointer5)() = view_all_records;
    printf("1. View all books\n2. Add a new book\n3. Find a book\n4. Update the status of a book\n5. Delete records of a book\n");
    printf("Enter the task number to perform one of the tasks\n");
    scanf("%d",&task);
    if(task == 1){
        success = function_pointer5();
    }else if(task == 2){
        printf("Enter the ID and title of new book\n");
        scanf("%d\n",&ID);    
        fgets(new_title, 20, stdin);
        success = function_pointer1(ID, new_title);
    }else if(task == 3){
        printf("Enter the ID of the book to search\n");
        scanf("%d",&ID);
        success = function_pointer3(ID);
    }else if(task == 4){
        printf("Enter the ID of the book to update\n");
        scanf("%d",&ID);
        success = function_pointer3(ID);
        if(success == 1){
            printf("Enter new status\n");
            scanf("%s", new_status);
            
            printf("Enter new date of issue\n");
            scanf("%s", new_date_of_issue);
            
            printf("Enter new due date\n");
            scanf("%s", new_due_date);
            
            printf("Enter first name of member\n");
            scanf("%s", new_member_first_name);
            
            printf("Enter last name of member\n");
            scanf("%s", new_member_last_name);
            
            printf("Enter member ID\n");
            scanf("%d", &new_member_id);
            
            success=function_pointer4(ID, new_status, new_date_of_issue, new_due_date, new_member_first_name,new_member_last_name, new_member_id);
        }
    }else if (task==5){
        printf("Enter the ID of the book to delete\n");
        scanf("%d",&ID);
        success=function_pointer2(ID);
    }else{
        printf("Wrong input\n");
    }
    if(success == pass){
        printf("Operation successful\n");
    }else if(success == fail){
        printf("Operation unseccessful\n");
    }else{
        printf("Error condition\n");
    }
    return 0;
}
