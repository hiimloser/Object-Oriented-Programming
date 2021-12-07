#include<iostream>
using namespace std;
class Date{
	protected:
		int ngay,thang,nam;
	public:
		Date()
		{
			ngay=thang=nam=0;
		}
		void nhap();
		void xuat();
};
void Date::nhap()
{
	cout<<"Ngay  : ";
	cin>>ngay;
	cout<<"Thang : ";
	cin>>thang;
	cout<<"Nam : ";
	cin>>nam;
}
void Date::xuat()
{
	cout<<ngay<<"/"<<thang<<"/"<<nam;
}
class CANBO : private Date{
	private :
		string macanbo,tencanbo;
		static int tienphucapchucvu;
		float luongcoban;
	public:
		CANBO()
		{
			macanbo ='\0';
			tencanbo='0';
			ngay=thang=nam=0;
			luongcoban=0;
		}
		void nhap1();
		void xuat1();
		float tinhluong();
};
int CANBO::tienphucapchucvu =0;
void CANBO::nhap1()
{
	fflush(stdin);
	cout<<"macanbo : ";
	getline(cin,macanbo);
	cout<<"tencanbo : ";
	getline(cin,macanbo);
	CANBO::nhap();
	cout<<"luongcoban : ";
	cin>>luongcoban;
	tienphucapchucvu++;
}
void CANBO::xuat1()
{
	cout<<macanbo<<" "<<tencanbo<<" ";
	CANBO::xuat();
	cout<<" "<<luongcoban<<" "<<tienphucapchucvu;
}
float CANBO::tinhluong()
{
	return luongcoban + tienphucapchucvu;
}
int main()
{
	Date a;
	cout<<"Nhap thong tin ngay thang : \n";
	a.nhap();
	cout<<"\nThong tin ngay thang :\n";
	a.xuat();
	CANBO CB[10];
	int n;
	cout<<"\nTong so CANBO : ";
	cin>>n;
	cout<<"\nNhap thong tin CANBO :\n";
	for(int i=0;i<n;i++)
	{
		cout<<"CANBO "<<i<<" :\n";
		CB[i].nhap1();
	}
	cout<<"\nThong tin CANBO :\n";
	for(int i=0;i<n;i++)
	{
		cout<<"CANBO "<<i<<" :\n";
		CB[i].xuat1();
		cout<<endl;
	}
	return 0;
}
