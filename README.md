# post_lab
# task 1 
#include <stdio.h>
void welcome(){
    printf("welcome to ATM\n");
}
void displayamount(int amount){
    printf("cash %d\n",amount);
}

int getWithdrawalLimit(){
    return 50000;
}
int calculatebalance(int currentbalance,int withdrawalamount){
    return currentbalance -withdrawalamount;
}
int checkWithdrawal(int currentbalance, int withdrawal, int maxlimit){
    if(withdrawal> 0 && withdrawal<=currentbalance && withdrawal <= maxlimit){
        return 1;
    }
    return 0;
}
int main() {
welcome();
int balance = 75000;
int withdrawalamount;
int maxlimit;
printf("current balace %d",balance);
    maxlimit=getWithdrawalLimit();;
 printf("enter amount to withdraw");
 scanf("%d",&withdrawalamount);
  
      if(checkWithdrawal( balance ,withdrawalamount, maxlimit)==1){
      printf("transaction paased");
         displayamount(withdrawalamount);
      balance = calculatebalance(balance,withdrawalamount);
      printf("remaining balance %d",balance);
      }
    else{
        printf("transaction failed");
    }

    return 0;
}
# task 2
#include<stdio.h>
void welcome(){
    printf("welcome to our shopping mall\n");
}
 int menu() {
     printf("1.fish ,2. pizza,3.fries\n");
 }
int products(int choice){
    if(choice==1) return 300;
    if(choice==2) return 400;
    if(choice==3) return 30;
}
int calculateitemprice(int price,int quantity){
    return price*quantity;
}
int calculatediscount(int subtotal){
    if(subtotal>=2000){
        return subtotal*0.10;
    }

    return 0;
}
int calculatefinalbill(int subtotal, int discount){
    return subtotal - discount;
}

    void displayreciept(int subtotal,int discount,int finalprice){
        printf("subtotal %d\n",subtotal);
        printf("discound %d\n",discount);
        printf("finalprice %d",finalprice);
    }
    int acontinue(){
        int response;
        printf("do you want to continue");
        scanf("%d",&response);
        return response;
    };
int main(){
int quantity;
int itemprice,itemtotal;
 int choice;
    int subtotal=0;
    int shopping=1;
welcome();
while(shopping==1){
    menu();

printf("enter the item number from 1 to 3\t");
    scanf("%d",&choice);
    printf("enter the quantity");
    scanf("%d",&quantity);
    itemprice=products(choice);
    if(itemprice==0){
        printf("please choice valid item");
        continue;
    }
        if(quantity<=0){
            printf("quanity must be greater than 0");
            continue;
        }
itemtotal=calculateitemprice(itemprice,quantity);
        subtotal+=itemtotal;
        printf("total %d",itemtotal);
        shopping=acontinue();
}
        if(subtotal>0){
         int totaldiscount=calculatediscount(subtotal);
          int finalbill=calculatefinalbill(subtotal,totaldiscount);
            displayreciept(subtotal,totaldiscount,finalbill);
        }else{
            printf("no items selected");
        }

    return 0;
}

# task 2

  
    return 0;
}
