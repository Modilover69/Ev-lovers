**BISECTION METHOD**

function []=RG\_BS(fun,x1,x2,acc) y1=feval(fun,x1); y2=feval(fun,x2);

while (y1\*y2)>0

x1=input('Enter value of x1\n'); x2=input('Enter value of x2\n');

y1=feval(fun,x1); y2=feval(fun,x2);

end

while abs(x1-x2)>acc x0=(x1+x2)/2;

y0=feval(fun,x0);

if y1\*y0<0

x2=x0;

y2=feval(fun,x0);

else x1=x0;

y1=feval(fun,x0);

end

end

x0=(x1+x2)/2;

fprintf('The root of eqn is %f\n',x0);

**GAUSS ELIMINATION**

a=input('Enter matrix A '); d=input('Enter matrix D '); n=length(d);

%Creating upper triangular matrix

for i=1:n

for k=i+1:1:n

f=a(k,i)/a(i,i); for j=1:n a(k,j)=a(k,j)-f\*a(i,j); end d(k)=d(k)-f\*d(i); end

end

% Backward Substitution

for i=n:-1:1 temp=d(i);

for j=i+1:n temp=temp-a(i,j)\*x(j); end

x(i)=temp/a(i,i);

end fprintf('x=%f\n',x)

**NEWTON RAPHSON**

function[]=RG\_NRM(fun,dfun,ddfun,x0,acc,maxitr) g=(feval(fun,x0)\*feval(ddfun,x0))/(feval(dfun,x0)^2);

while abs(g)>1

x0=input('Enter new value of x0\n');

g=(feval(fun,x0)\*feval(ddfun,x0))/(feval(dfun,x0)^2);

End itr=1;

while itr<=maxitr x1=x0-(feval(fun,x0)/feval(dfun,x0)); acc\_cal=abs(x1-x0);

if acc\_cal<acc Break

else x0=x1; itr=itr+1;

end

end

fprintf('Root of eqn is %f\n',x1);

**GAUSS SEIDAL**

function[]=RG\_GS(fx1,fx2,fx3,n) x1=0;

x2=0;

x3=0;

for i=1:1:n;

x1=fx1(x2,x3);

x2=fx2(x1,x3);

x3=fx3(x1,x2);

fprintf('\n Itr.No.=%0.1f x1=%f x2=%f x3=%f',i,x1,x2,x3);

end

fprintf('x1=%f x2=%f x3=%f',x1,x2,x3);

**SIMPSON’S 3/8TH RULE**

function[]=RG\_SIMP3(fun,x0,xn,n) h=(xn-x0)/n;

y0=feval(fun,x0); yn=feval(fun,xn);

yr=0;

ys=0;

for i=1:1:n-1 yr=yr+feval(fun,x0+i\*h); end

for j=3:3:n-1 ys=ys+feval(fun,x0+j\*h); end

yt=yr-ys; I=(3\*h/8)\*(y0+yn+2\*ys+3\*yt);

fprintf("The value of Integration is = %f",I)

**TRAPEZOIDAL RULE**

function[]=RG\_TRAP(fun,x0,xn,n) h=(xn-x0)/n;

y0=feval(fun,x0); yn=feval(fun,xn);

yr=0;

for i=1:1:n-1 yr=yr+feval(fun,x0+i\*h); end

I=(h/2)\*(y0+yn+2\*yr);

fprintf("The Value of integration is = %f",I)

**SIMPSON’S 1/3RD RULE**

**function[]=RG\_simp(fun,x0,xn,n) h=(xn-x0)/n;**

**y0=feval(fun,x0); yn=feval(fun,xn);**

**yodd=o;**

**for i=1:2:n-1**

**yodd=yodd+feval(fun,x0+i\*h); end**

**yeven=o;**

**for j=2:2:n-1**

**yeven = yeven+feval(fun,x0+j\*h); end**

**I = h\*(y0+4\*yodd+2\*yeven)/3;**

**fprintf("The value of Integration is %f",I);**

**NEWTON FORWARD INTERPOLATION**

**x=input('Enter x Vector'); y=input('Enter y Vector'); xn=input('Enter Value of xn'); n=length(x);**

**for j = 1:n-1**

**for i =1:n-j**

**if j==1**

**del(i,j)=y(i+1)-y(i);**

**else**

**del(i,j)=del(i+1,j-1)-del(i,j-1); end**

**end**

**end**

**del**

**h=x(2)-x(1);**

**u=(xn-x(1))/h;**

**term=0;**

**for j=1:n-1**

**mult=1;**

**for k=1:j**

**mult=mult\*(u-(k-2));**

**end**

**term = term + ((del(1,j)/factorial(j))\*mult); end**

**yr=y(1)+term**

**fprintf("yr=%f",yr);**

**Lagrange interpolation**

**x=input('Enter x Vector'); y=input('Enter y Vector'); xn=input('Enter Value of xn'); n=length(y);**

**sum=0;**

**pr=1;**

**i=1;**

**j=1;**

**while i<=n**

**while j<=n**

**if i==j**

**pr = pr+((xn-x(j))/(x(i)-x(j))); end**

**j=j+1;**

**end**

**sum = sum + x(1)\*pr; i=i+1;**

**j=1;**

**pr=1;**

**end**

**fprintf("Sum = %f",sum);**

**Range kutta**

**function[]=RG\_RK(fun,x0,y0,xn,h);**

**n = (xn-x0)/h;**

**for i=1:1:n**

**k1 = h\*feval(fun,x0,y0);**

**k2 = h\*feval(fun,x0+h/2,y0+k1/2); k3 = h\*feval(fun,x0+h/2,y0+k2/2); k4 = h\*frval(fun,x0+h,y0+k3); k=1/6\*(k1+2\*k2+2\*k3+k4); yn=y0+k;**

**x0=x0+h;**

**y0=yn;**

**end**

**fprintf('\n yn = %f',yn);**

**CURVE FITTING**

**x=input("Enter value of x");**

**y=input("Enter valu of y");**

**n = lenght(x);**

**sumx = 0;**

**sumxx = 0;**

**sumy=0;**

**sumxy=0;**

**sumxxx=0;**

**sumxxxx=0;**

**sumxxy=0;**

**for i = 1:1:n**

**sumx = sumx +x(i);**

**sumy = sumy + y(i);**

**sumxy = sumxy + x(i)\*y(i);**

**sumxx = sumxx + x(i)\*x(i);**

**sumxxx = sumxxx + x(i)\*x(i)\*x(i);**

**sunxxxx = sumxxxx + x(i)\*x(i)\*x(i)\*x(i); sumxxy = sumxxy + x(i)\*x(i)\*y(i);**

**end**

**p = [sumxxxx sumxxx sumxx ; sumxxx sumxx sumx ; sumxx sumx x];**

**q = [sumxxy;sumxy;sumy];**

**s = p/q;**

**A = s(1),a=A;**

**B = s(2),b=B;**

**C = s(3),c=C;**

**fprintf('\ny= %fx2 + %fx + %f ',a,b,c);**

**Euler’s Method**

**function[]=RG\_EM(fun,x0,y,xn,h);**

**while x0<xn**

**y1 = y1 + h\*feval(fun,x0,y1); x0 = x0 + h;**

**y0 = y1;**

**end**

**fprintf('\n y1 = %f',y1); end**
