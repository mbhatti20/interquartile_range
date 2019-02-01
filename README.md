# interquartile_range
find interquartile range using quartile function
    
    
    
    #include <cmath>
    #include <cstdio>
    #include <vector>
    #include <iostream>
    #include <algorithm>
    using namespace std;

    int median(int A[],int n)
    {	int med;
      if(n%2==0)
      {
        return med=((A[n/2-1]+A[n/2])/2.0);
      }
       else
      {
        return med=(A[n/2]);
      }
    }
    int quartile(int A[],int n)
    {	int Q2,Q1,Q3;
      int LH[n/2],UH[n/2];
      sort(A,A+n);
      if(n%2==0)
      {
        for(int i=0;i<n/2;i++)
        {
           LH[i]=A[i];
           UH[i]=A[n/2+i];
           Q2=median(A,n);
           Q1=median(LH,n/2);
           Q3=median(UH,n/2);
        }
      }
       if(n%2!=0)
        {	Q2=median(A,n);
            for(int i=0;i<n/2;i++)
          {
             LH[i]=A[i];
             UH[i]=A[n/2+i+1];
          }	
          Q1=median(LH,n/2);
          Q3=median(UH,n/2);
        }return Q3-Q1;
    }

    int main() {
        int N,sum;
        cin>>N;
        vector<int>X(N);
        vector<int>F(N);
        vector<int>S;
        for(int i=0;i<N;i++)
        {
            cin>>X[i];
        }
        for(int j=0;j<N;j++)
        {
            cin>>F[j];
            sum=sum+F[j];
        }
        for(int k=0;k<N;k++)
            for(int l=0;l<F[k];l++)
            {
                S.push_back(X[k]);
            }
        int arr[sum];
        for(int i=0;i<sum;i++)
        {
          arr[i]=S[i];
      }
        double a=double(quartile(arr,sum));
        printf("%.1f",a);

    }
