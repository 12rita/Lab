
#include "stdafx.h" 
using namespace std; 
class directory; 
class fil 
{ 
protected: 
string name; 
string data; 
public: 
friend directory; 
fil(string n, string d = 0) 
{ 
int q = n.length(); 
n += ".f"; 
name = n; 
data = d; 
} 
}; 
class directory 
{ 
protected: 
directory* pdir[10]; 
fil* pfil[10]; 
string name; 
public: 
directory* rod; 
directory(string n) 
{ 
name = n; 
for (int i = 0;i < 10;i++) 
{ 
pdir[i] = nullptr; 
pfil[i] = nullptr; 
} 
} 
void created(string n) 
{ 
directory* pnew = new directory(n); 
int i = 0; 
while (pdir[i] != 0) 
{ 
i++; 
} 
pdir[i] = pnew; 
pnew->rod = this; 
} 
void createf(string n,string d) 
{ 
fil* pnew = new fil(n,d); 
int i = 0; 
while (pfil[i] != 0) 
{ 
i++; 
} 
pfil[i] = pnew; 
} 
void remove(string n) 
{ 
for (int i = 0;i < 10;i++) 
{ 
if(pdir[i]->name == n) pdir[i]=nullptr; 
if(pfil[i]->name == n) pfil[i] = nullptr; 
} 
} 
void list() 
{ 
int i = 0; 
cout << "directories:" << endl; 
while (pdir[i] != 0) 
{ 
cout << pdir[i]->name<<endl; 
i++; 
} 
i = 0; 
cout << "files:" << endl; 
while (pfil[i] != 0) 
{ 
cout << pfil[i]->name<<endl; 
i++; 
} 
} 
void print() 
{ 
cout << name << ">>"; 
} 
void open(string n) 
{ 
int i = 0; 
while (pfil[i]->name != n) 
{ 
i++; 
} 
cout << pfil[i]->data<<endl; 
} 
friend void cd(string n); 
}; 



directory headdir("main"); 
directory* curdir=&headdir; 
void cd(string n) 
{ 
int i = 0; 
while (curdir->pdir[i]->name != n) 
{ 
i++; 
} 
curdir = curdir->pdir[i]; 
} 
//cd, mkdir, open, list, 
int main() 
{ 
string data, value,text; 
while (data != "exit") 
{ 
curdir->print(); 
cin >> data; 
switch (data[0]) 
{ 
case 'c'://cd 
cin >> value; 
cd(value); 
break; 
case't'://cr file 
cin >> value >> text; 
curdir->createf(value, text); 
break; 
case 'm'://cr dir 
cin >> value; 
curdir->created(value); 
break; 
case 'l'://list 
curdir->list(); 
break; 
case '.'://back 
curdir = curdir->rod; 
break; 
case'o'://open 
cin >> value; 
curdir->open(value); 
break; 
default: 
cout << "wrong command"<<endl; 
break; 
} 

} 

return 0; 
}
