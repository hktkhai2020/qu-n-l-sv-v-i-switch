# qu-n-l-sv-v-i-switch
quản lý sv với switch
#include <iostream>
#include <string.h>
#include <iomanip>
#include <conio.h>
using namespace std;
class sinhvien
{
	public :
		char hoten[20], gioitinh[20];
		char namsinh[20], diachi[30];
		char masv[10], lop[10];
		float tin1, tin2 , tin3 , anh1,anh2,DTB;
		void nhap(); 
		void hienthi();
		
};
// xay dung phuong thuc nhap
void sinhvien::nhap()
{
	cin.ignore(1); // xoa bo nho dem
	cout<<" \n Nhap ho ten:";cin.getline(hoten,20);fflush(stdin);
	cout<<" \n Nhap gioi tinh:";cin.getline(gioitinh,10);fflush(stdin);
	cout<< " \n Nhap nam sinh:";cin.getline(namsinh,20);fflush(stdin);
	cout<< " \n NHap dia chi :";cin.getline(diachi,20);fflush(stdin);
	cout<<"\n Nhap ma sinh vien :";cin.getline(masv,10);fflush(stdin);
	cout<<"\n Nhap  ten lop:";cin.getline(lop,10);fflush(stdin);
	cout<<"\n Nhap diem tin 1:"; cin>>tin1;
	cout<<"\n Nhap diem tin 2:"; cin>>tin2;
	cout<<"\n Nhap diem tin 3:";cin>>tin3;

	cout<<" \n Nhap diem anh 1 :"; cin>>anh1;
	cout<<" \n Nhap diem anh 2 :"; cin>> anh2;
	cout<<endl;
}
// ham nhap sinh vien
void sinhvien::hienthi()
{ cout<<endl;
	cout<<""<<setw(10)<<hoten<<setw(10)<<gioitinh<<setw(10)<<namsinh;
	cout<<""<<setw(10)<<diachi<<setw(10)<<masv<<setw(10)<<lop;
	
	cout<<""<<setw(10)<<tin1<<setw(10)<<tin2<<setw(10)<<tin3;
	cout<<""<<setw(10)<<anh1<<setw(10)<<anh2;
	
	DTB=(tin1+tin2+tin3+anh1+anh2)/5;
	cout<<""<<setw(10)<<DTB;
	cout<<""<<setw(10)<<setprecision(2)<<DTB;
	if( DTB>=8){
		cout<<" Xep loai gioi";
	}
	else if ( DTB>=7){
		cout<<" Xep loai kha";
	}
	else if ( DTB >=5){
		cout<<" Xep loai trung binh";
	}
	else if (DTB<5)
	{
		cout<<" Xep loai yeu";
	}
	
}

class quanlysv: public sinhvien // ke thua du lieu 
{
	public:
		sinhvien sv[100];
		int n;
		void nhap();
		void hienthi();
		void xeploaiHL();
		void dssvDTBgd();
		void timsvDTBMAX();
		void timkiem();
	};
//xay dung phuong thuc nhap
void quanlysv::nhap()
{
	cout<<"Nhap so luong sinh vien:"; cin>>n;
	for (int i=0;i<n;i++){
		cout<<"\n sinh vien thu:"<<i+1<<"";
		sv[i].nhap(); // goi phuong thuc nhap o lop sinh vien ben tren
		
	}
	
}
void quanlysv::hienthi()
{
	cout<<"\n Ho ten"<<setw(10)<<"Gioi tinh"<<setw(10)<<"Nam sinh"<<setw(10);
	cout<<"Dia chi"<<setw(10)<<"Ma sinh vien"<<setw(10)<<"Lop"<<setw(10);
	
	cout<<"Tin1"<<setw(10)<<"Tin2"<<setw(10)<<"Tin3"<<setw(10);
	cout<<"Anh1"<<setw(10)<<"Anh2"<<setw(10)<<"DTB"<<setw(15)<<" DTB lam tron"<<setw(10);
	for(int i=0;i<n;i++)
	{
		sv[i].hienthi();
	}
		
	}
// xay dung xep loai hoc luc sv
void quanlysv::xeploaiHL()
{
	cout<<"\n";
	cout<<"---\n Sinh vien xep loai hoc luc gioi---"<<endl;
	for (int i=0;i<n;i++)
	{
		
			if (sv[i].DTB>=8)
			{
				sv[i].hienthi();	
			}	
		}
		
		cout<<"\n";
		cout<<"\n ---Sinh vien xep loai hoc luc yeu---"<<endl;
		for (int i=0;i<n;i++)
		{
			if(sv[i].DTB<5)
			{
				sv[i].hienthi();		
			}
		}	
}

