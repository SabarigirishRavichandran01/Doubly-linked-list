# Doubly-linked-list
class node:
    def __init__(self):
        self.data=None
        self.next=None
        self.prev=None
class ddl:
    def __init__(self):
        self.head=None
        self.tail=None
    def insert(self,x):
        a=node()
        a.data=x
        if(self.head==None):
            self.head=a
            self.tail=a
        else:
            n=self.tail
            self.tail.next=a
            a.prev=n
            self.tail=a
    def infirst(self,x):
        a=node()
        a.data=x
        if self.head==None:
            self.head=a
            self.tail=a
        else:
            n=self.head
            a.next=n
            self.head.prev=a
            self.head=a
    def length(self):
        if self.head==None:
            return 0
        else:
            c=0
            t=self.head
            while(t!=None):
                c+=1
                t=t.next
            return c
    def inpos(self,x,pos):
        l=self.length()
        if pos>l:
            print("invalid pos")
        else:
            a=node()
            a.data=x
            n1=self.head
            n2=self.head
            i=1
            while i<pos:
                n1=n2
                n2=n2.next
                i+=1
            n2.prev=a
            a.next=n2
            n1.next=a
            a.prev=n1
    def delinpos(self,pos):
        l=self.length()
        if pos>l:
            print("invalid pos")
        else:
            n1=self.head
            n2=self.head
            i=1
            while i<pos:
                n1=n2
                n2=n2.next
                i+=1
            n=n1.prev
            n1.prev=None
            n1.next=None
            n2.prev=n
    def dellast(self):
            if self.head==None:
                print("nothin")
            elif self.head==self.tail:
                self.head=None
                self.tail=None
            else:
                n=self.tail.prev
                self.tail.prev=None
                n.next=None
                self.tail=n
    def delfirst(self):
        if(self.head==None):
            print("nothing")
        else:
            n=self.head.next
            n.prev=None
            self.head.next=None
            self.head=n 
    def display(self):
        t=self.head
        while(t!=None):
            print(t.data)
            t=t.next
l=ddl()
while True:
    print("Enter your choice")
    print("1.Insert at last")
    print("2.Insert at first")
    print("3.Insert at position")
    print("4.del at last")
    print("5.del at first")
    print("6.del at position")
    print("7.Display")
    print("8.Exit")
    ch=int(input(""))
    if(ch==1):
        x=int(input("Enter to insert at last"))
        l.insert(x)
        print("Value inserted at last")
    elif(ch==2):
        x=int(input("Enter to insert at first"))
        l.infirst(x)
        print("Value inserted at first")
    elif(ch==3):
        x=int(input("Enter value to insert"))
        pos=int(input("Enter the position"))
        l.inpos(x,pos)
    elif(ch==4):
        l.dellast()
        print("Value del at first")
    elif(ch==5):
        l.delfirst()
        print("Value del at first")
    elif(ch==6):
        pos=int(input("Enter the position"))
        l.delinpos(pos)
    elif(ch==7):
        l.display()
    elif(ch==8):
        print("end7")
        break
    else:
        print("Invalid Choice")
