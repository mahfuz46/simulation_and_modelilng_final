# simulation_and_modelilng_final
**chemical
import pandas as pd
k1=0.008
k2=0.002
a=[100]
b=[50]
c=[0]
T= [0]
t = 0
delta =0.1
n=10
for i in range(0,11,1):
    at=a[i] + (k2*c[i]-k1*a[i]*b[i])*delta
    bt = b[i] + (k2*c[i]-k1*a[i]*b[i])*delta
    ct = c[i] + 2*(k1*a[i]*b[i]-k2*c[i])*delta
    t = t + delta
    T.append(t)
    a.append(at)
    b.append(bt)
    c.append(ct)

dis = {"Time":T,"A":a,"B":b,"C":c}
r = pd.DataFrame(dis)
print(r)

**monte karlo
import matplotlib.pyplot as plt
import numpy as np
import random as rn
import math
def F(x):
   return math.sin(x*pi/b)

pi =math.acos(-1) # which is pi
#print(pi)

X = []
N =10 #number of item
i = 0
c = 1.00
a = 1
b = 30
while i<=b:
  X.append(i)
  i+= 0.001

Y = [F(x) for x in X ]
#rint(X,Y)
#print(Y)
X_random = [rn.random()*b for _ in range(N)] # means that these objects are used internally

Y_random = [rn.random()*c for _ in range(N)]
#print(X_random)
#print(Y_random)

probability = [1 if(F(X_random[i])>=Y_random[i]) else 0 for i in range(N)]



Accept = probability.count(1)
reject = probability.count(0)

total_point = Accept + reject



print('total accept ',Accept)
print('total reject ',reject)

print('Total point ', total_point)

print('Acceptance ratio :',Accept/N)

print('Rejection ratio :',reject/N)



plt.figure(figsize=(15, 3)) #This will modify/change the width and height of the plot.

plt.plot(X,Y,color='black')
plt.scatter(X_random,Y_random,c = probability,cmap='brg',s=30) #cmap stands for colormap
plt.plot([0,30],[0,0],color='black')

plt.plot([0,30],[1,1],color='red')#upper line 0 to 30 x=1 for star end y=1  end
plt.xticks([i for i in range(b+1)]) #Get or set the current tick locations and labels of the x-axis
for i in range(b+1):
  plt.plot([i,i],[0,1],color='black')

plt.xlabel('X_axis')
plt.ylabel('Y_axis')
plt.title('Monte_Carlo_Simulation')
plt.scatter(X_random,Y_random,c =probability,cmap ='brg') #rainbow
plt.colorbar()
plt.show()





'''faults = [[i+1,0] for i in range(b)]

for i in range(N):
  faults[int(X_random[i])][1]+= probability[i]

print('[Day, Faults]')

count_undercurve = 0
for f in faults:
  count_undercurve += f[1]
  print(f)

print('Fault count ',count_undercurve)'''



#X_random = [i*pi for _ in range(N)]

******boma
import math
from matplotlib import pyplot as plt

#Boomber=[[80,0],[90,-2],[99,-5],[108,-9],[116,-15],[125,-18],[133,-23],[141,-29],[151,-28],[160,-25],[169,-21],[179,-20],[180,-17]]
XB=[80,90,99,108,116,125,133,141,151,160,169,179,180]
YB=[0,-2,-5,-9,-15,-18,-23,-29,-28,-25,-21,-20,-17]
XF=0.0
YF=50.0
XFL=[]
YFL=[]
XFL.append(XF)
YFL.append(YF)
VF=20
flag=0
temp=0
print("Path of Fighter.........")
print("X=",XF,"\t\t\t\tY=",YF)
for p,q in zip(XB,YB):
    distance=math.sqrt((p-XF)**2+(q-YF)**2)
    temp+=1
    print("Distance:",distance)
    if distance<=10:
        flag=1
        break
    else:
        sin=(q-YF)/distance
        cos=(p-XF)/distance
        XF+=VF*cos
        YF+=VF*sin
        XFL.append(XF)
        YFL.append(YF)
        print("X=",XF,"Y=",YF)
