# TIC-TAC-TOE
#include<stdio.h>
#include<stdlib.h>

void player_move(char arr[3][3])
{
    int m=0,n=0;
    printf("Enter row of cell:");
    scanf("%d",&m);
    printf("Enter column of cell:");
    scanf("%d",&n);

    if((arr[m-1][n-1]== ' ' )&& (m<=3&&n<=3))
    {
        arr[m-1][n-1]='X';
    }
    else
    {
        printf("Invalid move please try again\n");
        player_move(arr);
    }
}

void computer_move(char arr[3][3])
{
    int m=rand()%3;
    int n=rand()%3;

      if((arr[m][n]==' ') && (m<=3&&n<=3))
    {
        arr[m][n]='O';
    }
    else
    {
        computer_move(arr);
    }
}

void display(char arr[3][3])
{
    int i,j,r=3,c=3;
    for(i=0;i<r;i++)
    {
        for(j=0;j<c;j++)
        {
            printf("| %c |",arr[i][j]);
        }
        printf("\n");
    }
}

void check(char arr[3][3])
{
    int i;
    for(i=0;i<3;i++)
    {
        if((arr[i][0]==arr[i][1])&&(arr[i][1]==arr[i][2])&&(arr[i][1]!=' '))
        {
            if(arr[i][1]=='X')
                printf("WINNER IS HUMAN\n");
            else
                printf("WINNER IS COMPUTER\n");
            exit(0);
        }
    }

    for(i=0;i<3;i++)
    {
        if((arr[0][i]==arr[1][i])&&(arr[1][i]==arr[2][i])&&(arr[1][i]!=' '))
        {
            if(arr[1][i]=='X')
                printf("WINNER IS HUMAN\n");
            else
                printf("WINNER IS COMPUTER\n");
            exit(0);
        }
    }
    if((arr[0][0]==arr[1][1])&&(arr[1][1]==arr[2][2])&&(arr[1][1]!=' '))
    {
        if(arr[1][1]=='X')
                printf("WINNER IS HUMAN\n");
        else
                printf("WINNER IS COMPUTER\n");
        exit(0);

    }
    else if((arr[0][2]==arr[1][1])&&(arr[1][1]==arr[2][0])&&(arr[1][1]!=' '))
    {
        if(arr[1][1]=='X')
                printf("WINNER IS HUMAN\n");
        else
                printf("WINNER IS COMPUTER\n");
        exit(0);
    }

}
int main()
{
   char ttt[3][3];
     int i,j,r=3,c=3;
      for(i=0;i<r;i++)
    {
        for(j=0;j<c;j++)
        {
            ttt[i][j]=' ';
        }
    }
   int k=9;
   printf("WELCOME TO TIC TAC TOE\n");
   display((char *)ttt);
   printf("You will be playing against a computer\n");

   for(k=9;k>0;k--)
   {
       if(k%2==1)
       {
           printf("HUMAN'S MOVE(X)\n");
           player_move(ttt);
           display((char *)ttt);

           if(k<6)
           {
               check(ttt);
           }


       }
       else
       {
           printf("COMPUTER'S MOVE(O)\n");
           computer_move(ttt);
           display((char *)ttt);
           if(k<6)
           {
               check(ttt);
           }
       }
   }
   if(k=1)
    printf("IT'S A DRAW\n");
   printf("GAME OVER");

return 0;
}
