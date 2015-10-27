
#include<stdio.h>
int main()
{
    int i,j,k,n;
    float tab[50][50],w,x[50],s=0.0;
    printf("Podaj ilosc niewiadomych: ");
    scanf("%d",&n);
    printf("\nWprowadzanie danych. Rownania wczytywane sa po kolei.\n");
    for(i=1; i<=n; i++)
    {
        for(j=1; j<=(n+1); j++)
        {
            printf("Wspolczynnik %d %d : ", i,j);
            scanf("%f",&tab[i][j]);
        }
    }
    for(j=1; j<=n; j++) //petla do wygenerowania macierzy górnej trójkątnej
    {
        for(i=1; i<=n; i++)
        {
            if(i>j)
            {
                w=tab[i][j]/tab[j][j];
                for(k=1; k<=n+1; k++)
                {
                    tab[i][k]=tab[i][k]-w*tab[j][k];
                }
            }
        }
    }
    x[n]=tab[n][n+1]/tab[n][n];
    for(i=n-1; i>=1; i--) //petla do podstawien wstecz
    {
        s=0;
        for(j=i+1; j<=n; j++)
        {
            s=s+tab[i][j]*x[j];
        }
        x[i]=(tab[i][n+1]-s)/tab[i][i];
    }
    printf("Wynik: \n");
    for(i=1; i<=n; i++)
    {
        printf("\nx%d=%f\t",i,x[i]);
    }
    return(0);
}