#print(XB)
del XB[temp:13]
#print (XB)
del YB[temp:13]
plt.title("Pure Pursuit Problem")
plt.xlabel("Boomber")
plt.ylabel("Fighter")
plt.plot(XB,YB,color='black',linestyle='dashed',linewidth=1,
         marker='o',markersize=10,markerfacecolor='green',
         markeredgecolor='blue')
        
plt.plot(XFL,YFL,color='green',linestyle='dashed',linewidth=1,
         marker='<',markersize=10,markerfacecolor='red',
         markeredgecolor='black')

plt.grid()
plt.show()
if flag==1:
    print("Fighter Attack the Boomber.")
else:
    print("Fighter Failed to Attack the Boomber.")


**lcg

x = int(input("Enter the value of initail Seed : "))
tem =x
a = int(input("Enter the value of a : "))
c = int(input("Enter the value of c : ")) 
m = int(input("Enter the value of m : "))
#
while 1:
    xi=(a*x+c)%m
    Ri = xi/m 
    x = xi
    if xi == tem or xi==0:
        break
    
    print(xi)

**আবু সাঈদ ইসলাম, [10/10/2023 11:50 PM]
x = int(input("Enter the value of initail Seed : "))
tem =x
a = int(input("Enter the value of a : "))
c = int(input("Enter the value of c : ")) 
m = int(input("Enter the value of m : "))
#
while 1:
    xi=(a*x+c)%m
    Ri = xi/m 
    x = xi
    if xi == tem or xi==0:
        break
    
    print(xi)

**document

import pandas as pd

st=[]
wt=[45,16,5,29,33,25,21]
ft =[]
cm=[]
bf=[]
nj=[]
s=c=0
n=7
noj=57
#nj.append(noj)
for i in range(0,n,1):
    st.append(s)
    s+=wt[i]
    c+=wt[i]
    
    nj.append(noj)
    if(c>=60):
        bf.append(1)
        ft.append(s)
        s+=5
        cm.append(c)
        c=0
    else:
        bf.append(0)
        ft.append(s)
        cm.append(c)
    noj-=1

print(nj,st,ft,bf,)
dis ={"Start Time":st,"Work Time":wt,"Finish Time":ft,"Cummulative Time":cm,"Break":bf,"Number of Job":nj}
r = pd.DataFrame(dis)
print(r)

**chi test

import random
s = []
for _ in range(0,100,1):
    t = str(random.random())
    t1 = float(t[0:4])
    s.append(t1)


ct1=ct2=ct3=ct4=ct5=ct6=ct7=ct8=ct9=ct10=0
for i in range(0,100,1):
    if s[i]>=0 and s[i]<=0.1:
         ct1 =ct1+1
    elif s[i]>=0.1 and s[i]<=0.2:
        ct2 =ct2+1
    elif s[i]>=0.2 and s[i]<=0.3:
        ct3 =ct3+1
    elif s[i]>=0.3 and s[i]<=0.4:
        ct4 =ct4+1
    elif  s[i]>=0.4 and s[i]<=0.5:
        ct5 =ct5+1
    elif  s[i]>=0.5 and s[i]<=0.6:
        ct6 =ct6+1
    elif s[i]>=0.6 and s[i]<=0.7:
        ct7 =ct7+1
    elif s[i]>=0.7 and s[i]<=0.8:
        ct8 =ct8+1
    elif s[i]>=0.8 and s[i]<=0.9:
        ct9 =ct9+1
    elif s[i]>=0.9 and s[i]<=1:
        ct10 =ct10+1
o = [ ]
o.append(ct1)
o.append(ct2)
o.append(ct3)
o.append(ct4)
o.append(ct5)
o.append(ct6)
o.append(ct7)
o.append(ct8)
o.append(ct9)
o.append(ct10)
print(o)
l =sum(o)
print(l)
E = [10]*10 #assign list with 10 time 10 value
print(E)
O_E = []
o_E_2 = []
for i in range(0,10,1):
    tem = o[i]-E[i]
    O_E.append(tem**2)
    tem1 = O_E[i]/E[i]
    o_E_2.append(tem1) 

check = sum(o_E_2)


# let c_val = 16.9
c_val = 16.9
if check <c_val:
    print("Accpted")
else:
    
    print("Rejected")

    
