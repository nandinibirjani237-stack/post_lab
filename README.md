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

  
    return 0;
}
