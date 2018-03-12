#include<iostream>
#include<fstream>
using namespace std;
int G;
int n;
float obiecte[100][3];
float profit;

int read_data()
{
fstream f;
f.open("input.dat",ios::in);
f>>G;
f>>n;
for(int i=0;i<=n-1;i=i+1)
  {
   f>>obiecte[i][0];
   f>>obiecte[i][1];
  }
}

int sort_data()
{
    int sortare;
    do
    {
        sortare = 1;
        for(int i = 1; i < n; i++)
            if(M[i].eficienta < M[i + 1].eficienta)
        {
            swap(M[i].eficienta, M[i + 1].eficienta);
            swap(M[i].profit, M[i + 1].profit);
            swap(M[i].greutate, M[i + 1].greutate);
            sortare = 0;
        }
     }while(sortare == 0);
}

int init_data()
{
for(int i=0;i<=n-1;i=i+1) {
   obiecte[i][2]=obiecte[i][0]/obiecte[i][1];}
sort_data(); // sorteaza orbiecte dupa eficienta
profit=0;
}

int greedy()
{
int i=1;
while((i<=n)&&(G>0))
{
    if(G>=obiecte[i][2]){profit=profit+obiecte[i][1];
    G=G-obiecte[i][2];}
    else {
         float x;
         x=(G*100)/obiecte[i][1];
         profit=profit+x;
         G=0;
         i=i+1;}
}
}

int main()
{
read_data();
init_data();
sort_data();
greedy();
cout<<profit;
}
