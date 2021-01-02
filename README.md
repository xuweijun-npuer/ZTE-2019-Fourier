# ZTE-2019-Fourier
A solution to radio frequency distortion modeling of ZTE algorithm contest in Fourier group.
# 1.Distortion Modeling
Modeling and Simulation of power amplifier with memory and predistorter
details in ZTE-2019-Fourier.pdf
# 2.Parameters selection
K、M selection and details in ZTE-2019-Fourier.pdf
# 3.Commit code finally
``` c
#include<iostream>
#include<sstream>
#include<fstream>
#include<vector>
#include<list>
#include<deque>
#include<queue>
#include<stack>
#include<map>
#include<set>
#include<bitset>
#include<algorithm>
#include<cstdio>
#include<cstdlib>
#include<cstring>
#include<cctype>
#include<cmath>
#include<ctime>
#include<iomanip>
#include<complex>
using namespace std;
#define out(x) cout<<#x<<": "<<x<<endl
const double eps(1e-8);
const int maxn=30100;
const long long maxint=-1u>>1;
const long long maxlong=maxint*maxint;
typedef long long lint;
//头文件用户可以增加，但请勿删除
//用户只需完善，CorrectBox，getPower两个函数
//支持c++11

/**********************************
*******用户函数修改开始部分************
*/
double getPower()
{
  //由用户完善
  //如下：设置具体的power值


  double power = -5;
  return power;
}

/**********************************
*******用户函数修改开始部分************
*/
vector<complex<double> > CorrectBox(vector<complex<double> > x)
{
  //由用户完善
  //校正模型函数
  //注意不需要有文件读写和输入输出操作
  complex<double> b10 {0.247624464851855,-0.0956475314464437};
  complex<double> b20 {-2.67551373697241e-5,4.30688794829388e-5};
  complex<double> b30 {6.66375907424498e-9,-1.08500304094595e-8};
  complex<double> b40 {-2.01965776265591e-13,9.06508575813386e-13};
  complex<double> b11 {1.09397990053842,-0.151922390649327};
  complex<double> b21 {1.20426509220274e-5,3.06151097787348e-5};
  complex<double> b31 {-1.22916465734018e-8,-6.33955153297187e-9};
  complex<double> b41 {7.68213861439997e-13,4.74981407193908e-13};
  complex<double> b12 {0.213160418908962,0.0769849715338297};
  complex<double> b22 {-8.23196176218695e-6,1.34730030516446e-5};
  complex<double> b32 {1.08030403620087e-8,-4.37417586073866e-9};
  complex<double> b42 {-4.19202124856439e-13,4.00354124034771e-13};
  complex<double> b13 {-0.816974513711706,-0.00865337628649099};
  complex<double> b23 {-1.76239051779360e-5,-2.36495532456673e-5};
  complex<double> b33 {-1.85907872162677e-9,6.33409656730577e-9};
  complex<double> b43 {-1.00203269864746e-13,-5.46316287987832e-13};
  complex<double> b14 {0.216703051092134,0.00883451161897075};
  complex<double> b24 {1.57162386214232e-5,3.06906264271743e-6};
  complex<double> b34 {-1.23498579051727e-9,-8.21229083194408e-10};
  complex<double> b44 {1.04112914142266e-13,6.81271270041075e-14};
  int N;
  N = x.size();
  int i;
  vector<complex<double> > y(N);
  for(i=0;i<x.size();i++){
      if(i<4)y[i] = x[i];
      else y[i] = x[i]*b10 + x[i-1]*b11 + x[i-2]*b12 + x[i-3]*b13 + x[i-4]*b14 + abs(x[i])*x[i]*b20 + abs(x[i-1])*x[i-1]*b21 + abs(x[i-2])*x[i-2]*b22 + abs(x[i-3])*x[i-3]*b23 + abs(x[i-4])*x[i-4]*b24 + abs(x[i])*abs(x[i])*x[i]*b30 + abs(x[i-1])*abs(x[i-1])*x[i-1]*b31 + abs(x[i-2])*abs(x[i-2])*x[i-2]*b32 + abs(x[i-3])*abs(x[i-3])*x[i-3]*b33 + abs(x[i-4])*abs(x[i-4])*x[i-4]*b34 + abs(x[i])*abs(x[i])*abs(x[i])*x[i]*b40 + abs(x[i-1])*abs(x[i-1])*abs(x[i-1])*x[i-1]*b41 + abs(x[i-2])*abs(x[i-2])*abs(x[i-2])*x[i-2]*b42 + abs(x[i-3])*abs(x[i-3])*abs(x[i-3])*x[i-3]*b43 + abs(x[i-4])*abs(x[i-4])*abs(x[i-4])*x[i-4]*b44;
  }  
  return y;
}

//接下来的代码用户请勿修改
//
string print(complex<double> cm)
{
  char buff[110];
  sprintf(buff,"%f%+fi",cm.real(),cm.imag());
  string s = buff;
  return s;
}

vector<complex<double> > init()
{
  vector<complex<double> > x;
  double r,i;
  int n=0;
  while(~scanf("%lf%lfi",&r,&i))
  {
    n++;
    complex<double> cm=complex<double>(r,i);
    x.push_back(cm);
  }
  for (auto cm : x)
  {
    //cout<<print(cm)<<endl;
  }
  return x;
}

void work()
{
  vector<complex<double> > x = init();
  double power = getPower();
  vector<complex<double> > y = CorrectBox(x);
  //output
  printf("%f\n",power);
  for(complex<double> cm : y)
  {
    cout<<print(cm)<<endl;
  }
}
int main()
{
		work();
		return 0;
}
``` 
