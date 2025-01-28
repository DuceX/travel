---
title: LZYZ-OI 新春欢乐赛 2025 Div.3 E.不定项
date: 2025-01-2 15:40:23
tags: 题解
---

```CPP
#include <iostream>
#include <cstdio>
#include <cstring>
#include <vector>
using namespace std;
#define v(x,i) (value[x]>>i)&1
int n,m,maxx,lenth=1;
char ch='E';
vector<int> value,size;
int main(){
	scanf("%d%d",&n,&m);getchar();
	int len=0;
	size.push_back(0); 
	while (m--){
		char c=getchar();
		if (c<=ch){
			if (len==2) size[size.size()-1]|=(1<<(lenth-1)),maxx++;
			if (++lenth==31) size.push_back(0),lenth=1;
			value.push_back(0),len=0;
		}
		value[value.size()-1]|=(1<<(3-c+'A'));ch=c;len++;
	}
	if (len==2) size[size.size()-1]|=(1<<(lenth-1)),maxx++;
	if (n==value.size()) for (int i=0;i<=value.size()-1;i++) printf("%d %d %d %d\n",v(i,3),v(i,2),v(i,1),v(i,0));
	else if (n==(value.size()+maxx)){
		int x,l,r;
		for (int i=0,j=0,k=0;i<=value.size()-1;i++,k++){
			if ((size[j]>>k)&1){
				for (x=3;x>=0;x--)
					if ((value[i]>>x)&1){
						for (l=3;l>x;l--) printf("0 ");
						printf("1");
						for (r=x-1;r>=0;r--) printf(" 0");
						printf("\n");
					}
			}
			else printf("%d %d %d %d\n",v(i,3),v(i,2),v(i,1),v(i,0));
			if (i==30) j++,k-=30;
		}
	}
	else printf("-1");
	return 0;
}

```

