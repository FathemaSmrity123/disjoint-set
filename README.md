#include<bits/stdc++.h>
using namespace std;
int parent[29],ran[29];
void built(int n)
{
    for(int i=1; i<=n; i++)
    {
        parent[i]=i;
        ran[i]=0;
    }
}
int make_friend(int n)
{
    if(parent[n]==n)
        return n;
    else
        return parent[n]=make_friend(parent[n]);

}
void make_union(int a,int b)
{
    if(ran[a]>ran[b])
        parent[b]=a;
    else
    {
        parent[a]=b;
        if(ran[a]==ran[b])
            ran[b]++;
    }
}
int main()
{
    int test;
    int node,edge,ndd;
    char nd,a1,b1;
    char s[10];
    int a,b;
    cin>>test;
    while(test--)
    {
        printf("\n");
        memset(parent,0,sizeof parent);
        memset(ran,0,sizeof ran);
        cin>>nd;
        ndd=nd-64;
        built(ndd);
        cin.ignore();
        while(gets(s))

        {
            if(s[0]=='\0')
                break;
            a1=s[0];
            b1=s[1];
            a=a1-64;
            b=b1-64;
            int pa=make_friend(a);
            int pb=make_friend(b);
            if((pa!=pb)||(a==b))
                make_union(pa,pb);
        }
        int c=0;
        for(int i=1; i<=ndd; i++)
        {
            if(ran[i]!=0)
                c++;
        }
        cout<<c<<endl;
        if(test)
            puts("");
    }
    return 0;
}

