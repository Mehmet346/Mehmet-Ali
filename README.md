#include <cstddef>
#include <iostream>
using namespace std;

struct node
{
    int data;
    node *next;
};
 
struct node *head = NULL;
struct node *tail = NULL;


  void insert_position_del(int pos,int insert_ad)//silerek ekleme
  {
    node *current=new node;
    node *previous=new node;
    current=head;
    for(int i=1;i<pos;i++)
    {
      previous=current;
      current=current->next;
    }
    current->data=insert_ad;
  }
  
  void insert_position(int pos, int value)//silmeden ekleme
  {
    node *pre=new node;
    node *cur=new node;
    node *temp=new node;
    cur=head;
    for(int i=1;i<pos;i++)
    {
      pre=cur;
      cur=cur->next;
    }
    temp->data=value;
    pre->next=temp;
    temp->next=cur;
  }
  
void insert_start_del(int value)//silerek ekleme
  {
	node *first=new node;
    first=head;
    first->data=value;
  }
 
void insert_start(int value)//silmeden ekleme
  {
    node *temp=new node;
    temp->data=value;
    temp->next=head;
    head=temp;
  }
void insert_end(int value)//silmeden ekleme
  {
  	node *temp=new node;
    node *current=new node;
    node *previous=new node;
    current=head;
    while(current->next!=NULL)
    {
      previous=current;
      current=current->next;
    }
	current->next=temp;
	temp->data=value;
	temp->next=tail;
  }

void insert_end_del(int value)//silerek ekleme
  {
    node *current=new node;
    node *previous=new node;
    current=head;
    while(current->next!=NULL)
    {
      previous=current;
      current=current->next;
    }
	current->data=value;
	current=tail;
  }

  void delete_first()
  {
    node *first=new node;
    first=head;
    head=head->next;
    delete first;
  }

  void delete_last()
  {
    node *current=new node;
    node *previous=new node;
    current=head;
    while(current->next!=NULL)
    {
      previous=current;
      current=current->next;
    }
    tail=previous;
    previous->next=NULL;
    delete current;
  }

  void delete_sira(int pos)
  {
    node *current=new node;
    node *previous=new node;
    current=head;
    for(int i=1;i<pos;i++)
    {
      previous=current;
      current=current->next;
    }
    previous->next=current->next;
  }

int print()
{
    cout << "Linked List: " << endl;
    struct node *p = head;
    while(p!=NULL)
    {
        cout << p->data << endl;
        p=p->next;
    }
    return 1;
}

int print_position(int sayi)
{
    cout << "Linked List: " << endl;
    struct node *p = head;
    for(int i=0;i<sayi;i++)
    {
    	p=p->next;
        cout << p->data << endl; 
    }
    return 1;
}

int main()
{
    while (1)
    {
        menu:
        int i = 1;
        int sayi ;
        cout << "1 - Ekleme\n2 - Hepsini Yazdirma\n3 - Eleman Yazdirma\n4 - Eleman Silme\n5 - Cikis" << endl;
        cout << "Hangi Islemi Yapmak Istersiniz : ";
        cin >> sayi;

        if (sayi == 1)
        {
            int number;
            cout << "1 - Baslangica Ekle\n2 - Baslangica Silerek Ekleme\n3 - Sona Ekle\n4 - Sona Silerek Ekleme\n5 - Istedigim Siraya Silerek Ekleme\n6 - Istedigim siraya silerek ekleme";
            cin >> number ;
            if (number == 1)
            {
                int numara;
                cout << "Eklemek Istediginiz Sayiyi Giriniz : ";
                cin >> numara;
                insert_start(numara);
                goto menu;
            }
            else if(number == 2)
            {
                int number;
                cout << "Eklemek Istediginiz Sayiyi Giriniz : ";
                cin >> number;
                insert_start_del(number);
                goto menu;
			}
            else if(number == 3)
            {
                int number_second;
                cout << "Eklemek Istediginiz Sayiyi Giriniz : ";
                cin >> number_second;
                insert_end(number_second);
                goto menu;
            }
            else if(number == 4)
            {
            	int number_second;
                cout << "Eklemek Istediginiz Sayiyi Giriniz : ";
                cin >> number_second;
                insert_end_del(number_second);
                goto menu;
			}
            else if(number == 5)
            {
            	cout<<"hangi siraya eleman eklemek istersiniz : ";
        		int pos;
        		cin>>pos;
        		
        		cout<<"eklemek istediginiz elemani giriniz : ";
        		int insert_ad;
        		cin>>insert_ad;
        	
        		insert_position_del(pos,insert_ad);
           	    goto menu;
			}
			else if(number == 6)
			{
			    cout<<"hangi siraya eleman eklemek istersiniz : ";
        		int pos;
        		cin>>pos;
        		
        		cout<<"eklemek istediginiz elemani giriniz : ";
        		int insert_ad;
        		cin>>insert_ad;
        	
        		insert_position(pos,insert_ad);
           	    goto menu;	
			}
            else
            {
                cout << "Hatali Tuslama Yaptiniz" << endl;
                goto menu;
            }
        }
        else if (sayi == 2)
        {
        	print();
            goto menu;
        }
        else if (sayi == 3)
        {
        	int sayi;
        	cout<<"kacinci elemani yazdirmak istersiniz : ";
        	cin>>sayi;
            print_position(sayi);
            goto menu;
        }
        else if (sayi == 4)
        {
            cout << "1 - Ilk Sayiyi Sil\n2 - Son Sayiyi Sil \n3 - Sectigin Bir Sayiyi Sil :";
            int numara;
            cin >> numara;
            if (numara == 1)
            {
                delete_first();
                goto menu;
            }
            else if(numara == 2)
            {
                delete_last();
                goto menu;
            }
            else if(numara == 3)
            {
                int sira;
                cout << "Kacinci Siradaki Sayiyi Silmek Istersin : ";
                cin >> sira;
                delete_sira(sira);
                goto menu;
            }
            else
            {
                cout << "Yanlis Tuslama Yaptiniz" << endl;
                goto menu;
            }
        }
        else if (sayi == 5)
        {
            return 0;
        }
        else
        {
            cout << "Hatali tuslama yaptiniz" << endl;
            goto menu;
        }
        return 0;
    }
}