void quanlysv::dssvDTBgd()
{
		int i,j;
	sinhvien tg;
	cout<<"\n";
	cout<<"\n ---Danh sach sinh vien co diem trung binh giam dan---"<<endl;
	for (i=0;i<n-1;i++)
	{
		for(j=j+1;j<n;j++){
			if (sv[i].DTB<sv[j].DTB)
			tg=sv[i];
			sv[i]=sv[j];
			sv[j]=tg;
							}		
	}
	cout<<"Sau khi sap xep la:"<<endl;
	for (int i=0;i<n;i++)
	{
		sv[i].hienthi();
		
	}
}
void quanlysv::timsvDTBMAX(){
cout<<"\n";
cout<<"\n---Danh sach sinh vien co diem trung binh cao nhat"<<endl;
int max=0;
for (int i=0;i<n;i++){
	if (sv[i].DTB>max){
		max= sv[i].DTB;
	}
}	
	for (int i=0;i<n;i++){
		if (sv[i].DTB > max){
			sv[i].hienthi();
		}
	}
	
}
void quanlysv::timkiem()
{
	string msv;
	int count=0;
	cout<<"\n Nhap ma sinh vien can tim:";fflush(stdin);getline(cin,msv);
	cout<<"\n---Thong tin sinh vien khi nhap xong la---";
	cout<<"\n Ho ten"<<setw(10)<<"Gioi tinh"<<setw(10)<<"Nam sinh"<<setw(10);
	cout<<"Dia chi"<<setw(10)<<"Ma sinh vien"<<setw(10)<<"Lop"<<setw(10);
	cout<<"Tin1"<<setw(10)<<"Tin2"<<setw(10)<<"Tin3"<<setw(10)<<"Tin4"<<setw(10);
	cout<<"Anh1"<<setw(10)<<"Anh2"<<setw(10)<<"DTB"<<setw(10)<<"DTB lam tron"<<setw(10);
	for (int i =0; i<n;i++)
	{
		if (sv[i].masv == msv ){
			sv[i].hienthi();
			count++;
			
		}
	}
	if (count==0){
		cout<<"\n Khong tim thay du lieu sinh vien";
		
	}
}
main() {
	quanlysv HUBT;
int luachon,n;
cout<<"=====DAY LA CHUONG TRINH QUAN LY SINH VIEN HUBT=====\n";
cout<<"Xin moi ban nhap mot so de tiep tuc:"; cin>>n;
while (n>0){
	cout <<"=========MENU========"<<endl;
	cout<<"===Chuong trinh quan ly sinh vien==="<<endl;
	cout<<"Moi ban chon cac lua chon sau:"<<endl;
	cout<<"1.Nhap thong tin sinh vien."<<endl;
	cout<<"2.Hien thi thong tin sinh vien."<<endl;
	cout<<"3.Xep loai hoc luc sinh vien."<<endl;
	cout<<"4.Danh sach sinh vien co diem trung binh giam dan."<<endl;
	cout<<"5.Tim sinh vien co diem trung binh cao nhat."<<endl;
	cout<<"6.Tim kiem sinh vien bang ma sinh vien."<<endl;
	cout<<"*xin moi nhap lau chon cua ban:"; cin>>luachon;
	switch (luachon){
		
		case 1: 
		HUBT.nhap();
		cout<<"\n ---Nhap mot phim bat ky de tiep tuc---"<<endl;
		system("pause>0");
		break;
		case 2:
		HUBT.hienthi();
		cout<<"\n ---Nhap mot phim bat ky de tiep tuc---"<<endl;
		system("pause>0");
		break;
		case 3:
			HUBT.xeploaiHL();
			cout<<"\n ---Nhap mot phim bat ky de tiep tuc---"<<endl;
		system("pause>0");
			break;
		case 4:
			HUBT.dssvDTBgd();
			cout<<"\n ---Nhap mot phim bat ky de tiep tuc---"<<endl;
		system("pause>0");
			break;
		case 5:
			HUBT.timsvDTBMAX();
			cout<<"\n ---Nhap mot phim bat ky de tiep tuc---"<<endl;
		system("pause>0");
		break;
		case 6:
			HUBT.timkiem();
			cout<<"\n ---Nhap mot phim bat ky de tiep tuc---"<<endl;
		system("pause>0");
			break;
		default :
			cout<<"Ban nhap sai lua chon!"<<endl;
	}
	
	
	
}
	getch();
		
	
	
	
	return 0;
}

