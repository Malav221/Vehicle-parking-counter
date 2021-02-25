# Vehicle-parking-counter
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
#include<windows.h>
#include<string.h>
#define MAX 4
int hours, minutes, seconds, day, month, year;
int lower = 2, upper =300 , count = 1;
void insert();
void deletion();
int queue_array[MAX];
int rear = - 1;
int front = - 1;
int entry();
int disperse();
int wash();
int capacity();
int receipt();
int num;
int p2=20;
int p4=40;
int b2,b4;
char x [50];
int wch;
int c,w,i;
char s[50];
int capacity1,capacity2;
int w2=500;
int w4=1000;
time_t now;
struct TIME
{
   int seconds;
   int minutes;
   int hours;
};
struct TIME startTime,stopTime;
void printRandoms(int lower, int upper,int count)
{
    int i;
    for (i = 0; i < count; i++)
	{
       num = (rand() %
           (upper - lower + 1)) + lower;
    }
    srand(time(0));
}

void SetColor(int ForgC);
int main()
{

    SetColor(34);
    printf("\n#######WELCOME TO PAY & PARK########\n");
    menu();
    return 0;
}

int menu()
{
       int ch;
       do{
       SetColor(14);
        printf("\n\n\n**************MENU****************");
		printf("\n\tPress 1.For Vehicle Entry details\n");
		printf("------------------------------------------");
		printf("\n\tPress 2. For Vehicle exit details\n");
		printf("------------------------------------------");
		printf("\n\tPress 3.Wash\n");
		printf("------------------------------------------");
		printf("\n\tPress 4.Capacity Check\n");
		printf("------------------------------------------");
		printf("\n\tPress 5.Exit\n");
		printf("------------------------------------------");
		printf("\n\tEnter choice : ");
            scanf("%d",&ch);
            switch(ch)
            {
              case 1:
              	SetColor(3);
              	printf("\nWelcome to the parking center please enter the details for your block number.");
              	printf("\n-----------------------------------------------------------------------------");
              	entry();
                break;
              case 2:
                SetColor(3);
                printf("\nThank You for choosing PAY & PARK");
                printf("\n-----------------------------------------------------------------------------");
                disperse();
                break;
              case 3:
			    SetColor(3);
			    wash();
				break;
              case 4:
                SetColor(3);
                printf("\nCurrent Capacity");
                printf("\n-----------------------------------------------------------------------------");
                capacity();
                break;
              case 5:
                printf("Do come again!!");
                exit(0);
            default:
                SetColor(4);
                Beep(750,350);//in case of invalid entries
                printf("Invalid Entry!!!!");
            }
    }while(ch!=5);
}

int entry()
{
    printRandoms(lower, upper, count);
    printf("\nEnter the start time\t");
    printf("\nEnter hours, minutes and seconds: ");
    scanf("%d %d %d", &startTime.hours,&startTime.minutes,&startTime.seconds);
    printf("ENTRY AT- %d :%d :%d",startTime.hours,startTime.minutes,startTime.seconds);
    startTime.seconds=0;
    printf("\n\tEnter your name: ");
    scanf(" %s",&x);
    printf("\n----------------------------------------");
    printf("\n\t%c is your parking block ", x[2]);
    printf("\n----------------------------------------");
    printf("\n\tTicket number is  %d\n",num);
    printf("\n----------------------------------------");
    printf("\n\tEnter type of vehicle(2/4):");
    scanf("%d",&w);
                  if(w==2)
                  {
                      printf("\n\tINITIAL PRICE= %d",p2);
                  }
                  else if(w==4)
                  {
                      printf("\n\tINITIAL PRICE= %d",p4);
                  }
                  else
                  {   Beep(750,350);
                      printf("\n\tInvalid entry!!!!");
                  }
                  if(w==2)
                  {
                    capacity1++;
                    printf("\n\tNo. of 2 wheelers parked : %d ",capacity1);
                  }
                  else
                  {
                    capacity2++;
                    printf("\n\tNo. of 4 wheelers parked :%d ",capacity2);
                  }

                  if(w==2)
              	 {
              	   if(capacity1>4)
				   {
				    printf("\n\tPARKING LOT FOR 2 WHEELERS IS FULL");
				   }
				 }
              	else if(w==4)
              	{
              	  if(capacity2>4)
				  {
				  printf("\n\tPARKING LOT FOR 4 WHEELERS IS FULL");
				  }
				}
				else
				{
				    Beep(750,350);
					printf("\n\tINVALID INPUT");
				}
}
int disperse()
{
	int h;
	printf("\n\tEnter the stop time. \n");
    printf("\n\tEnter hours, minutes and seconds: ");
    scanf("\n\t%d %d %d", &stopTime.hours,&stopTime.minutes,&stopTime.seconds);
    stopTime.seconds=0;
    h=stopTime.hours;
    if(h>=1 && h<=7)
    {
    	Beep(750,350);
    	printf("PARKING LOT IS CLOSED. IF YOUR CAR IS STILL PARKED, CONTACT THE OFFICER!");
	}
    else if(h>=8 && h<=12 )
    {
    	b2=p2+20;
    	b4=p4+30;
	}
	else if(h>12 && h<=17)
	{
		b2=p2+30;
    	b4=p4+40;
	}
	else if(h>17 && h<=20)
	{
		b2=p2+40;
    	b4=p4+50;
	}
	else if(h>20 && h<23)
	{
		b2=p2+60;
		b4=p4+70;
	}
	else if(h=0)
	{
	    b2=p2+70;
		b4=p4+80;
	}
 printf("\n\tEnter name: ");
 fflush(stdin);
 scanf("%s",&s);
 printf("\n\tEnter type of vehicle(2/4):");
 scanf("\n%d",&w);
 if(w==2)
 {
 printf("price= 20");
                  }
                  else if(w==4)
                  {
                    printf("\n\tPRICE= 40");
                  }
                  else
                  {
                    Beep(750,350);
                    printf("\n\t\tInvalid entry!!!!");
                  }
                  if(w==2)
                  {
                    if(capacity1!=0)
                    {
                    capacity1--;
                    printf("\n\t\tNo. of 2 wheelers parked : %d ",capacity1);
                    }
                    else
                    {
                    printf("\n\t\tNO 2 WHEELERS PARKED!!");
                    }
                  }
                  else
                  {
                    if(capacity2!=0)
                    {
                    capacity2--;
                    printf("\n\tNo. of 4 wheelers parked :%d ",capacity2);
                    }
                    else
                    {
                    printf("\n\tNO 4 WHEELERS PARKED!!");
                    }
                  }
   printf("\n\n\n\n\n\n");
   printf("\t**PAY & PARK Receipt**");
   printf("\n**********************************");
   printf("\nName: %s\t\n",s);
   printf("--------------------------------");
   printf("\nType of Vehicle: %d\t\n",w);
   printf("--------------------------------");
   printf("\nParking block: %c\t\n",s[2]);
   time_t now;
   time(&now);
   printf("--------------------------------");
   printf("\nExit time is :%s\t\n",ctime(&now));
   printf("--------------------------------");
   if(w==2)
   {
    printf("\nBalance: %d\t\n",b2);
    printf("-------------------------------");
   }
   else
   {
    printf("\nBalance: %d\t\n",b4);
   }
   printf("\n********************************");
return 0;
}

