# #include <iostream>
#include<algorithm>
#include<array>
#include<cmath>
#include<ctime>
using namespace std;
//double standarddx(double a[]);
int main()
{
    clock_t t;
    t=clock();
    const int years=50;
    double sumx=0.0,dsumx=0.0,xmean,sx,sumsx=0.0,standarddx=0.0,x,
            sumy=0.0,dsumy=0.0,ymean,sy,sumsy=0.0,standarddy=0.0,
             r,a,b,p=0.0,xi,yi  ;
    double xy= 0.0;
    array<double,50> year=
    {54.1,54.8,54.3,55.2,53.9,56.1,54.7,54.9,53.4,54.3,
        53.0,55.7,55.0,55.2,54.9,56.0,55.5,55.5,55.3,55.1,
        54.8,54.0,57.2,57.2,53.9,55.5,55.2,55.3,53.7,54.3,
        57.2,56.5,53.9,56.3,56.4,53.4,54.5,55.8,56.8,55.0,
        55.3,54.0,56.7,56.4,57.3,55.3,54.4,56.7,57.2,56.3};
    for(int i=0;i<50;i++)
    {
        xy+=year[i]*(i+1.0);
    }
    cout<<"Sum of product A.temperature (xy):\t"<<xy<<endl;
    for(int i=0;i<50;i++)
    {
        sumy+=year[i];
        dsumy+=pow(year[i],2);
        
    }
    cout<<"Sum of A.temperature:\t"<<sumy<<endl;// sum of temperature Ey
    cout<<"Square sum of A.temperature:\t"<<dsumy<<endl;//sum of square of years Ey^2
    
    ymean=sumy/years;// mean of temperature Y
    cout<<"Mean of A.temperature:\t"<<ymean<<endl;//mean of tempearture
    
    for(int i=0;i<50;i++)
    {
        sy=pow((year[i]-ymean),2);// (temperature-mean)^2
        sumsy+=sy; //E(y-mean)^2
    }
    cout<<"Sum of (A.temperature-mean)^2:\t"<<sumsy<<endl;////sum of (temperature-mean)^2
    
    standarddy=sqrt(sumy/years); //Standard Derivation of temperature SDY
    cout<<"Standard Derivation of A.temperature (SDY):\t"<<standarddy<<endl;// Standard Derivation of temperature
   
    for(int i=1;i<=years;i++)
    {
        //cout<<"year:\t"<<i<<endl;// for year 1968 to 2017
        x=i;
        sumx+=i;
        dsumx+=pow(i,2);
        //cin>>user[i];
    }
    cout<<"Sum of years(Ex):\t"<<sumx<<endl;// sum of years Ex
    cout<<"Square sum of years(Ex2):\t"<<dsumx<<endl;//sum of square of years Ex^2
    
    xmean=sumx/years;
    cout<<"Mean of years x:\t"<<xmean<<endl;// mean of x;
    
    for(int i=1;i<=years;i++)
    {
        sx=pow((i-xmean),2);//years-mean whole square(x-u)^2
        sumsx+=sx;
    }
    cout<<"Sum of (year-mean)^2:\t"<<sumsx<<endl;// sum of years-mean whole square(x-u)^2
    
    standarddx=sqrt(sumsx/years);
    cout<<"Standard Derivation of (SDx):\t"<<standarddx<<endl;//standard derivation of SDx
    
    
    r= (years*xy-(sumx*sumy))/sqrt(((years*dsumx)-pow(sumx,2))*((years*dsumy)-pow(sumy,2)));// corelation coffecient
    cout<<"Co-relation cofficent(r):\t"<<r<<endl;
    a=r*(standarddy/standarddx);// value of a
    cout<<"Value of a:\t"<<a<<endl;
    b=ymean-(a*xmean);// value of b
    cout<<"Value of b:\t"<<b<<endl;
   cout<<" "<<"*********************************"<<" "<<endl;
    cout<<"Enter a year to prediction Average temperature  :\t"<<endl;
    
    cin>>yi;
    p=a*yi+b;
    xi=yi+2017;
        
    cout<<"The Average temperature prediction of year"<<" "<< xi<<" "<<"is:\t"<<p<<endl;
    
    t=clock()-t;
    cout<<"It take:\n"<<(float)t/CLOCKS_PER_SEC<<"sec"<<endl;
    return 0;
}
