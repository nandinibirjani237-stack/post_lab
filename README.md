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

# task 9
#include <stdio.h>

int atm(int choice, int *balance)
{
    int amount;

    switch (choice)
    {
        case 1:
            printf("\nYour current balance is Rs. %d\n", *balance);
            break;
        case 2:
            printf("\nEnter amount to deposit: ");
            scanf("%d", &amount);

            if (amount <= 0)
            {
                printf("Deposit amount must be positive.\n");
                return 0;
            }

            *balance = *balance + amount;

            printf("Deposit successful!\n");
            printf("Your updated balance is Rs. %d\n", *balance);
            break;

        case 3:
            printf("\nEnter amount to withdraw: ");
            scanf("%d", &amount);

            if (amount <= 0)
            {
                printf("Withdrawal amount must be positive.\n");
                return 0;
            }

            if (amount > 10000)
            {
                printf("Transaction cannot exceed Rs. 10000.\n");
                return 0;
            }

            if (amount > *balance)
            {
                printf("Insufficient balance.\n");
                return 0;
            }

            *balance = *balance - amount;

            printf("Withdrawal successful!\n");
            printf("Your updated balance is Rs. %d\n", *balance);

            if (*balance < 5000)
            {
                printf(" Your balance is below Rs. 5000.\n");
            }

            break;

        case 4:
            printf("\nThank you for using the ATM!\n");
            break;

        default:
            printf("\nInvalid choice.\n");
    }

    return 1;
}

int main()
{
    int balance = 20000;
    int choice;

    do
    {
        printf("1. Check Balance\n");
        printf("2. Deposit Money\n");
        printf("3. Withdraw Money\n");
        printf("4. Exit\n");
       

        printf("Enter your choice: ");
        scanf("%d", &choice);

        atm(choice, &balance);

    } while (choice != 4);

    return 0;
}
# task 
#include <stdio.h>
int ElectricityBillCalculator(int units,int category){
    int total=0;
      if(category==1){
          if(units>0 && units<=100){
              total=units*15;
          }else if(units>100) {
              total=(100*15)+((units-100)*20);
          }
      }else{
         total=units*25;
      }
   return total;
  }
 int main() {
     int category,units,total,surcharge=0,finalbill=0;
      printf("enter the catagory 1 for domestic 2 for commercial customers");
      scanf("%d",&category);
      printf("enter the units consumed");
      scanf("%d",&units);
     total=ElectricityBillCalculator(units,category);
     printf("total %d",total);
     if(total>5000){
          surcharge=total*0.05;
     }
      finalbill=total+surcharge;
     printf("final bill %d",finalbill);  
         printf("surcharge %d",surcharge);
    return 0;
}
# task
#include <stdio.h>

int main()
{
    float price, quantity, subtotal;
    float discount = 0, memberDiscount = 0;
    float fee = 0, total;
    int member, payment;

    printf("Enter product price: ");
    scanf("%f", &price);

    printf("Enter quantity: ");
    scanf("%f", &quantity);

    subtotal = price * quantity;

    printf("Is customer a member? (1 for Yes, 0 for No): ");
    scanf("%d", &member);

    printf("Payment method (1 for Cash, 2 for Card): ");
    scanf("%d", &payment);

    if (subtotal > 5000)
    {
        discount = subtotal * 10 / 100;
    }

    if (member == 1)
    {
        memberDiscount = subtotal * 5 / 100;
    }

    total = subtotal - discount - memberDiscount;

    if (payment == 2)
    {
        fee = total * 2 / 100;
    }

    total = total + fee;

    printf("\n Shopping Bill \n");
    printf("Subtotal: Rs. %f\n", subtotal);
    printf("Discount: Rs. %f\n", discount);
    printf("Member discount: Rs. %.2f\n", memberDiscount);
    printf("Payment fee: Rs. %f\n", fee);
    printf("Final amount: Rs. %f\n", total);

    return 0;
}
# task 
#include<stdio.h>
int evenodd(int num){
if(num%2==0){
    return 1;
}else{
    return 0;
}

}
int palindrome(int num){
int originalnum=num;
int reversednum=0;
int reminder;
while(num>0){
    reminder=num%10;
    reversednum=(reversednum*10)+reminder;
    num=num/10;
}
if(originalnum==reversednum){
    return 1;
}else{
    return 0;
}
}
int checkprime(int num){
    if(num<=1){
        return 0;
    }
    for(int i=2;i<num/2;i++){
        if(num%i==0){
            return 0;
        }
    }
    return 1;
}