int capacity()
{
  printf("\n2 WHEELERS PARKED : %d\n",capacity1);
  printf("\n4 WHEELERS PARKED : %d\n",capacity2);
}

int wash()
{
do
{
printf("\n\n------------WELCOME TO WASH CENTRE---------------");
printf("\nPRESS\n1.ENTRY\n2.EXIT\n3.Return to Main Menu");
printf("\n\tENTER CHOICE: ");
scanf("%d",&wch);
switch(wch)
{
	case 1:
		insert();
		break;
	case 2:
		printf("\t\tThank you for choosing us");
		deletion();
		break;
	case 3:
		;
        break;
    default:
    	Beep(750,350);
    	printf("\tINVALID INPUTS!");
}
}
while(wch!=3);
return 0;
}

void insert()
{
printRandoms(lower, upper, count);
     int n,a;
     if(rear==MAX-1)
     {
         printf("Queue is full");
         printf("Please wait till all vehicles leave");
         a=1;
     }
     else if(front==-1 && rear==-1)
     {
         front=rear=0;
     }
     else
     {
         rear++;
     }
     if(a!=1)
     {
printf("\n---ENTRY---");     	
printf("\nYOUR TOKEN NO. IS %d",num);
queue_array[rear]=num;
printf("\nHAVE A HAPPY WASH!!");

printf("\nENTER TYPE OF VEHICLE(2/4):\n");
scanf("%d",&w);
printf("--Given below is the bill--\n");
if(w==2)
		{
			printf("----------------------------------------");
			printf("\nYOUR BILL FOR BIKE WASH :%d",w2);
			printf("\nTYPE OF VEHICLE %d wheelers",w);
			printf("\n----------------------------------------");
		}
		else if(w==4)
	   {
	   	    printf("----------------------------------------");
			printf("\nYOUR BILL FOR CAR WASH : %d",w4);
			printf("\nTYPE OF VEHICLE %d wheelers",w);
			printf("\n----------------------------------------");
	   }
     }
}

void  deletion()
{
     int n,check;
     if(front==-1||front>rear)
     {
     	printf("\nQUEUE IS EMPTY");
	 	printf("\nIT'S YOUR TURN");
        check==0;
     }
     
     else 
     {
        n=queue_array[front];
        front++;
        check++;
     }
     
	 if(check!=0)
     {
     	while(check!=0)
     	{
            printf("\nThe token number deleted / vehicle exited was :%d",n);
            time_t now;
	        time(&now);
	        printf("\n---EXIT---");
	        printf("\nday:time:date is- %s",ctime(&now));
	        printf("\nThank you for choosing our service");
	        check--;
	    }
     }
     
 }
 
 //Adding colors to the code
 void SetColor(int ForgC)
 {
     WORD wColor;
     //This handle is needed to get the current background attribute
     HANDLE hStdOut = GetStdHandle(STD_OUTPUT_HANDLE);
     CONSOLE_SCREEN_BUFFER_INFO csbi;
     //csbi is used for wAttributes word
     if(GetConsoleScreenBufferInfo(hStdOut, &csbi))
     {
      //To mask out all but the background attribute, and to add the color
      wColor = (csbi.wAttributes & 0xF0) + (ForgC & 0x0F);
      SetConsoleTextAttribute(hStdOut, wColor);
     }
 }