int main(){
int n;
printf("enter a positive number");
scanf("%d",&n);
if(n<=0){
    printf("enter the positive number");
}
if(checkprime(n)==1){
    printf("prime\n");
}else{
    printf(" not prime\n");
}
if(evenodd(n)==1){
printf("even\n");
}else{
    printf("odd\n");
}
if(palindrome(n)==1){
    printf("palindrome\n");
}else{
    printf("not a palindrome number\n");
}
return 0;
}
# task 
#include<stdio.h>
int DeliveryChargesCalculator(int *weight,int *distance,int *status,int cost,int *discount){
 cost=0,*discount=0;
 int distance_charges=0;
    if(*weight<=2){
    cost=200;
}
if(*weight>2 && *weight<=5){
    cost = 400;
}
if(*weight>5){
    cost=700;
}
if(*distance>10){
    distance_charges=20*(*distance-10);
    cost+=distance_charges;
}
if(*status==1){
    if(cost>1000){
        *discount=cost*0.10;
        cost=cost-*discount;
    }
}
return cost;
}
int main(){
    int cost=0, distance=0,weight=0,status,discount=0;
    printf("enter the weight\n");
    scanf("%d",&weight);
   printf("distance");
   scanf("%d",&distance);
   printf("status 1 for member 2 for non member");
   scanf("%d",&status);
    cost=DeliveryChargesCalculator(&weight,&distance,&status,cost,&discount);
printf("%d",cost);
}

# task 

#include<stdio.h>
int EmployeeSalaryandBonus(int salary,int years ,int *bonus,int *tax){
     
    int total=0;
if(years>5){
    *bonus=0.15*salary;
}else if(years>=3 && years<=5){
    *bonus=0.10*salary;
}else if (years<3){
    *bonus=0.05*salary;
}
total=salary+*bonus;

if(total>100000){
    *tax=total*0.05;
}
total=total-*tax;
return total;
}
int main(){
    int years,salary,total,tax=0,bonus=0;
printf("enter the years you have worked");
scanf("%d",&years);
printf("enter the salary");
scanf("%d",&salary);
total=EmployeeSalaryandBonus(salary,years,&bonus,&tax);
printf("total %d\n",total);
printf("basic salary %d",salary);
printf(" tax %d\n",tax);
printf("bonus %d ",bonus);

return 0;
}

# task 
#include<stdio.h>
int LoanEligibilityChecker(int age,int salary,int payment,int *max_loan){
    int remainingincome=salary-payment;
    double required_savings=0.40*salary;
if(age<21 ){
    printf("age is less than 21 so not eligible");
}
else if(salary<50000){
    printf("salary is less than 500000 so not eligible");
}
else if (required_savings>remainingincome){
printf("remaining income is less than 400000 so not eligible");
}

else{
     *max_loan=10*remainingincome;
     return 1;
}

}
int main(){
    int age,salary,payment,status,max_loan=0;
    printf("enter the age");
    scanf("%d",&age);
printf("enter the salary");
    scanf("%d",&salary);
    printf("enter the existing payment");
    scanf("%d",&payment);
     status=LoanEligibilityChecker(age ,salary,payment,&max_loan);
    if(status==1){
        printf("finalloan %d",max_loan);
    }
}
  


